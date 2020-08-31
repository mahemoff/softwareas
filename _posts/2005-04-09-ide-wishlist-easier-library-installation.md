---
id: 92
title: 'IDE Wishlist: Library Installation for the Google Generation'
date: 2005-04-09T22:01:53+00:00
author: admin
layout: post
guid: http://www.softwareas.com/?p=92
permalink: /ide-wishlist-easier-library-installation/
categories:
  - SoftwareDev
---
Let's say I'm coding in exploration (or "spike") mode. Just tinkering a bit, playing around with some ideas. Or maybe experimenting with some new technologies. So it's quite likely **I'll be downloading and installing some libraries**. And I don't want it to distract me ... it should be as transparent as possible.

Even savvy IDEs offer limited support for this sort of thing. Maven can do some magic, but I don't think it's very well integrated into the IDEs (I can't be sure though?). A few wishlist items:

* **Online import intentions** When I add a class that's not in the classpath, give me a list of all known matches in the world. Like what I'd get if I 
performed a [Jarhoo search](http://www.jarhoo.com).
** A "library" database** Similar to the Idea's plugin manager, which is immensely helpful as it automatically installs plugins, it would be possible to integrate a browser and searcher similar to Jarhoo.
* **Automatically download libraries** Triggered by an intention or direct command by the developer of the library.
* **Drop 'N' Go Directory** As with plugins and deployable components in many containers, let me specify a directory where all JARs are automatically included in the project. That way. I don't have to go through the configuration hassles. 