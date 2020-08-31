---
id: 302
title: 'Ajax Patterns Tutorial &#8211; Updated Docs'
date: 2006-05-24T16:26:26+00:00
author: admin
layout: post
guid: http://www.softwareas.com/ajax-patterns-tutorial-updated-docs
permalink: /ajax-patterns-tutorial-updated-docs/
dsq_thread_id:
  - "397954250"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Demos
  - Links
  - Tutorial
---
As just mentioned, I've <a href="http://www.softwareas.com/ajax-patterns-code-now-available">posted code for the AjaxPatterns demos and the tutorial</a>. You can run the <a href="http://ajaxify.com/tutorial">tutorial here</a>. The interesting thing here is it's all designed to be hand-coded, so you can see how an Ajax app can easily be built up from first principles, good for learning. The final demo then uses an external library, to make the point that you don't need to hand-code in the real world.

<a href="http://www.ajaxify.com/tutorial/ajaxagram/ajaxified/richer/performant/library/"><img src="http://img254.imageshack.us/img254/7269/ajaxagramfadein3fj.png"/></a>

The <a href="http://ajaxify.com/tutorial/">Ajaxagram demo</a>, with its various <a href="http://www.ajaxify.com/tutorial/ajaxagram/ajaxified/richer/performant/library/">refactorings</a>, is a useful way to introduce the patterns, and I covered it in Ajax Experience presentation. I've edited the overview page to help explain what value each refactoring is adding:

<blockquote>

  <p><a href="ajaxagram/">Ajaxagram: A Conventional Web App</a><br/> No Ajax yet.</p>

  <p><a href="ajaxagram/ajaxified/">Ajaxifying Ajaxagram</a><br/> Ajax version -
  runs in a single page without refresh. Basically the same user exeperience as
  before, but better for your resume and ready for the nice Ajax enhancements to
  come. </p>

  <p><a href="ajaxagram/ajaxified/richer/">Enhancing Functionality and
  Usability</a><br/> Now we're actually seeing the benefits of Ajax. Three
  Functionality and Usability patterns are introduced to enhance the user
  experience - <a href="http://ajaxpatterns.org/Live_Search">Live Search</a>,
  <a href="http://ajaxpatterns.org/Progress_Indicator">Progress Indicator</a>,
  <a href="http://ajaxpatterns.org/One-Second_Spotlight">One-Second
  Spotlight</a>.
  </p>

  <p><a href="ajaxagram/ajaxified/richer/performant/">Streamlining
  Performance</a><br/> Ooops, although it looks prettier and feels smoother, our app
  now has some technical issues. That's a little side effect of most UI
  enhancements. Firstly, there's a bug - if you type too quickly, you'll see
  results for more than one search appear. Secondly, it's too slow - we're
  going back to the server every single keystroke. The Ajax patterns include
  Programming patterns to complement the Functionality and Usability
  patterns, and in this case, we remedy the situation with <a
  href="http://ajaxpatterns.org/Submission_Throttling">Submission
  Throttling</a>.

  <p><a href="ajaxagram/ajaxified/richer/performant/library/">Using An External
  Library</a><br/> This final refactoring appears the same to users, but underneath
  the covers, we've introduced the <a
  href="http://ajaxify.com/run/testAjaxCaller/">ajaxCaller</a> library to
  handle remoting. The point is to illustrate that Ajax Patterns don't have to
  be hand-coded - many are easier to introduce with appropriate <a
  href="http://ajaxpatterns.org/Ajax-Frameworks">Ajax Frameworks and
  Libraries</a>. There's no shame in reusing reliable third-party code - it's
  something to be proud of!</p>
</blockquote>
