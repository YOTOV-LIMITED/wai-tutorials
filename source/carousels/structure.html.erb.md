---
title: Structure & Basic Styles
status: editors-draft
order: 2
wcag_success_criteria:
  - 1.3.1
  - 2.4.6
wcag_techniques:
  - G130
  - H42
  - H48
---

As with every part of a website, a good markup structure is the base for a carousel to work in an accessible way. This helps the carousel to be easily discovered and also allows non-visual users to interpret the individual slides in a meaningful way.

## Carousel Heading

As a carousel is a set of content pieces, that share some properties, it is useful to add a [heading](/background/headings.html) directly in front of the carousel, for example:

{::nomarkdown}
<%= code_start %>
{:/nomarkdown}

~~~html
<h3>Featured articles</h3>

<h3>Editor’s picks</h3>

<h3>Price Winners</h3>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

The heading has to be in the correct heading structure of the document, for example the heading of the next section of the document should be the same as the one before the carousel.

## Carousel Skeleton

Depending on the content of the individual slides, a there are some possibilities of how the basic skeleton may look like. For a simple list of images or teasers, a list (`<ul>`) may be perfectly sufficient, if complete articles are the content of the carousel, the use of `<article>` elements for every slide may be more appropriate.

{::nomarkdown}
<%= code_start('', 'Simple content') %>
{:/nomarkdown}

~~~html
<div class="carousel">
    <ul>
        <li class="slide">…</li>
        <li class="slide">…</li>
        <li class="slide">…</li>
    </ul>
</div>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

{::nomarkdown}
<%= code_start('', 'Complete articles') %>
{:/nomarkdown}

~~~html
<div class="carousel">
    <article class="slide">…</article>
    <article class="slide">…</article>
    <article class="slide">…</article>
</div>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

To allow semantic flexibility, CSS should use classes to make the carousel look good. Those classes should also be used in the JavaScript to provide the necessary interaction. Note that there are no elements in the code for buttons or pagination indicators, as they are only added with JavaScript when they are needed. This [Progressive Enhancement](/background/progressive-enhancement.html) principle makes sure that the content is always available even if the JavaScript fails to load.

## Slide Construction

Slides can consist of various elements, including headings (which should be one level below the main carousel heading) and links.

### Image Content
{:.ex}

When using images in a slide show, each image needs to have an alternative text that describes it according to the [Images tutorial](/images/index.html).

{::nomarkdown}
<%= code_start %>
{:/nomarkdown}

~~~html
<h3>Photos of our trip to Paris:</h3>
<div class="carousel">
  <ul>
      <li class="slide">
          <img src="path/to/image.jpg" alt="Alternative text">
      </li>
      <li class="slide">
          <img src="path/to/image.jpg" alt="Alternative text">
      </li>
      <li class="slide">
          <img src="path/to/image.jpg" alt="Alternative text">
      </li>
  </ul>
</div>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

### Complex Content
{:.ex}

Complex content should use headings, so the content is easily findable. If used as teasers, links should be used in a descriptive manner. In the example below, background images are used, as the images are for illustration only and do only visually support the content of the slide. The content of the image itself is not relevant in this case.

{::nomarkdown}
<%= code_start %>
{:/nomarkdown}

~~~html
<h3>Featured Articles:</h3>
<div class="carousel">
    <ul>
        <li class="slide" style="background-image: url('teddy1.jpg');">
            <h4>Space Teddy production reaches all-time high</h4>
            <p>
                Teddies in Space Inc. has released outstanding numbers for the last solar year.
                <a href="…">Full Annual Report</a>
            </p>
        </li>
        <li class="slide" style="background-image: url('teddy2.jpg');">
            <h4>New Space Teddy Announced!</h4>
            <p>
                Space Teddy 6 wears an aluminum space suit. Sapphire glass eyes are first used universe-wide.
                <a href="…">Everything about the new model</a>
            </p>
        </li>
        <li class="slide" style="background-image: url('teddy3.jpg');">
            <h4>Adventures of the Space Teddy</h4>
            <p>
                Using modern HTML5 technologies, the latest installment of our game performs great on your computer, tablet, or mobile.
                <a href="…">Play the Game here!</a>
            </p>
        </li>
    </ul>
</div>
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

## Basic Styling

Basic styling makes sure that the slides are looking good on their own, even if the JavaScript fails to load. More CSS is used in the following parts of the tutorial while the example is getting enhanced into a fully-fledged carousel.

### Accessibility Requirement: Contrast Ratio

By using semi-transparent backgrounds, the [contrast ratio](/background/contrast-ratio.html) between text and the background-image is sufficient for low vision users and in situation where the contrast of the screen itself is low, like in direct sunlight.

{::nomarkdown}
<%= code_start %>
{:/nomarkdown}

~~~css
.slide h4 {
  background-color: rgba(255,255,255,.8);
}
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}

{::nomarkdown}
<%= notes_start %>
{:/nomarkdown}

**Note:** To keep the demo simple, a fixed-width implementation of a carousel is implemented in this tutorial.

{::nomarkdown}
<%= notes_end %>
{:/nomarkdown}

{::nomarkdown}
<%= sample_start %>
{:/nomarkdown}

<h3 role="presentational">Featured Articles:</h3>
<div class="carousel">
    <ul>
        <li class="slide" style="background-image: url('../../img/ex-teddy1.jpg');">
            <h4>Space Teddy production reaches all-time high</h4>
            <p>
                Teddies in Space Inc. has released outstanding numbers for the last solar year.
                <a href="…">Full Annual Report</a>
            </p>
        </li>
        <li class="slide" style="background-image: url('../../img/ex-teddy2.jpg');">
            <h4>New Space Teddy Announced!</h4>
            <p>
                Space Teddy 6 wears an aluminum space suit. Sapphire glass eyes are first used universe-wide.
                <a href="…">Everything about the new model</a>
            </p>
        </li>
        <li class="slide" style="background-image: url('../../img/ex-teddy3.jpg');">
            <h4>Adventures of the Space Teddy</h4>
            <p>
                Using modern HTML5 technologies, the latest installment of our game performs great on your computer, tablet, or mobile.
                <a href="…">Play the Game here!</a>
            </p>
        </li>
    </ul>
</div>

<style>
  .carousel, .slide {
    width: 640px;
    padding:0;
    margin: 0;
    /* overflow: hidden; */
  }
  .carousel {
    position: relative;
  }
  .carousel ul {
    margin:0;
    padding: 0;
  }
  .slide {
    /*position: absolute;*/
    height: 480px;
    background-size: cover;
    position: relative;
    margin-bottom:1em;
    border:1px solid #333;
  }
  .slide h4 {
    display:inline-block;
    float:righ;
    font-size: 1.25em;
    margin:0;
    padding: .25em;
    text-align: right;
    background-color: rgba(255,255,255,.8);
    float:right;
    border-radius: 0 0 0 .5em;
  }
  .slide p {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    margin:0;
    clear:both;
    padding: 1em 5em 1em 3em;
    background-color: rgba(255,255,255,.8);
  }
  .slide a {
    display:block;
    text-align: right;
  }
</style>

{::nomarkdown}
<%= sample_end %>
{:/nomarkdown}

{::nomarkdown}
<%= code_start('','CSS') %>
{:/nomarkdown}

~~~css
  .carousel, .slide {
    width: 640px;
    padding:0;
    margin: 0;
  }
  .carousel {
    position: relative;
  }
  .carousel ul {
    margin:0;
    padding: 0;
  }
  .slide {
    height: 480px;
    background-size: cover;
    position: relative;
    margin-bottom:1em;
    border:1px solid #333;
  }
  .slide h4 {
    display:inline-block;
    float:righ;
    font-size: 1.25em;
    margin:0;
    padding: .25em;
    text-align: right;
    background-color: rgba(255,255,255,.8);
    float:right;
    border-radius: 0 0 0 .5em;
  }
  .slide p {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    margin:0;
    clear:both;
    padding: 1em 5em 1em 3em;
    background-color: rgba(255,255,255,.8);
  }
  .slide a {
    display:block;
    text-align: right;
  }
~~~

{::nomarkdown}
<%= code_end %>
{:/nomarkdown}