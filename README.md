# unstyle

A tool to fight CSS bloat.

**Visit [the web page](http://waldyrious.github.io/unstyle)**
for a live demo and usage instructions.

## Differences from existing tools

**`unstyle`** takes inspiration in pre-existing similar tools,
but fills a different niche:

- The original [css reset](http://meyerweb.com/eric/tools/css/reset/)
  completely wipes out all of the browser's default styles
  to provide a clean slate upon which custom stylesheets can be built;
- [normalize.css](https://necolas.github.io/normalize.css/)
  is much less drastic, and focuses on ironing out cross-browser styling differences
  and harmonizing them to provide consistent look and behavior everywhere;
- [sanitize.css](https://jonathantneal.github.io/sanitize.css/)
  is kind of a more comprehensive version of normalize.css, covering all HTML elements,
  but using hand-picked default styles, rather than reset.css's nuclear approach.

**`unstyle`**, on the other hand, is intended as a stand-alone style
— one that pays homage to HTML's natural readability and flexibility
and attempts to produce readable and visually pleasing output
while remaining as close as possible to the default look of unstyled HTML.

It follows the philosophy brilliantly championed by [Fluidity](http://fluidity.sexy),
[MotherfuckingWebsite.com](http://motherfuckingwebsite.com)
and [BetterMotherfuckingWebsite.com](http://bettermotherfuckingwebsite.com),
which (with various degrees of —ahem— enthusiasm)
praise the merits of plain HTML as a format for rich documents.

Here's a live comparison of how plain HTML markup looks
[without any styling](http://waldyrious.github.io/unstyle/demo-raw.xhtml)
vs.
[using unstyle](http://waldyrious.github.io/unstyle/demo-unstyle.xhtml).

<!-- TODO: insert side-by-side screenshots here. -->

## Details of included CSS rules

**`unstyle`** combines elements from various simple rulesets
created to demonstrate how only a few minor tweaks to the default HTML styling
can produce massive improvements in legibility and layout.

The origin and motivation of each ruleset is detailed below:

- From **[Fluidity](http://fluidity.sexy)**,
  by Adam Morse ([@mrmrs](https://github.com/mrmrs)):  
  Make HTML more responsive:
  > HTML is **almost** 100% responsive by default. These 247 bytes of css fix the 'almost' part.

  ```css
  img, canvas, iframe, video, svg, select, textarea { max-width: 100%; }
  pre { overflow-x: auto; }
  ```
  These rules allow elements that don't adjust to the size of the container by default,
  to behave like the rest of the basic HTML elements
  like, say, paragraphs, which flow the text as the window resizes.

- From **[W3C's CSS Device Adaptation Module Level 1]
  (https://www.w3.org/TR/css-device-adapt/#width-and-height-properties)**:
  Restore normal viewport size on mobile browsers:
  ```css
  @viewport { width: device-width; initial-scale: 1; }
  ```

- From **[CSS Tricks](https://css-tricks.com/box-sizing)**,
  by Marie Mosley ([@mariemosley](https://github.com/mariemosley)):  
  Adjust the box model to match [intuitive expectations]
  (https://en.wikipedia.org/wiki/Internet_Explorer_box_model_bug#Support_for_Internet_Explorer.27s_box_model).  
  This ensures that when defining sizes of elements in CSS,
  they correspond better to the mental model of a physical box,
  whose dimensions normally refer to the box itself (outer size),
  not to its content alone (inner size).
  ```css
  html { box-sizing: border-box; } *, *:before, *:after { box-sizing: inherit; }
  ```
   
- From **[CSS Tricks](https://css-tricks.com/molten-leading-css/)**,
  by Chris Coyier ([@chriscoyier](https://github.com/chriscoyier))
  from an original idea by Tim Brown ([@tbrown](https://github.com/tbrown)):  
  Size text according to screen width
  ```css
  html { font-size: 16px; }
  @media (min-width: 600px) { html { font-size: calc(0.4vw + 13.6px) } }
  ```
  These rules allow text to resize dynamically to adapt to the width of the container.
  It's the same concept as [flowtype.js](http://simplefocus.com/flowtype/),
  but implemented entirely in CSS.

- From **[Better Motherfucking Website](http://bettermotherfuckingwebsite.com)**, by Drew McConville ([@drewmcc](https://github.com/drewmcc)):
  Improve default typography:
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
  Note: This is the set of rules that makes the biggest visual difference, even though it fits in a tweet.
  It's quite opinionated, sure, and not right for every design -- but a much better default to start from.
  The only rule not included here was the font size,
  which is better handled by the responsive text sizing described in the CSS Tricks entry above.

- From **[Skeleton](http://getskeleton.com)**, by Dave Gamache ([@dhg](https://github.com/dhg)):  
  Clean table style:
  ```css
  table { border-collapse: collapse; font-family: sans-serif; font-size: 90%; }
  th, td { padding: 0 .75em; text-align: left; border-bottom: 1px solid #ddd; }
  th { border-bottom-color: #aaa; }
  th:first-child, td:first-child { padding-left: 0; }
  th:last-child, td:last-child { padding-right: 0; }
  ```

- Additional adjustments (my own)
  ```css
  a { text-decoration: none; } a:hover { text-decoration: underline; }
  a { color: RoyalBlue; } a:visited { color: Indigo; }
  pre, code, kbd, samp { padding: .2em .5em; background: #eee; border-radius: 4px; }
  img { margin: .5em; }
  textarea { vertical-align: text-top; }
  ```
