<div id="top"></div>

# README.css

## Is & is'nt

---

**This is:** A collection of concise and practical notes for experienced developers of the most common features of CSS.

**This is not:** a reference.

CSS has a flexible and diverse set of property values for style rules. Because writing out all possible values is beyond the scope of this guide, mostly just common properties and shorthands are listed. For the few property values listed, they represent common but not exhaustive lists of values. For an exhaustive reference please refer to [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference).

Short for Cascading Style Sheets, CSS is a web technology along side with HTML, JavaScript and WASM. CSS was designed to style HTML elements and describe how to render them on various media such as print, screen, speech and more. CSS is standardized according to the [W3C specification](https://www.w3.org/Style/CSS/#specs).

## Table of Contents

---

- [CSS](#css)
  - [The Cascade](#the-cascade)
  - [Units](#units)
  - [Style Rule Syntax](#style-rule-syntax)
  - [Selectors](#selectors)
  - [Pseudo](#pseudo)
  - [Text](#text-styling)
  - [Position](#position)
  - [Box Properties](#box-properties-and-styling)
  - [List](#list-styling)
  - [Images](#images)
  - [Flexbox](#flexbox)
  - [Gridbox](#gridbox)
  - [UI](#ui)
  - [Transform](#transform)
  - [Transitions](#transitions)
  - [Animations](#animations)
  - [Media Queries](#media-queries)
  - [Variables](#variables)
- [SASS](#sass)
  - [Variables](#variables)
  - [Nesting](#nesting)
  - [Other Stuff](#other-stuff)
- [CSS Modules & CSS-in-JS](#css-in-js)

## CSS

<p align="right"> (<a href="#top">back to top</a>) </p>

---

### The Cascade

```css
p {
  color: black;
}

p {
  color: white;
}
```

What is the result of the code above? CSS utilizes an algorithm to determines ambiguities like this, we refer to this as the Cascade. There are four aspects to it.

- Order: CSS can come from `<link>`, `<style>`, or **inline css** with the "style" attribute. Declarations later in the code takes priority. Inline css overides any styles unless `!important` is used.

- Specificity: Each selector has a weighted score attributed that describes specificity. From least to most specific:
  - `element`
  - `class`
  - `ID`
- Origin...from least to most specific:

  - User Agent (Browser)
  - Local User (OS or extensions)
  - Authored CSS (Developer code)
  - Authored `!important`
  - Local User `!important`
  - User Agent `!important`

- Importance...from least to most specific:
  - normal style rule
  - animation rule
  - `!important` rule
  - transition rule

Note: The **CSSOM** is the CSS Object Model. This is a tree like data structure that describes the styling for the entire document.

### Units

#### Absolute Measurements

```css
%
cm
in
mm
pc
pt
px
```

#### Relative Measurements

```css
em
rem
vh
vw
ch
ex
gd
vm
fr
```

#### Angles

```css
deg
rad
grad
turn
```

#### Time

```css
ms
s
```

#### Color

```css
color name
rgb(x, y, z)
rgba(x, y, z, alpha)
#rrggbb
hsl(0, %, %)

```

### Style Rule Syntax

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
<selector > {
  <property>: <value>;
}

a {
  color: "blue";
}
```

### Selectors

<p align="right"> (<a href="#top">back to top</a>) </p>

#### Universal

```css
* {
}
```

#### ID

```css
#id {
}
```

#### Class

```css
.class {
}
```

#### Type

```css
h1,
h2,
h3 {
}
```

#### Adjacent Siblings

```css
h1 + p {
}
```

#### General Siblings

```css
h1 ~ p {
}
```

#### Children

```css
ul > li {
}
```

#### Descendant

```css
p a {
}
```

#### Attribute

```css
button[type="input"]
```

### Pseudo

<p align="right"> (<a href="#top">back to top</a>) </p>

#### Hover

```css
:hover {
}
```

#### Active

```css
:active {
}
```

#### Focus

```css
:focus {
}
```

#### Visited Links

```css
a:visited {
}
```

#### Links

It matches every unvisited \<a> or \<area> element that has an href attribute.

```css
class:link {
}
```

#### Checked Elements

```css
input:checked {
}
```

#### Disabled Elements

```css
input:disabled {
}
```

#### Enabled Elements

```css
input:enabled {
}
```

#### Not

```css
:not(p) {
}
```

#### First Line

```css
p::first-line {
}
```

#### First Letter

```css
p::first-letter {
}
```

#### First Child

```css
:first-child {
}
```

#### Last Child

```css
:last-child {
}
```

#### Only Child

```css
:only-child {
}
```

#### nth Child

```css
:nth-child {
}
```

#### First Element

```css
:first-of-type {
}
```

#### No Child

```css
:empty {
}
```

#### Before Element

```css
.class::before {
}
```

#### After Element

```css
.class::after {
}
```

### Text Styling

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
color: ;
font-family: ;
font-variant: ;
font-style: ;
font-weight: ;
font-size: ;
font-size-adjust: ;

line-height: ;
letter-spacing: ;
direction: ;

text-align: start | end | left | right | center;
text-overflow: clip | ellipsis | "-" | "" | <string>;
text-decoration: <color> <line> <style> <thickness>;
text-transform: capitalize | uppercase | lowercase | none | full-width;
text-outline: ;

word-spacing: ;
word-break: normal | anywhere | break-word;
overflow-wrap: normal | anywhere | break-word;
```

### Position

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
position: relative | static | absolute | fixed | sticky;
top: ;
bottom: ;
left: ;
right: ;
z-index: ;
vertical-align: top | middle | bottom;
```

### Box Properties and Styling

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
box-sizing: border-box | content-box;
display: inline | block | flex | grid | none;
visible: visible | hidden;
margin: <sizes> | auto;
padding: ;
width: <size> | max-content | min-content | auto;
height: <size> | max-content | min-content | auto;
max-height: ;
max-width: ;
overflow: <visible | clip | scroll | auto> <visible | clip | scroll | auto>; // shorthand for: overflow-x overflow-y

border: <style> <color> <thickness>;
border-radius: ;
box-shadow: <offset-x> <offset-y> <blur> <spread> <color>;
background-image: ;
background-size: ;
background-position: <sizes> | top | bottom | left | right | center;
background-repeat: repeat | repeat-x | repeat-y | no-repeat | round | space;
background-attachment: fixed | scroll | local;
background-origin: border-box | padding-box | content-box;
background-clip: border-box | padding-box | content-box | text;
background-color: ;
```

### List Styling

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
list-style: <type> <position> <image>;
```

### Flexbox

<p align="right"> (<a href="#top">back to top</a>) </p>

#### Parent Container

```css
display: flex;
flexflow: <row | column | row-reverse | column-reverse> < wrap | nowrap |
  wrap-reverse>; // adjusts to rtl ltr
justify-content: flex-start | flex-end | center | space-between | space-around |
  space-evenly | start | end | left | right; // main axis
align-items: stretch | flex-start | flex-end | center | baseline | first
  baseline | last baseline | start | end | self-start | self-end; // secondary axis
align-content: flex-start | flex-end | center | space-between | space-around |
  space-evenly | stretch | start | end | baseline | first baseline | last
  baseline;
gap: <row-gap> <column-gap>;
```

#### Child Container

```css
order: <int>;
flex: <grow> <shrink> <basis>;
align-self: auto | flex-start | flex-end | center | baseline | stretch;
```

### Gridbox

<p align="right"> (<a href="#top">back to top</a>) </p>

#### Parent Container

```css
display: grid;
grid-template-rows: ;
grid-template-columns: ;
grid-template-areas:
  "header header header"
  "footer footer footer";
gap: <row-gap> <column-gap>;
justify-items: start | end | center | stretch;
align-items: start | end | center | stretch;
justify-content: start | end | center | stretch | space-around | space-between |
  space-evenly;
align-content: start | end | center | stretch | space-around | space-between |
  space-evenly;
grid-auto-flow: row | column | row dense | column dense;
```

#### Child Container

```css
grid-column: <start-line> / <end-line> | <start-line> / span <value>;
grid-row: <start-line> / <end-line> | <start-line> / span <value>;
grid-area: <name> | <row-start> / <column-start> / <row-end> / <column-end>;
justify-self: start | end | center | stretch;
align-self: start | end | center | stretch;
```

### UI

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
cursor: none | help | pointer | text | wait | move | grab | grabbing | zoom-in |
  zoom-out; // more on MDN
appearance: none | auto; // more on MDN
scroll-behavior: ;
scroll-margin: ; // this is more than just styling, it impacts behavior
scroll-padding: ; // this is more than just styling, it impacts behavior
scroll-snap-align: ;
scroll-snap-type: ;
resize: none | both | horizontal | vertical;
```

### Transform

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
transform: none | matrix | matrix3d | translate3d | translateX | translateY |
  translateZ | scale | scale3d |scaleX | scaleY | scaleZ | rotate | rotate3d |
  rotateX | rotateY | rotateZ | skewX | skewY | skew | perspective;
transform-origin: ;
transform-style: ;
perspective: ;
perspective-origin: ;
backface-visibility: ;
```

### Transitions

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
transition: property | duration | timing function | delay;
```

### Animations and Keyframes

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
animation: name | duration | timing function | delay | iteration count |
  direction | fill mode | play state;

@keyframes slidein {
  from {
    margin-left: 100%;
    width: 300%;
  }

  75% {
    font-size: 300%;
    margin-left: 25%;
    width: 150%;
  }

  to {
    margin-left: 0%;
    width: 100%;
  }
}
```

### Media Queries

<p align="right"> (<a href="#top">back to top</a>) </p>

Media queries are used for the following:

To conditionally apply styles with the CSS @media and @import at-rules.
To target specific media for the \<style>, \<link>, \<source>, and other HTML elements with the media= attribute.
To test and monitor media states using the Window.matchMedia() and MediaQueryList.addListener() JavaScript methods.

media types: all, print, screen

media features: any-hover, any-pointer, aspect-ratio, color, color-gamut, color-index, display-mode, dynamic-range, forced-colors, grid, height, hover, inverted-colors, monochrome, orientation, overflow-block, overflow-inline, pointer, prefers-color-scheme, prefers-contrast, prefers-reduced-motion, resolution, scripting, update, video-dynamic-range, width.

logical operators: not, and, only

```css
@media (hover: hover) {
  ...;
}
@media (max-width: 12450px) {
  ...;
}
@media (color) {
  ...;
}
@media (min-width: 30em) and (orientation: landscape) {
  ...;
}
@media screen and (min-width: 30em) and (orientation: landscape) {
  ...;
}
@media (min-height: 680px), screen and (orientation: portrait) {
  ...;
}
@media (30em <= width <= 50em) {
  ...;
}
@media (not (color)) or (hover) {
  ...;
}
```

### Variables

<p align="right"> (<a href="#top">back to top</a>) </p>

```css
:root {
  --main-bg-color: white;
}

element {
  background-color: var(--main-bg-color);
}
```

---

## SASS

<p align="right"> (<a href="#top">back to top</a>) </p>

### Variables

```css
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: $font-stack;
  color: $primary-color;
}
```

### Nesting

```css
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li {
    display: inline-block;
  }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

### Other Stuff

SASS includes additional features to provide modularity, inheritance, and reusability. These include partials, modules and native inheritance. There are modern and simpler methods to tackle these problems, thus these features won't be covered here.

## CSS-in-JS

<p align="right"> (<a href="#top">back to top</a>) </p>

The way developers structure files of a given project used to be by having their style files and JavaScript files separate. This wasnt the best method, resulting in name collisions, dead code, and style scope issues. Over time two solutions came forth: CSS Modules and CSS-in-JS. There solutions aim to keep related JS code and its styles, together and scoped. Below are quick snippets about these solutions, please refer to their official documentation for usage.

**CSS Modules**
With the advent of frontend frameworks and module bundlers, developers can now modularize relevant code together by keeping styles and js in the same file.

```javascript
import "./my-component-name.css";
const MyComponent = () => {
  // component codes
};
export default MyComponent;
```

**CSS-in-JS**
This technique is often used by "CSS-in-JS" libraries such as: Emotion, stitches, and styled-components. Each library handles this a little different and have their own optimizations and tradeoffs, but generally speaking CSS-in-JS solutions are used immensely. Below is an examples of how to do this in styled-compoents.

```css
const Button = styled.a`
  /* This renders the buttons above... Edit me! */
  display: inline-block;
  border-radius: 3px;
  padding: 0.5rem 0;
  margin: 0.5rem 1rem;
  width: 11rem;
  background: transparent;
  color: white;
  border: 2px solid white;

  /* The GitHub button is a primary button
   * edit this to target it specifically! */
  ${props => props.primary && css`
    background: white;
    color: black;
  `}
`

render(
  <div>
    <Button
      href="https://github.com/styled-components/styled-components"
      target="_blank"
      rel="noopener"
      primary
    >
      GitHub
    </Button>

    <Button as={Link} href="/docs">
      Documentation
    </Button>
  </div>
)
```
