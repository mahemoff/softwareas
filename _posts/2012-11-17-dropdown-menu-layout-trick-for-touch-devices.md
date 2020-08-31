---
id: 1872
title: 'Dropdown Menu: Layout Trick for Touch Devices'
date: 2012-11-17T15:56:45+00:00
author: admin
layout: post
guid: http://softwareas.com/?p=1872
permalink: /dropdown-menu-layout-trick-for-touch-devices/
categories:
  - SoftwareDev
---
I'm making a dropdown menu to explore Player FM channels, and the expandable items are quite big. So here's a little trick I used.

On desktop, it looks like this:

![](http://i.imgur.com/niKIj.png)

A big expanding area like this could be annoying, as it's easy to accidentally hover over a region. The important thing is it's easy to collapse it again just by mousing up a bit, since the top of the sub-menu is aligned with the item you've just hovered over.

On touch devices, however, space is more limited, so we want to show more. Conversely, we don't have the same concern as we do with a mouse, because you can't "accidentally" touch a menu item and you can easily touch anywhere on the device to release it. So on touch devices, we vertically align the top of the submenu with the top of the main menu to show as much as possible:

![](http://i.imgur.com/b19Vr.png)

How do we achieve this difference? We can use Modernizr to easily add a "touch" or "no-touch" to the root HTML element. From there, we use relative positioning, but vary the container element depending on whether it's touch or not. SASS makes this easy:

[css]
.menu
  .touch &
    position: relative
  &:hover
  .menu-item
    .no-touch &
      position: relative
    .submenu
      position: absolute
      top: 0
      left: 100%
[/css]

There are also some interesting effects of touch devices' handling of hover states, and how this affects a CSS dropdown menu. But that's another post.