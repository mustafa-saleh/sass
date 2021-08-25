# Sass

Sass stands for Syntactically Awesome Stylesheets, its a stylesheet language that's compiled to css. I allows you to use variables, nested rules, mixins, functions and much more with a fully Css-compatible syntax. Sass helps keep large stylesheets well-organized and makes it easier to share style with and accross projects.

## Sass has two file types

- .sass files: indented syntax, no semicolons and curly braces

```css
nav
  ul
    margin: 0
    list-style: none

  li
    display: inline-block

  a
    display: block
    padding: 6px 12px
```

- .scss: popular superset syntax, write regu;ar css and extend it with additiona features as needed

```css
nav {
  ul {
    margin: 0;
    list-style: none;
  }
  li {
    display: inline-block;
  }
  a {
    display: block;
    padding: 6px 12px;
  }
}
```

## Sass Variables

use $ to declare variables and reference them

```css
$red: hsl(0, 100%, 50%);

.button.danger {
  color: $red;
}
```

css also introduced its own native variables

```css
:root {
  --red: hsl(0, 100%, 50%);
}

.button.danger {
  color: var(--red);
}
```

## Sass Nesting

classes in css are often used as name spaces and duplicated over and over again

```css
.button a {
  font-weight: bold;
}

.button.danger {
  color: red;
}

.button.warning {
  color: yellow;
}
```

sass avoids duplication by nesting styles inside the parent

```css
.button {
 a {
  font-weight: bold;
 }

 .danger {
  color: red;
 }
```

## Sass & Selector

tells sass to combine parent selector with nested child selector (refer to parent selector)

```css
//scss
.btn {
  &: focus {

  }
}
//css
.btn: focus {

}
```

## Mixins

One more issue with css is that you'll find your self often including similar group of styles on multiple classes

```css
.card {
  display: flex;
  background: grey;
}

.aside {
  display: flex;
  background: grey;
}
```

Sass Mixins allow you to encapsulate a group of styles, then apply them anywhere in your code using include keyword

```css
@mixin flex-column {
  display: flex;
  background: grey;
}
.card {
  @include flex-column;
}

.aside {
  @include flex-column;
}
```

mixins can also take arguments to create a number of similar classes programmatically

```css
@mixin flex-column($color, $bg) {
  display: flex;
  color: $color;
  background: $bg;
}
.card {
  @include flex-column(black, white);
}
```

## Sass Functions

Sass alos provies a set of tools to help you write programmetic code such as if statement for conditional logic

```css
@mixin theme-color($theme) {
  @if $theme == "light" {
    background: $light-bg;
  } @else {
    background: $dark-bg;
  }
}
```

you can also create an array of values with a variable and loop over them with each

```css
$sizes: 10px, 20px, 50px;

@each $size in $sizes {
  .icon-#{$size} {
    font-size: $size;
  }
}
```

you can also extract any logic to a reusable function

```css
@function sum($numbers) {
  $sum: 0;
  @each $number in $numbers {
    $sun: $sum + $number;
  }
  @return $sum;
}
```

Sass has built-in functions, if you need to adjust a color, use lighten or darken functions to adjust a color by a predictable value

```css
$base-color: green;

.card {
  background: lighten($base-color, 25%);
  color: darken($base-color, 25%);
}
```

When finished, the compiler will convert your code to a valid css that can run on the browser
