---
id: markup
layout: default
meta_title: Markup
title: Markup
---

# Markup

Here's a barebones example of a fully working reveal.js presentation:
```html
<html>
  <head>
    <link rel="stylesheet" href="dist/reveal.css">
    <link rel="stylesheet" href="dist/theme/white.css">
  </head>
  <body>
    <div class="reveal">
      <div class="slides">
        <section>Slide 1</section>
        <section>Slide 2</section>
      </div>
    </div>
    <script src="dist/reveal.js"></script>
    <script>
      Reveal.initialize();
    </script>
  </body>
</html>
```

The presentation markup hierarchy needs to be `.reveal > .slides > section` where the `section` element represents one slide and can be repeated indefinitely.

If you place multiple `section` elements inside of another `section` they will be shown as [vertical slides](/features/vertical-slides). The first of the vertical slides is the "root" of the others (at the top), and will be included in the horizontal sequence. For example:

```html
<div class="reveal">
  <div class="slides">
    <section>Single Horizontal Slide</section>
    <section>
      <section>Vertical Slide 1</section>
      <section>Vertical Slide 2</section>
    </section>
  </div>
</div>
```
<div class="reveal example-deck">
  <div class="slides">
    <section>Single Horizontal Slide</section>
    <section>
      <section>Vertical Slide 1</section>
      <section>Vertical Slide 2</section>
    </section>
  </div>
</div>

It's also possible to write presentations using [Markdown](/content/markdown).

## Viewport
The reveal.js viewport is the wrapper DOM element that determines the size of your presentation on a web page. By default, this will be the `body` element. If you're including multiple presentations on the same page each presentations `.reveal` element will act as their viewport.

The viewport is always decorated with a `reveal-viewport` class reveal.js is initialized.

## Slide Visibility
When preparing a presentation it can sometimes be helpful to prepare optional slides that you may or may not have time to show. This is easily done by appending a few slides at the end of the presentation, however this means that the reveal.js progress bar and slide numbering will hint that there are additional slides.

To "hide" those slides from reveal.js' numbering system you can add a `data-visibility` attribute to the slide.
```html
<section data-visibility="uncounted"></section>
```

## Slide States

If you set `data-state="purple-haze"` on a slide `<section>`, "purple-haze" will be applied as a class on the [viewport element](#viewport) when that slide is opened. This allows you to apply broad style changes to the page based on the active slide.

```html
<section data-state="purple-haze"></section>
```

```css
/* CSS */
.purple-haze {
  filter: drop-shadow(0 0 10px purple);
}
```

You can also listen to these changes in state via JavaScript:

```javascript
Reveal.on( 'purple-haze', () => {
  console.log('🎸');
} );
```