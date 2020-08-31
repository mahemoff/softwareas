---
id: 358
title: 'ImageMagick: One-Second Gradient Images'
date: 2006-11-21T12:58:16+00:00
author: admin
layout: post
guid: http://www.softwareas.com/imagemagick-one-second-gradient-images
permalink: /imagemagick-one-second-gradient-images/
dsq_thread_id:
  - "375199635"
categories:
  - SoftwareDev
---
<tags>Command-Line, CSS, Design, Gradient, HTML, ImageMagick, Tutorial, Web2.0</tags>

Problem: The great thing about standards-based web development is how easily you can tweak the look by modifying CSS properties. However, contemporary <del>gimmicks</del>constructs like curved surfaces and gradients aren't yet supported, which means simple tweaks - like changing a colour - usually require a round-trip between a graphical editor (Photoshop, Gimp, etc) and your CSS file. Or, you might be able to just make the change in your editor, but even that will take a lot longer than editing the CSS file, anywhere between 10 and 100 times as long (usually 1-5 minutes versus 1-5 seconds).

Solution: Generate images on the command line. Using ImageMagick, it's possible to do tons of things on the command line. <a href="http://imagemagick.sourceforge.net">ImageMagick</a>, which usually is executed with the "convert" command, is probably installed on your Unix/OSX machine already and your Linux web host as well (many Captcha utilities use ImageMagick to create and warp the image). It's extremely powerful. Until today, I'd only ever used it for transformations, but now I'm using it for image generation too. Unfortunately, it's not too well documented - the official docs are thorough, but completely lack examples (a common problem with open-source projects is documents oriented around the features rather than the typical tasks, and <a href="http://softwareas.com/documentation-needs-examples-duh/">often in the absence of any useful examples</a> that in this case would show how to construct a command-line). Fortunately, there's <a href="http://www.cit.gu.edu.au/~anthony/graphics/imagick6/">this set of examples</a>.

You can generate (and therefore easily tweak) logos, curved surfaces, etc, but what I'll talk about here is gradient images. If you want, jump straight to the one-line examples below. The trick relies on several features of ImageMagick, pseudo-images, image stacks, and appending:

<ul>
<li>ImageMagick usually works by converting one image to another, e.g. "convert -transparent white normal.gif transparent.gif". But we want to create an image from nowhere, so what ImageMagick lets us do is create an input image from thin air, a <a href="http://imagemagick.sourceforge.net/http/www/formats.html">"pseudo-image"</a>. To create a pure red image, we use a pseudo-image of type Canvas, mysteriously named "xc". Go on, type this in right now to make a pure red GIF image:<br/>
<tt>convert -size 3000x120 xc:red /tmp/red.gif</tt>
</p>
<p>
Canvas is only one example of a pseudo-image; there are pseudo-images based on patterns, fractal generation, etc. (In fact, there is a pseudo-image called "rose:" which is actually a photo of a rose that ships with ImageMagick, a brilliant feature as it means people can write <a href="http://www.cit.gu.edu.au/~anthony/graphics/imagick6/mosaics/">tutorials that manipulate the image</a> without requiring you to download it.) We can generate a gradient image using a gradient pseudo-image.
</p>
</li>
<li>Optionally, it's useful to work with an <a href="http://www.imagemagick.org/script/command-line-processing.php">"image stack"</a> - sometimes you need more than one transformation to get to your desired image. Instead of dumping all those intermediate images in temp files along the way, ImageMagick offers a nice, clean way to build a transient image. It's like saying "final=a+(b-c)" instead of "temp=b-c; final=a+temp" (the <a href="http://www.refactoring.com/catalog/replaceTempWithQuery.html">Replace Temp with Query</a> refactoring :-)). A transient image is created with parentheses (example below).
</li>
<li>Images can be combined together: <tt>convert a.gif b.gif -append c.gif</tt> will stack a on b vertically to output c. (+append will stack horizontally).</li>
</ul>

So how to generate a gradient image?

Simplest technique is:

<tt>convert -size 2000x100 gradient:#4b4-#bfb /tmp/greenbar.gif</tt>

<img src="http://img226.imageshack.us/img226/5227/greenbarng2.gif" width="350" height="100">

Great! Now we can tweak the colour without going through all the hassle of mousing around a graphics utility.

Say we want that bar to be the top of a box, where the rest of the box is the same colour as the bottom of the gradient bar (so the bar blends directly into it). One way is to keep the gradient image as is, and alter the CSS background-color, so we have a CSS line like:

<tt>gradientBox { background-image: url(greenbar.gif); background-repeat: no-repeat; background-color:#bfb; }</tt>

That's neat, but does require two updates each time you want to change the colour (one to the imagemagick command-line and one to the CSS). You could also generate a gradient leading to colour "none", which means it's transparent - still have to update the CSS to update the other colour but there's no redundancy. Another way is to build a big image (at least during development). We can do that by stacking a single-colour image under the gradient image, using the transient image and appending techniques described above (the parentheses are escaped with \ for the Unix command line):

<tt>convert \(gradient:#995-#cc9 -size 3000x120\) -append \(xc:#c9 -size 3000x1000\) /tmp/greenbox.gif</tt>

<img src="http://img226.imageshack.us/img226/2442/greenboxqg8.gif" width="350" height="150">

BTW One thing about these gradient images is that GIF format (and PNG too I think) strangely doesn't compress them at all well - increase the width from 1 pixel to 100 pixels and the file size will also increase by a factor of 20 to 50. It's surprising as the information content is virtually identical, but the consequence anyway is that you should generally use just a single pixel wide and CSS style <tt>background-repeat: repeat-x</tt> to stretch it out.

Now you can update your bling with the touch a key!