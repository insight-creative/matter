<h1>Matter</h1>

A utility-first SCSS framework with substance.

Matter is a small utility-first SCSS framework for projects at Insight Creative, Inc. This is packed with classes like flex, pt-4, and text-center that can be composed to build any design, directly in your markup. Similar to frameworks like Tailwind, Bootstrap, and Tachyons but with only the utility classes that we actually use and need.

<h2>Utility-First Fundamentals</h2>

Building complex components from a set of utility classes. This SCSS framework leans on small, tersely named, single-purpose classes that are combined in the HTML to build up UIs. This approach can speed development time, reduce complexity, and increase consistency by limiting, and in some cases eliminating, the need to author new CSS.

The goal is to reduce decision-making friction, by having a set of pre-defined utility classes we can focus on higher-order problems while increasing quality and consistency for Insight Creative’s customers.

Table of contents
- [Design tokens](#design-tokens)
    - [Variables for visual consistency across platforms.](#variables-for-visual-consistency-across-platforms)
- [Breakpoints](#breakpoints)
  - [Implementing breakpoints](#implementing-breakpoints)
- [Colors](#colors)
  - [Accessibility](#accessibility)
    - [Text styling](#text-styling)
    - [Avoid using color exclusively](#avoid-using-color-exclusively)
- [Customizing your theme](#customizing-your-theme)
- [Scale and rhythm](#scale-and-rhythm)
- [Blocks](#blocks)
- [Wrappers](#wrappers)
- [Margin and padding](#margin-and-padding)
  - [Margin](#margin)
  - [Padding](#padding)
- [Typography](#typography)
  - [Headings sizes](#headings-sizes)
  - [How to use it:](#how-to-use-it)
  - [Body sizes](#body-sizes)
  - [How to use it:](#how-to-use-it-1)
- [Adding Custom Styles](#adding-custom-styles)

## Design tokens
#### Variables for visual consistency across platforms.

Design tokens power the visual building blocks of Matter. Values for colors, scale, and fonts, are stored in a simple format of SCSS variables that can then be used to create consistency throughout your project.

Because tokens are our “single source of truth”, changes are only made in one place. This way you don't need to update every instance of a color for example. Update that color variable once and watch it immediately take effect throughout your entire project.

Ex:

```
// Colors
$primary-color: #cd1f40;
$secondary-color: #92981b;
$tertiary-color: #8bc0c6;
$accent-color: #FDDF49;
$black: 1d1d1d;
$light-gray: #f6f6f6;
$white: #ffffff;
```

```
// Scale and rhythm based on a major third. A simple system to encourage visual rhythm.
$scale: 1.25;

$ic--200: 1rem / $scale / $scale;
$ic--100: 1rem / $scale;
$ic-100: 1rem;
$ic-200: 1rem * $scale;
$ic-300: 1rem * $scale * $scale;
```

## Breakpoints

| Size          | Breakpoint(em) | Breakpoint(px)  |
| ------------- |:--------------:| ---------------:|
| sm            | 37.5em         | 600px           |
| md            | 62em           | 992px           |
| lg            | 75em           | 1200px          |
| xl            | 112.5em        | 1800px          |

### Implementing breakpoints

```
.my-item {
    // styles for the "small" range at the root
    @include breakpoint(sm) {
        // styles above "small"
    }
    @include breakpoint(md) {
        // styles above "medium"
    }
    @include breakpoint(lg) {
        // styles above "large". These will be rare but they are here if needed
    }
    @include breakpoint(xl) {
        // styles above "extra large". These will be rare but they are here if needed
    }
}
```

## Colors

You will see in the Customizing your theme section below, colors are stored in SCSS variables. Use these as a base but add as many brand colors as you may need for your project.

```
// Colors
$primary-color: #cd1f40;
$secondary-color: #92981b;
$tertiary-color: #8bc0c6;
$accent-color: #FDDF49;
$black: 1d1d1d;
$light-gray: #f6f6f6;
$white: #ffffff;
```

You can then implement these colors throughout your project using these variables.

```
.my-item {
  color: $primary-color;
}
```

### Accessibility

Accessibility is important for everyone, and it should not forgotten in the design process. Accessible colors are vital for those with color blindness or other vision impairments. By using a high color contrast ratio, you can make sure that your design is accessible to as many people as possible.

#### Text styling

All text, including text in images and link text, should have enough contrast to stand out. This is especially important for links that aren’t underlined (and should apply to all states, including default, hover, and focus). See [WCAG 2.1 AA success criterion](https://www.w3.org/TR/WCAG21/#contrast-minimum) for contrast for the current requirements.

#### Avoid using color exclusively

Colors can also be used to convey information. For example, using red for error messages or green for success messages can help users understand your interface more quickly. Ultimately, accessible colors can help create a better experience for all users, regardless of their abilities.

However, color alone should not be used exclusively as an indicator for a user experience especially when an action or response from the user is required. To provide a more inclusive experience, additional information, such as supportive text, should be included.

For example, when expressing an error state on an input in a form, the input color should provide a visual indicator that the element needs attention. However, the color change should not be the sole indicator. The color change should be paired with supportive text that gives the user more information on how to recover from the error state.

## Customizing your theme

To customize Matter to meet the needs of your project, configure SCSS variables like your color palette, spacing and typography scale in variables.scss:

```
// Colors
$primary-color: #cd1f40;
$secondary-color: #92981b;
$tertiary-color: #8bc0c6;
$accent-color: #FDDF49;
$black: 1d1d1d;
$light-gray: #f6f6f6;
$white: #ffffff;
```

```
// Scale and rhythm based on a major third
$scale: 1.25;

$ic--200: 1rem / $scale / $scale;
$ic--100: 1rem / $scale;
$ic-100: 1rem;
$ic-200: 1rem * $scale;
$ic-300: 1rem * $scale * $scale;
```

## Scale and rhythm

A simple system to encourage visual rhythm.

Good spacing systems are based on simple mathematical principles with increments that are visually distinguishable. This toolkit gives designers and developers guidelines for effectively applying layout spacing, resulting in a more consistent application of space across our product.

Our scale is set through a $scale variable which then gets passed into a series of additional variables along with some simple math calculations.

```
// Scale and rhythm based on a major third
$scale: 1.25;

$ic--200: 1rem / $scale / $scale;
$ic--100: 1rem / $scale;
$ic-100: 1rem;
$ic-200: 1rem * $scale;
$ic-300: 1rem * $scale * $scale;
$ic-400: 1rem * $scale * $scale * $scale;
$ic-500: 1rem * $scale * $scale * $scale * $scale;
$ic-600: 1rem * $scale * $scale * $scale * $scale * $scale;
$ic-700: 1rem * $scale * $scale * $scale * $scale * $scale * $scale;
$ic-800: 1rem * $scale * $scale * $scale * $scale * $scale * $scale * $scale;
$ic-900: 1rem * $scale * $scale * $scale * $scale * $scale * $scale * $scale * $scale;
$ic-1000: 1rem * $scale * $scale * $scale * $scale * $scale * $scale * $scale * $scale * $scale;
```

## Blocks

Main sections on our websites, usualy content containers. Often also referred in other systems as .box .page-blocks .panel .info-box etc ...

Blocks are the building blocks of all core sections of a website. These blocks utilize our scale variables wrapped in a clamp() function to set a minimum value, a preferred value, and a maximum allowed value.

```
.block {
    padding: 5% 0;
    padding: clamp($ic-400, 10%, $ic-900) 0;
}
```

## Wrappers

Elements for wrapping general layout. Often also referred in other systems as .container .inner .outer .row etc ...

Wrappers are almost always paired with our blocks to wrap our content and ensure we constrain our layouts to some sort of maximum width.

```
.wrapper {
    width: 100%;
    max-width: 63rem;
    margin-inline: auto;
    padding-inline: $ic-300;
}
```

## Margin and padding

Margin and padding can be applied to elements using a variety of pre-defined utility class with margins and paddings set to match our rhythmic scale. All margin and padding classes follow the same naming convention.

| Name          | Output         |
| ------------- |:--------------:|
| mt            | margin-top     |
| mr            | margin-right   |
| mb            | margin-bottom  |
| ml            | margin-left    |

Margin and padding classes based on our rhythmic scale:

### Margin

```
.mt-1 {
  margin-top: $ic-100;
}

.mt-2 {
  margin-top: $ic-200;
}

.mt-3 {
  margin-top: $ic-300;
}

...

.mt-9 {
  margin-top: $ic-900;
}

.mt-10 {
  margin-top: $ic-1000;
}
```

### Padding

```
.pt-1 {
  padding-top: $ic-100;
}

.pt-2 {
  padding-top: $ic-200;
}

.pt-3 {
  padding-top: $ic-300;
}

...

.pt-9 {
  padding-top: $ic-900;
}

.pt-10 {
  padding-top: $ic-1000;
}
```

How to use:

```
<div class="block">
   <div>...</div>
   <div class="ml-6">...</div>
</div>
```

## Typography

A small number of text options based on our typography scale.

### Headings sizes

The typography scale classes are based on design rather than HTML tags, decoupling HTML semantics from the style. This allows developers to choose the correct tag which adds semantic value rather than selecting based on the styles associated with the tag.

Each heading level is defined with an associated class name. This way we can style an h3 like an h1 without using an <h1></h1> and break HTML semantics in our HTML markup.

### How to use it:

In most instances the heading utility classes can be used.

```
h1,
.h1 {
  font-size: clamp($ic-400, 4vw, $ic-700);
  max-width: 30ch;
}

<h3 class="h1">Example Heading</h3>
```

### Body sizes

Font size utility classes that are based on a typography scale

```
.fs-100 {
  font-size: $ic-100;
}

.fs-200 {
  font-size: $ic-200;
}

.fs-300 {
  font-size: $ic-300;
}

...

.fs-1000 {
  font-size: $ic-1000;
}
```

### How to use it:

```
<h3 class="h1">Example Heading</h3>

<p class="fs-300">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>

<p class="fs-100">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>

```

## Adding Custom Styles

Often the biggest challenge when working with a utility framework is figuring out what you’re supposed to do when there’s something you need that the framework doesn’t handle for you.

This is where the components folder comes into play. Use this folder to add all components that need custom styles for your project.