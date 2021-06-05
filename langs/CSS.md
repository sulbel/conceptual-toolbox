# CSS

## Inline Styling
A technique where one places `style=""` inline with the HTML
  * This only applies to the single element that is styled

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

## Common properties

Property | Description
---------|-----------
color | change the color of an elements text
font-size | control the text font size
font-family | control the font used by an element

