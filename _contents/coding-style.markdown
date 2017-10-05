---
layout: content
title:  "Coding Style"
permalink: /contents/coding-style
---

**You should:**

- Use soft-tabs with a two space indent
- Put spaces before `{` in rule declarations (right: `.foo {}`; wrong: `.foo{}`)
- Use `//` for comment blocks (instead of `/* */`)

**Would be nice if you:**

- Avoid using `margin-bottom` and prefer the use of only `margin-top`. With all your elements having margin only above them it is easier to organize the overall structure.

## Order of property declarations

In order for us to have a standard way of writing CSS we should always try to declare the properties in a specific order. This is not a "frozen" thing, and it is flexible, but the main guideline here is to group some properties together and have these blocks in a specific order.

The declarations groups are the following (and should follow this order):

`text` properties (i.e.: `text-transform`, `text-decoration`, etc.)
and `border`

0. **Variable declarations**: you may use local variables inside your main selector. Don't worry, they won't bleed to other components/pages. Each selector creates a scope.

0. **Selector extensions**: these should be the first instructions to be declared. It is not a property, and it should be declared before so it can be overridden by properties declared below it.

0. **Typography**: properties such as the `font` properties (i.e.: `font-size`, `font-family`, etc.) and `line-height`.

0. **Positioning properties**: properties with the function of positioning elements such as `position`, `top`, `right`, `bottom`, and `left`.

0. **Content flow properties**: properties that regulate flow of content, such as `overflow`, `float`, `display` and all `flex`-related properties.

0. **Box model properties**: the CSS box model is essentially a box that wraps around every HTML element. These are `width`, `height`, `padding` and `margin`.

0. **Table/List model properties**: some properties are relevant if you are building a list or table, these are `list-style`-related properties, `table-layout` and some other unused properties.

0. **Aesthetic/cosmetic/animation properties**: `transition`, `transform`, `animation` properties, text decoration properties, like `text-decoration`, `text-align`, `line-height`, `letter-spacing` and more.

0. **Other**: properties that change the elements visual aspects without changing its size or positioning, such as `background`, `color`, `box-shadow`, `opacity`, `cursor`, `border` etc.

0. **Mixins' includes**: these should be the last instructions to be declared. They're usually something that overrides the default style of your component, like responsive mixins.

These groups should be separated by a blank line.


**Example**

```scss
.button {
  @include btn;

  width: 240px;
  margin-top: 2rem;
  margin-bottom: 4rem;

  position: absolute;
  top: 8rem;

  font-size: $font-size-body;
  text-transform: uppercase;
  text-decoration: underline;

  color: $color-highlight;
  background-color: $color-dark;
  opacity: 0.6;
  box-shadow: 0 2px 4px rgba(#000, 0.2);

  transition: opacity 0.2s ease-in;
}
```

Another relevant pattern to be followed is declaring abscissa properties before ordinate properties if both exists. For example, `transformX` should come before `transformY`; and `width` should come before `height`.

Properties should also be spread when possible to avoid conflicts of overriding when not wanted.

**Avoid**

```scss
.bg {
  background: fixed $color-main url(../assets/bg.png) center top no-repeat;
}
```

**Prefer**

```scss
.bg {
  background-attachment: fixed;
  background-color: $color-main;
  background-image: url(../assets/bg.png);
  background-position: center top;
  background-repeat: no-repeat;
}
```

### Tools
There are tools that help the process of organization. They help a lot by improving the overall productivity and make you focus on writing code instead of losing time organizing it.

Here on Flama we use [CSScomb](http://csscomb.com/) with a settings file that keep the code organized, standardized and clean.

For those of you that use [Atom](https://atom.io/), it has a package called [atom-csscomb](https://atom.io/packages/atom-csscomb) that runs it on a keystroke. In order to keep the team always in sync, we use the same [config file](https://github.com/flama/flama_front/blob/develop/.csscomb.json).

Enjoy! :3

<div style="width:100%;height:0;padding-bottom:92%;position:relative;"><iframe src="https://giphy.com/embed/12NUbkX6p4xOO4" width="50%" height="50%" style="position:absolute" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div><p><a href="https://giphy.com/gifs/shia-labeouf-12NUbkX6p4xOO4">via GIPHY</a></p>
