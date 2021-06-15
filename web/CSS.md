# CSS

## Inline Styling
A technique where one places `style=""` inline with the HTML
  * This only applies to the single element that is styled
  * **Inline styles will override *both* class and id styling**

## Styling by selectors
A better approach is to use a `style` block at the top of your HTML codr
  * This will style **all** elements specified
```
<style>
  h2 {
      color: blue;
  }
</style>
```

## Classes
Reusable styles that can be added to HTML elements
  * Instead of specifying a selector for an HTML element, declare a class
  * Class names **begin with a .**
  * Apply classes to elements with the `class=""` tag. Note that the . is not needed inside the element class attribute
  * Classes allow you to use the same CSS styles on multiple HTML elements
  * If multiple classes are applied to an element, the class which is declared **last** in the stylesheet overrides classes which precede it

## `id` Attribute
Each HTML element can also have an `id` attribute
  * Can use `id` to style a **single** element
  * Can use the `id` element to select and modify specific elements with JavaScript
  * Best practice to keep `id` unique; do not give more than 1 element the same `id`
  * Like classes, can style an element based on `id`
    * However, **`id` takes precedence over `class`** -> if both are applied with conflicting styles, the `id` styling will be applied
    * `id` style is referenced with `#` instead of `.`

## Spacing
* All HTML elements can be thought of as 'little rectangles'
* 3 important properties control the space surrounding HMTL elements:
  * Padding - amount of space between the element's *content* and *border*
    * Padding controls the space **inside** the element
  * Margin - amount of space between elements *border* and surrounding elements
    * Margin controls the space **outside** the element

## Attribute selectors
Can also style based on attribute selectors, e.g. to style a form's checkbox: `[type="checkbox"] {...}`

## Variables
* Assign a CSS variable by: `--var-name: value`
* After assigning a variable, use it like so: `property: var(--var-name);`
* This allows one to change many properties in the style sheet by only changing one value
* Assign a fallback value in case the browser is unable to locate the variable, e.g. `background: var(--color-var, black);`
* Variables are usually defined in the `:root` element of the style sheet, so that all selectors may inherit from it 
  * Variables may be (locally) overwritten in specific classes, without changing the global value

## Pseudo Classes
A pseudo class is a keyword that can be used to select a specific state of an element
  * e.g. the a:hover{color: blue;} will change the color of an anchor link when the element is hovered


## Positioning Types
### Relative Positioning
* CSS treats each HTML element as its own box, usually referred to as the *CSS Box Model*
* Can specify an element to have `position: relative;`, allowing the item to be moved based off its relevative position
  * Pairs with offset properties `top` `bottom` `left` and `right`
    * The offset says how much distance to move the element **away** from the direction specified (i.e. `bottom: 25px;` moves the element 25 pixels *away* from the bottom, or 25 pixels up)
  * Other elements still 'think' the element is at the location specified in the HTML

### Absolute Positioning
* Locks an element in place, relative to its parent container
* Unlike relative positioning, removes the element from the normal flow of the HMTL document

### Fixed Positioning
* Elements with a fixed position do not move when the user scrolls the webpage (like a navbar)
* Like absolute positioning, removes the element from the normal flow of the HMTL document

### Centering a Div
* One way to center a div is to apply the `margin: auto;` property
* This also works for images.  Images are normally inline elements, but may be changed to block elements with the `display: block;` property

## Colors
### HSL
* Added in **CSS3**, HSL allows for specifying colors beyond names or hex codes
* HSL is useful when you have a base hue that you like, but need different variations of it
* `Hue` is the base color, based on a 360-degree color wheel
* `Saturation` is how much grey the hue has. A value of 0 is nearly full grey; a value of 100 is fully saturated with nearly no grey
* `Lightness` is how much white or black exists. A value of 100 is fully white; 0 is fully black

### Linear Gradient
* Create a background linear gradient with `background: linear-gradient();`
  * Arguments to `linear-gradient()`: direction gradient starts (90deg is horizontal), 2->n arguments specify the order of colors used
* Can also use the `repeating-linear-gradient()` to have the pattern repeat

## Transform
* The `transform` property allows scaling of elements
* An interesting use-case is with the `:hover` pseudo-class, to make elements scale when hovered

## Keyframes
* `@keyframes` can be used to add animation with CSS
* The 2 required properties to enable animation are `animation-name:` and `animation-duration:`
* Example showing how to animate a button on hover:
```
  button:hover {
    animation-name: background-color;
    animation-duration: 500ms;
  }

  @keyframes background-color {
    100% {
      background-color: #4791d0;a
    }
  }
```
* Infinite heart beat:
```
<style>
  .back {
    position: fixed;
    padding: 0;
    margin: 0;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: white;
    animation-name: backdiv;
    animation-duration: 1s;
    animation-iteration-count: infinite;
  }

  .heart {
    position: absolute;
    margin: auto;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: pink;
    height: 50px;
    width: 50px;
    transform: rotate(-45deg);
    animation-name: beat;
    animation-duration: 1s;
    animation-iteration-count: infinite;
  }
  .heart:after {
    background-color: pink;
    content: "";
    border-radius: 50%;
    position: absolute;
    width: 50px;
    height: 50px;
    top: 0px;
    left: 25px;
  }
  .heart:before {
    background-color: pink;
    content: "";
    border-radius: 50%;
    position: absolute;
    width: 50px;
    height: 50px;
    top: -25px;
    left: 0px;
  }

  @keyframes backdiv {
    50% {
      background: #ffe6f2;
    }
  }

  @keyframes beat {
    0% {
      transform: scale(1) rotate(-45deg);
    }
    50% {
      transform: scale(0.6) rotate(-45deg);
    }
  }

</style>
<div class="back"></div>
<div class="heart"></div>
```


## Common properties

Property | Description
---------|-----------
color | change the color of an elements text
font-size | control the text font size
font-family | control the font used by an element
width | control an elements width
border-color | color of a border
border-width | width of a border
border-style | style of a border; solid etc
border-radius | round the corners of a border
background-color | set the background color of an element
padding | distance between the content and border surrounding it
text-align | justify -> fill lines to edge; center; left; right
box-shadow | applies one or more shadows to an element
opacity | how opaque an item is; 1 is fully opaque, 0 is fully transparent
text-transform | adjusts text without changing the HTML
line-height | adjust the height of each line in a block of text
z-index | controls the layering of elements; higher values appear on top of lower valued elements
transform | change the size of an element

