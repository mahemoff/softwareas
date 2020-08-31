---
id: 449
title: Server-Side Hosting Options
date: 2008-06-09T08:36:54+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=446
permalink: /server-side-hosting-options/
dsq_thread_id:
  - "375573736"
categories:
  - SoftwareDev
tags:
  - Hosting
  - Server-Side Javascript
  - Websites
---
<a href="http://www.muralsforkids.com/images/JungleAnimalsBorder.jpg"><img src="http://picupper.com/2008/06/09/JungleAnimalsBorder.jpg" /><a>

I've been thinking about what language and framework to use for my next hobby projects. There has always been a frustrating trade-off between language quality and ease of hosting. The languages I know best are: Ruby (+Rails), PHP, Java, and Javascript. So these will be my options.

What I'm looking for is a hosting environment which will scale well as I add new sites, each with their own domain and database. I want to deploy new sites almost with a single click, but realistically in an hour or less. And I don't want to pay for each new site I deploy - in virtual hosting and cloud style, I want to be paying for overall consumption, not for the number of applications.

(Update: A couple of people suggested I should add Python, so it's now here for completeness.)

<h2>Ruby</h2>

<img src="http://picupper.com/2008/06/06/2126326186_4148045bd0.jpg" />

I say Ruby, but really I mean Ruby on Rails. The only other feasible frameworks for Ruby are Camping and Merb. The first is too simple and the second is too immature and lacking web host support.

Hosting for Rails has been a tragedy for me. I developed a site a year ago and tried to outsource deployment to Amazon EC2, and both suppliers gave up on the job. This was after I deployed it myself on SliceHost, requiring much effort, and then found it couldn't handle the load. There are big Rails-specific hosts, EngineYard and RailsMachine, but they are very expensive and not practical for hobby projects. When I was working on Quizr, I also spent ages getting it deployed on RailsMachine; it was not turnkey as some people expect it to be. All I wanted was a server, a backup server, and a DB - so a fairly standard config. That's not a criticism of RailsMachine, but don't expect it to be trivial if you want more than one server (this was 18 months ago, it might be different now).

Rails is a super coding environment and would be a no-brainer for all of my projects, if only hosting was simple and reasonably priced. With a virtual environment like SliceHost, I found it takes several hours to set up a new site, and you also end up with a lot of config files to maintain (ie mucking about with apache modules and load balancing). You can also use a grid solution like <a href="http://heroku.com">Heroku</a>. This is a fantastic way to keep things lightweight. The downside, though, is there's always some little tasks you need that are outside the sandbox. e.g. setting up a cron job or adding some custom C library. Right now, Heroku doesn't have a commercial model and apparently doesn't let you use your own domain name. This rules it out for anything too serious.

I think the ideal for me would be a virtual Linux environment like SliceHost, with some VERY high level scripts that deploy a Rails app in a single click. These would have to be client-side scripts. I found <a href="http://wiki.slicehost.com/doku.php?id=more_than_one_deprec_on_a_slice">Deprec</a> is close to this and might get there at some stage.

<h2>PHP</h2>

<a href="http://www.dog-breed-picture.com/images/bulldog.jpg"><img src="http://picupper.com/2008/06/08/bulldogstand.jpg" /><a>

PHP isn't the best language, but it's certainly easy to get something up and running. I find for small projects, it's quite maintainable too, even without using PHP5's OO. However, I'd like to use one of the Rails-inspired frameworks, e.g. PHP on Trax, in order to speed things up and ensure it's easily maintained. This is where things get more tricky, because there are so many clones to choose from, and the community for each suffers as a result. As many have pointed out, Rails benefits from being the only serious contender in Ruby space, and the same cannot be said for any other server-side language. With PHP, you don't need any framework at all, so in fact each framework is probably only used by less than 1% of PHP developers. In contrast, Rails is probably used by > 99% of Ruby programmers. Less community means less documentation, support forums, books, and information about hosting and capabilities.

<h2>Java</h2>

<img src="http://picupper.com/2008/06/08/elephant.jpg"/>

Well, I mostly mention this for the sake of completeness. Java's an okay language for web development, especially if you choose your framework right, but hosting has mostly been restricted to enterprises. I find it funny, given Moore's Law, how much Java hosting still costs in 2008, but it's still pretty silly and not easy to just keep adding domains and applications without expense. Furthermore, I find it funny that Sun missed the boat on grid hosting for Java. So while there are consumer-focused solutions for grid hosting Rails and Javascript, no such thing for Java. On the whole, consumer-focused Java hosting is a cottage industry. Given that the language itself isn't so brilliant, not worth the effort.

Where Java might get interesting is the VM. You could use it to host Groovy or Rails projects via JRuby. However, until it's really, really, mature, I feel like JRuby is going to be one of those open-source things that sounds good on paper, but feels less enticing at 4am and with 26 open browser tabs pointing at pertinent blogs and support forums. I will reserve judgement for now.

<h2>Python</h2>

<img src="http://picupper.com/2008/06/22/owl.jpg" width="200" />

Python has a number of modern web frameworks, with Django being the most prominent. The fragmentation didn't help, as compared with Ruby with its one gigantically popular framework, so it helped <a href="http://www.oreillynet.com/onlamp/blog/2006/08/guido_blesses_django_django_an.html">when Guido blessed Django</a>. I'm sure Django (and others like TurboGears) is a good framework, maybe even better than Rails from what I hear. However, as I already know Ruby, I don't have that much interest in taking the time to learn it - the languages and frameworks are similar enough that it wouldn't be worth the effort. Moreover, I like the whole Ruby and Rails community and all the web presence and docs and books around it. It's more fun and focused on the things I care about, like usability, aesthetics, and being opinionated. Also, there is simply a much greater volume of resources.

That said, Python has gained a lot of momentum due to Google App Engine, which exclusively hosts Python. But Google loves Java and I'm sure it will expand to at least support Java at some stage, if not more generic stuff like EC2. Providing a Java runtime would allow for stuff like Scala, JRuby, and Rhino.

<h2>Javascript</h2>

<img src="http://picupper.com/2008/06/08/unicorn.jpg" />

I consider server-side Javascript the holy grail over the next few years. I've explained why before - in summary, it's the fact that you're using the same language on both sides and the synergy that results. It's not just that it's simpler for you, the human programmer, who only has to speak in a single tongue. It's more about the code you end up with. You can have a single module representing a web page, which contains both client and server code. It says "show the user two buttons. If they clicked button 1, do this; If they clicked button 2, do that". So the code is very much combining client and server sides; and unlike high-level web-app compilation services, the code is actually what gets executed on both sides.

The main problem with server-side Javascript is immaturity. It will get interesting when we get Rails like models, the kind of stuff <a href="steve-yegge.blogspot.com/2007/06/rhino-on-rails.html - 83k -">Steve Yegge has talked about</a>. However, it shouldn't be too similar to Rails; otherwise, you'd miss out on the synergetic effect described above. For now, though, server-side Javascript does suffer a lot in comparison with Rails, due to lack of a cohesive MVC model.

The main options for hosting are <a href="http://appjet.com">AppJet</a> and <a href="http://www.aptana.com/jaxer">Jaxer</a>. AppJet is a nice, easy, grid solution, but doesn't yet have enough info on commercial hosting and custom domain names. Jaxer has a lot of promise, but the Linux module will need to come out, be not too processor-intensive, and be supported by web hosts. There is also the upcoming <a href="http://www.aptana.com/cloud">Aptana Cloud</a> solution, but this is similar to AppJet. For now, can't host your own domain. These grid solutions are very handy, but I want to be able to release new apps and domains willy-nilly, and I suspect the grids, when they do become fully commercial, will impose a charge for each new app/domain.