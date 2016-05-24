# default.css
A sensible default HTML style in under 50 lines of CSS.
Here's how it looks: **[live demo](http://waldyrious.github.io/default.css)**

## Usage

To use **`default.css`** in your project,
[download the source](https://raw.githubusercontent.com/waldyrious/default.css/master/default.css),
or simply place the following in your HTML:

```html
<link rel="stylesheet" href="http://rawgit.com/waldyrious/default.css/master/default.css" />
```

## Why yet another CSS framework/reset?

This is not a CSS framework, nor it is a [reset]() or [normalize]().

**`default.css`** is simply a small set of rules
that instantly makes plain HTML look much more polished and readable.

In short, its goal is to **improve upon HTML's default raw styling**.

See for yourself: [before]() / [after]().

## What's in it?

Glad you asked! **`default.css`** combines a set of simple rulesets
identified by people who noticed how a few tiny tweaks to the default HTML styling
produce massive improvements in legibility and layout.

The entire stylesheet consists of only 20 rulesets,
whose origin and motivation is detailed below:

1. From **[Fluidity](http://fluidity.sexy)**,
   make HTML more responsive:
   ```css
   img, canvas, iframe, video, svg, select, textarea { max-width: 100%; }
   ```
   This rule allows elements that don't adjust to the size of the container by default
   to behave like the rest of the basic HTML elements
   like, say, paragraphs, which flow the text as the window resizes.

2. From **[CSS Tricks](https://css-tricks.com/box-sizing)**:
   [Adjust the box model](https://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug#Support_for_Internet_Explorer.27s_box_model)
   to match intuitive expectations  
   This ensures that when defining sizes of elements in CSS,
   they better match the mental model of a physical box,
   whose dimensions always refer to the box itself, including potential padding,
   but never its content.
   ```css
   html { box-sizing: border-box; } *, *:before, *:after { box-sizing: inherit; }
   ```
   
3. Size text according to screen width (adapted from http://adamkaplan.me/grid)
   ```css
   html { font-size: 100%; }
   @media (min-width: 40rem) { html { font-size: 112%; } }
   @media (min-width: 65rem) { html { font-size: 120%; } }
   ```

4. From **[Better Motherfucking Website](http://bettermotherfuckingwebsite.com)**,
   improved typography:
   > **Let it breathe**  
   > Look at lines 1 and 2 of some shitty website you're building. Assuming they're not married they probably shouldn't be humping.
   > The defaults are trash -- pick a minimum line-height: 1.4 for body copy. Headings should be tighter. If you can't see that...piss off.

   > **A little less contrast**  
   > Black on white? How often do you see that kind of contrast in real life? Tone it down a bit, asshole. I would've even made this site's background a nice #EEEEEE if I wasn't so focused on keeping declarations to a lean 7 fucking lines.

   > **Line-width, motherfucker**  
   > Looking at an LCD screen is strainful enough. Don't make me read a line of text that's 200 fucking characters long. Keep it to a nice 60-80 and users might actually read more than one sentence of your worthless dribble.

   ```css
   h1, h2, h3, h4, h5, h6 { line-height: 1.2; }
   body { line-height: 1.6; color: #444; margin: 1em auto; max-width: 35em; }
   ```
   This is the set of rules that makes the biggest visual difference, even though it fits in a tweet.
   It's quite opinionated, sure, and not right for every design -- but a much better default to start from.
   The only rule I didn't include was the font size, which is better handled by Grid above.

5. Clean table style table (adapted from http://getskeleton.com)
   ```css
   table { border-collapse: collapse; font-family: sans-serif; font-size: 90%; }
   th, td { padding: 0 .75em; text-align: left; border-bottom: 1px solid #ddd; }
   th { border-bottom-color: #aaa; }
   th:first-child, td:first-child { padding-left: 0; }
   th:last-child, td:last-child { padding-right: 0; }
   ```

6. Additional adjustments (my own)
   ```css
   a { text-decoration: none; } a:hover { text-decoration: underline; }
   a { color: RoyalBlue; } a:visited { color: Indigo; }
   pre, code, kbd, samp { padding: .2em .5em; background: #eee; border-radius: 4px; }
   img { margin: .5em; }
   textarea { vertical-align: text-top; }
   ```
