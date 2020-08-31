---
id: 403
title: CSS Coding Style and the Unbearable Tendency for People to Adore Whitespace in their Source Code
date: 2007-10-22T22:21:37+00:00
author: admin
layout: post
guid: http://www.softwareas.com/css-coding-style-and-the-unbearable-tendency-for-people-to-adore-whitespace-in-their-source-code
permalink: /css-coding-style-and-the-unbearable-tendency-for-people-to-adore-whitespace-in-their-source-code/
dsq_thread_id:
  - "375573404"
categories:
  - SoftwareDev
tags:
  - AjaxPatterns
  - Coding Style
  - CSS
  - HTML
  - Links
  - Programming
  - Web
---
<a href='http://writerresponsetheory.org/wordpress/2006/05/12/plain-text-weird-text/'><img src='http://picupper.com/2007/10/22/obfuscated-arachnid2004.png.jpg'/></a>

CSS coding style doesn't get a lot of play. Most people are happy to stick with the convention of one property per line, like this:
[css]
#score {
  background: yellow;
  width: 12em;
  border: 1px solid orange
  padding: 2em;
  margin: 3em 0;
  display: none;
}
[/css]

I, for one, can't stand that style. I'm heavily biased towards information-dense coding styles, which don't have much whitespace. People mechanically argue "oh but whitespace is so important etc" as if we were designing a modern art installation. Well, whitespace is indeed essential, but you have to discriminate between a touch of elegant whitespacing for the sake of clarity, and "oh dear! My 80-column row seems to have just 12 characters on it. Come to think of it, every row on my 30-inch Cinema Display has 12 characters on it." Seriously, I don't know why anyone would use an 80-column terminal anymore, unless they enjoy coding on their iPhone. I tend to think 120 or 160 is ideal; any more than that and most people won't be able to see the whole thing without moving their head. Anyway, I'll be conservative and assume 80 columns. The average end column in the above code snippet is roughly 15, which means in your scrawny 1975 80-column terminal, you're filling 20% of it with information and 80% with whitespace.

There's an old figure that says the average programmer codes 10 lines per day. It's obviously not a very accurate figure and maybe it was meant to include all the non-programmers on the project or something, but the point is interesting, as there's probably some reasonably consistent <i>LOC per developer</i> figure (obligatory <a href="http://en.wikipedia.org/wiki/Mutatis_mutandis">mutatis mutandis</a> caveat). Seizing on this historical figure, Bruce Eckel said a while ago (paraphrasing) "if I only get 10 lines a day, I want them to be good ones".

That's why I favour information-dense coding styles. As a programmer, you're supposed to be an expert user who spends all day in front of the same system. This is a typical example of a situation which demands a <a href="http://www.mit.edu/~jtidwell/language/sovereign_posture.html">"Sovereign Posture"</a>. It's an <b>expert system</b>. When people long for glorious pastures of whitespace, they're ignoring the fact that with sufficient practice, they'll be virtually as proficient at reading and writing a more information-dense style, and vastly more efficient by having so much more code available at any time. It's the same reason why Real Programmers commit to learning Unix and Vi or Emacs; if you're going to spend decades working in this environment, why wouldn't you spend a few days committing to the most efficient tools available?

For the record, I still have plenty of whitespace in my programs, but when there is a decision to be made between one popular convention and another, I almost always go for the one which reduces whitespace. I have enough faith in programmers' pattern-detection skills to know that in time, they will be fine with either style, but the one with less whitespace will always give them more bang for their Cinema Display buck.

Back to CSS. Here's how I'd format the above snippet:

[css]
#score { background: yellow;  border: 1px solid orange;
             width: 12em;  padding: 2em;  margin: 3em 0;
             display: none;
}
[/css]

What I do is group similar attributes on each line. I'm pragmatic about the precise rules. If it's just a handful of properties, I'll stick them all on the same line. If there's more than that, then typically I'll have one line for appearance  (colour, fonts, etc.), another for layout, and possibly more for other things like display settings or detailed positioning. You also don't need whitespace between each rule either, so you can often end up with a whole sequence of related one-liner rules:
[css]
/******************************************************************************
   SCOREBOARD
 *****************************************************************************/
#scoreboard { background: black; color: white; }
#homeTeam, #awayTeam { color: pink; text-align: right; position: absolute; }
#homeTeam { top:20px; left: 120px; font-size: 8em; }
#awayTeam { top:80px; right: 120px; font-size: 5em; }
...

/******************************************************************************
   ARENA
 *****************************************************************************/
.player { color: #f99; }
.runner { color: #99a; }
...
[/css]

This format is not only denser but also easier to comprehend as related properties are grouped together. The typical one-line-per-property format tends to include a random jumble of properties; rarely does any thought go to the order in which the properties appear.

Another thing that helps with CSS brevity is learning shorthand formats. Use "border: 1px solid orange" instead of "border-width: 1px; border-style: solid; border-color: orange". Use "margin: 3em 0;" instead of "margin-left: 3em; margin-right: 3em;", and so on.