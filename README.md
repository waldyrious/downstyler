# default.css
A sensible minimal style for plain HTML in under 50 lines of CSS.

### [live demo](http://waldyrious.github.io/default.css)

## How? (a.k.a. "Usage")

To use **`default.css`** in your project,
[download the source](https://raw.githubusercontent.com/waldyrious/default.css/master/default.css),
or simply place the following in your HTML:

```html
<link rel="stylesheet" href="http://rawgit.com/waldyrious/default.css/master/default.css" />
```

## Why? (a.k.a. "How is this different from existing tools?")

**`default.css`** takes inspiration in pre-existing similar tools,
but fills a different niche:

- The original [css reset](http://meyerweb.com/eric/tools/css/reset/)
  unsets browsers' default styles
  to provide a clean slate upon which a stylesheet can be built;
- [normalize.css](https://necolas.github.io/normalize.css/)
  specifically targets cross-browser differences in styling
  and harmonizes them to provide consistent look and behavior everywhere;
- [sanitize.css](https://jonathantneal.github.io/sanitize.css/)
  actively attempts to provide a comprehensive set of defaults for HTML elements,
  building upon normalize.css.

**`default.css`**, on the other hand,
aims to provide a the smallest, most unintrusive set of CSS rules
that remains as close as possible to the default styling
while still getting readable and visually pleasing output.

See for yourself how plain HTML markup looks
[without any styling](http://waldyrious.github.io/default.css/unstyled.xhtml)
vs.
[using default.css](http://waldyrious.github.io/default.css).

<!-- TODO: insert side-by-side screenshots here. -->

## What? (a.k.a. "Which styles are included?")

**`default.css`** combines a set of simple rulesets
identified by a bunch of smart people
who noticed how only a few minor tweaks to the default HTML styling
can produce massive improvements in legibility and layout.

The entire stylesheet consists of only ~25 rulesets,
whose origin and motivation is detailed below:

1. From **[Fluidity](http://fluidity.sexy)**,
   by Adam Morse ([@mrmrs](https://github.com/mrmrs)):  
   Make HTML more responsive:
   > HTML is **almost** 100% responsive by default. These 247 bytes of css fix the 'almost' part.

   ```css
   img, canvas, iframe, video, svg, select, textarea { max-width: 100%; }
   pre { overflow-x: auto; }
   ```
   These rules allow elements that don't adjust to the size of the container by default
   to behave like the rest of the basic HTML elements
   like, say, paragraphs, which flow the text as the window resizes.

2. From **[W3C's CSS Device Adaptation Module Level 1]
   (https://www.w3.org/TR/css-device-adapt/#width-and-height-properties)**:
   Restore normal viewport size on mobile browsers:
   ```css
   @viewport { width: device-width; initial-scale: 1; }
   ```

3. From **[CSS Tricks](https://css-tricks.com/box-sizing)**,
   by Marie Mosley ([@mariemosley](https://github.com/mariemosley)):  
   [Adjust the box model](https://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug#Support_for_Internet_Explorer.27s_box_model)
   to match intuitive expectations.  
   This ensures that when defining sizes of elements in CSS,
   they better match the mental model of a physical box,
   whose dimensions always refer to the box itself, including potential padding,
   but never its content.
   ```css
   html { box-sizing: border-box; } *, *:before, *:after { box-sizing: inherit; }
   ```
   
4. From **[CSS Tricks](https://css-tricks.com/molten-leading-css/)**,
   by Chris Coyier ([@chriscoyier](https://github.com/chriscoyier))
   from an original idea by Tim Brown ([@tbrown](https://github.com/tbrown)):  
   Size text according to screen width
   ```css
   html { font-size: 16px; }
   @media (min-width: 600px) { html { font-size: calc(0.4vw + 13.6px) } }
   ```
   These rules allow text to resize dynamically to adapt to the width of the container.
   It's the same concept as [flowtype.js](http://simplefocus.com/flowtype/), but in CSS!

5. From **[Better Motherfucking Website](http://bettermotherfuckingwebsite.com)**, by Drew McConville ([@drewmcc](https://github.com/drewmcc)),
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

6. From **[Skeleton](http://getskeleton.com)**, by Dave Gamache ([@dhg](https://github.com/dhg)):  
   Clean table style:
   ```css
   table { border-collapse: collapse; font-family: sans-serif; font-size: 90%; }
   th, td { padding: 0 .75em; text-align: left; border-bottom: 1px solid #ddd; }
   th { border-bottom-color: #aaa; }
   th:first-child, td:first-child { padding-left: 0; }
   th:last-child, td:last-child { padding-right: 0; }
   ```

7. Additional adjustments (my own)
   ```css
   a { text-decoration: none; } a:hover { text-decoration: underline; }
   a { color: RoyalBlue; } a:visited { color: Indigo; }
   pre, code, kbd, samp { padding: .2em .5em; background: #eee; border-radius: 4px; }
   img { margin: .5em; }
   textarea { vertical-align: text-top; }
   ```
