---
id: 291
title: Bitten By Rails Pluralization/Inflection
date: 2006-04-15T17:19:19+00:00
author: admin
layout: post
guid: http://www.softwareas.com/bitten-by-rails-pluralizationinflection
permalink: /bitten-by-rails-pluralizationinflection/
aktt_notify_twitter:
  - 'yes'
dsq_thread_id:
  - "375335278"
categories:
  - SoftwareDev
tags:
  - Grammar
  - Inflection
  - Rails
  - Ruby On Rails
---
<img src="http://img67.imageshack.us/img67/7453/octopi0oq.jpg"/>

If you've heard DHH or other Rails enthusiasts introducing Rails, they'll often point to the neat inflection module, which maps back and forth between plurals and singular forms, among other things. Even if not the most killer thing about Rails, it's an excellent introductory topic as it quickly conveys the humane nature of the Rails API as well as the principle of Convention Over Configuration.

It's also the kind of thing where you think "These exception cases probably won't happen to me...how likely am I to be coding Octopi, Sheep, or Oxen" (unless you work in the underwater farm sector). Actually, it turns out exceptions do happen more than I at first expected and are generally handled in a clean way. But how about exceptions that can't be handled?

Where the inflector isn't smart enough, I've seen the advice (e.g. in PragRails) to override ActiveRecord.set_table_name. e.g.

[ruby]
class Sheep < ActiveRecord::Base
   set_table_name "sheep"
end
[/ruby]

But today I had a problem. My class, "Fave", was leading to an error message about class "Fafe" not found, while loading the fixture. After some bemused grepping, I realised that it was due to this pluralisation issue. Seems that the fixture loader performs some singularization - here's an extract from fixtures.rb:

[ruby]
    @class_name = class_name || 
                  (ActiveRecord::Base.pluralize_table_names @table_name.singularize.camelize : @table_name.camelize)
[/ruby]

**Overriding set_table_name doesn't solve this problem**. Which is surprising given the usual advice, so maybe I missed something!!! The solution that worked for me was to <a href="http://wiki.rubyonrails.com/rails/pages/Turn">configure the Inflection module</a>. I now have this in my config/environment.rb:

[ruby]
Inflector.inflections do |inflection| inflection.irregular "fave", "faves"
end
[/ruby]

Now that Rails' notion of grammar has been redefined, the set_table_name can be removed as it's redundant.

Side note: Since people are often intrigued by the pluralization algorithm but probably not enough to hunt down the code, here it is - taken from active_support/inflections.rb (which confirms why "Faves" became "Fafe"):
[ruby]
  inflect.plural(/$/, 's')
  inflect.plural(/s$/i, 's')
  inflect.plural(/(ax|test)is$/i, '1es')
  inflect.plural(/(octop|vir)us$/i, '1i')
  inflect.plural(/(alias|status)$/i, '1es')
  inflect.plural(/(bu)s$/i, '1ses')
  inflect.plural(/(buffal|tomat)o$/i, '1oes')
  inflect.plural(/([ti])um$/i, '1a')
  inflect.plural(/sis$/i, 'ses')
  inflect.plural(/(?:([^f])fe|([lr])f)$/i, '12ves')
  inflect.plural(/(hive)$/i, '1s')
  inflect.plural(/([^aeiouy]|qu)y$/i, '1ies')
  inflect.plural(/([^aeiouy]|qu)ies$/i, '1y')
  inflect.plural(/(x|ch|ss|sh)$/i, '1es')
  inflect.plural(/(matr|vert|ind)ix|ex$/i, '1ices')
  inflect.plural(/([m|l])ouse$/i, '1ice')
  inflect.plural(/^(ox)$/i, '1en')
  inflect.plural(/(quiz)$/i, '1zes')

  inflect.singular(/s$/i, '')
  inflect.singular(/(n)ews$/i, '1ews')
  inflect.singular(/([ti])a$/i, '1um')
  inflect.singular(/((a)naly|(b)a|(d)iagno|(p)arenthe|(p)rogno|(s)ynop|(t)he)ses$/i, '12sis')
  inflect.singular(/(^analy)ses$/i, '1sis')
  inflect.singular(/([^f])ves$/i, '1fe')
  inflect.singular(/(hive)s$/i, '1')
  inflect.singular(/(tive)s$/i, '1')
  inflect.singular(/([lr])ves$/i, '1f')
  inflect.singular(/([^aeiouy]|qu)ies$/i, '1y')
  inflect.singular(/(s)eries$/i, '1eries')
  inflect.singular(/(m)ovies$/i, '1ovie')
  inflect.singular(/(x|ch|ss|sh)es$/i, '1')
  inflect.singular(/([m|l])ice$/i, '1ouse')
  inflect.singular(/(bus)es$/i, '1')
  inflect.singular(/(o)es$/i, '1')
  inflect.singular(/(shoe)s$/i, '1')
  inflect.singular(/(cris|ax|test)es$/i, '1is')
  inflect.singular(/([octop|vir])i$/i, '1us')
  inflect.singular(/(alias|status)es$/i, '1')
  inflect.singular(/^(ox)en/i, '1')
  inflect.singular(/(vert|ind)ices$/i, '1ex')
  inflect.singular(/(matr)ices$/i, '1ix')
  inflect.singular(/(quiz)zes$/i, '1')

  inflect.irregular('person', 'people')
  inflect.irregular('man', 'men')
  inflect.irregular('child', 'children')
  inflect.irregular('sex', 'sexes')
  inflect.irregular('move', 'moves')

  inflect.uncountable(%w(equipment information rice money species series fish sheep))
[/ruby]