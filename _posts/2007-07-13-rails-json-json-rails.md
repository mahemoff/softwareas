---
id: 390
title: Rails JSON, JSON Rails
date: 2007-07-13T18:56:29+00:00
author: admin
layout: post
guid: http://www.softwareas.com/rails-json-json-rails
permalink: /rails-json-json-rails/
dsq_thread_id:
  - "375148948"
categories:
  - Links
  - SoftwareDev
tags:
  - ActiveRecord
  - AjaxPatterns
  - JSON
  - Links
  - Rails
  - Ruby
---
<img src="http://picupper.com/2007/07/13/json.jpg" width="130" height="130" style="float: left"; />
<img src="http://picupper.com/2007/07/13/rails.png.jpg" width="130" height="130"  style="float:left; padding-left: 30px;"/>

<p style="clear:both; margin-top: 2em; ">
Man, <a href="http://ajaxpatterns.org/JSON_Message">JSON</a> has come out of nowhere! I first came across it amid the Javascript hype in early '05, now it's everywhere. Not only in your Ajax apps, but in the <a href="http://ajaxpatterns.org/On-Demand_Javascript">On-Demand Javascript</a> APIs of the world.

Sharing an ethic of simplicity with Rails, it's not surprising these technologies have come closely together, with JSON support now baked into the Rails core. (They would have been even closer together, if only anyone had noticed <a href="http://redhanded.hobix.com/inspect/yamlIsJson.html">JSON==YAML</a> early on and merged the two completely.) And yet, the current implementation misses a couple of tricks.

<ul>
<li><strong>Use of "attributes".</strong> According to Rails, a JSON object generally has just a single key, "attributes". Instead of the simple { :name=>"Pac-Man", :creator=>"Namco" }, we get (and have to give) { :attributes => { :name=>"Pac-Man", :creator=>"Namco" }}. That's not DRY. Not that it matters, but the reason for this is because ActiveRecords internally store persistable data fields in a hashmap called "attributes". The JSON serialization is therefore faithful to Rails' internal implementation, while being unfaithful to intuition. Maybe you could argue for "attributes" on the basis that you might one day have a transient attribute with the same name as a persistent attribute, in which case you'd get a clash. But Convention Over Configuration rules this argument out; you can always override JSON serialization behavior in boundary situations.
<li><strong>Child attributes</strong> This is probably an issue with XML as well. Basically, there is no attention paid to child attributes, i.e. JSON/XML serialization of a HABTM or has_many relationship. You want something like { :name=>"Pac-Man", :creator=>"Namco", :high_scores=>[{ :player_id=>1, :score=>99999 }, {:player_id=>2, :score=>88888 }] }, but all you get is the top-level attributes :name and :creator.
</ul>

What to do?

First, I just discovered this extremely helpful library - <a href="http://blog.codefront.net/2007/07/11/better-json-output-from-rails-with-the-jsonifier-plugin/">Jsonifier</a>, which also ships as a Rails plugin. It deals with both of the above problems. There's no "attributes" chaff and it deals with associated records, even going recursive and letting you navigate from end of a many-to-many into the other. (In my example, you could show the names and ages of Pac-Man high scorers.) You also get to whitelist or blacklist attributes matches Rails' associations syntax, i.e. :only, :except. Highly recommended, check it out.

Jsonifier, however, is pure to_json - it doesn't (yet) handle deserialization. <a href="http://www.ruby-forum.com/topic/114361">To my knowledge</a>, there's no Rails library that persists both parent and children in one go. There are lots of forum posts about handling multiple checkboxes and the like, and the answer usually involves overriding "children=" or "child_ids=". I want to do this automatically!

I've been working out how to extend ActiveRecord to persist automatigically. I have the following very rough code working in basic situations, although it would need to do some more validation to work in production, among other things. It works on data structures such as the recurisve one above. You must first use a before_filter to convert the incoming JSON string into a Rails structure.

[ruby]
class << ActiveRecord::Base

  def recursive_create(params)
    transaction do
      collections_by_children = pluck_hash_collections_by_children params
      new_model = self.create(params)
      populate_children new_model, collections_by_children
      new_model
    end
  end

  def pluck_hash_collections_by_children(params)
    hash_collections_by_children = Hash.new
    params.each_pair { |name, value|
      if value.class==Array
        hash_collections_by_children[name] = value
        params.delete(name)
      end
    }
    hash_collections_by_children
  end

  def populate_children(new_model, hash_collections_by_children)
    hash_collections_by_children.each_pair { |children_name, hash_collection|
      new_model.send("#{children_name}").destroy_all
      child_class_name = children_name.singularize.camelize
      child_class = Object.const_get(child_class_name)
      hash_collection.each { |child_hash|
        child = child_class.create(child_hash)
        new_model.send("#{children_name}") << child
      }
    }
  end

end

module ActiveRecord
  class Base

    def recursive_update_attributes(params)
      transaction do
        collections_by_children = self.class.pluck_hash_collections_by_children params
        self.update_attributes(params)
        self.class.populate_children self, collections_by_children
        save
      end
    end

  end

end
[/ruby]