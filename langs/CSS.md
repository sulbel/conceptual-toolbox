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


