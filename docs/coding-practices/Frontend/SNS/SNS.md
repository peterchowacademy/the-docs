---
title: SNS
layout: default
parent: Frontend 
grand_parent: Coding Practices
---

# SNS
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

# 1. CSS
## Flexbox

### From Youtube by Coding Startup - 1 - Basics
old ways: float, table (not invented for responsive pages)
modern ways: using Flexbox

You can play together on the [CSS Flexbox site](https://codepen.io/stevenlei/pen/YzKYEBZ)

```html
<div class="box A">A</div>
<div class="box B">B</div>
```
```css
.box {
    width:60px; /*set box weight and height*/
    height:60px; 
    background-color: #eee; /*set bg color as grey*/
    text-align:center; /*set content to center */
    line-height:60px; /*set content to fit box center */
    border-radius: 4px; /* Rounded edges for box */
    box-shadow: 0px 1px 3px rgba(0,0,0, .18); /*shadow*/
    font-size: 2em;

}
.A {background-color:#6DD9BF} /* color green*/
.B {background-color:#F26E50} /* color red*/
```

Basic concept: `<div>`'s default's display is a block
Default each block A and B are lined up in different columns 

There are two ways to design flex box:
1. flex-container
2. flex-items

To achieve flex-container do 2 things
1. Move all `<div>` into parent `<div class="flex-container">`
2. Add the .flex-container to css
3. Add a background color of #044BD9 (selected from Adobe Color)
Your final css and html should be like this

```html
<div class="flex-container">
    <div class="box A">A</div>
    <div class="box B">B</div>
</div>
```

```css

.flex-container{
    display: flex;
    background-color: #044BD9;
}
.box {
    width:60px; /*set box weight and height*/
    height:60px; 
    background-color: #eee; /*set bg color as grey*/
    text-align:center; /*set content to center */
    line-height:60px; /*set content to fit box center */
    border-radius: 4px; /* Rounded edges for box */
    box-shadow: 0px 1px 3px rgba(0,0,0, .18); /*shadow*/
    font-size: 2em;

}
.A {background-color:#6DD9BF} /* color green*/
.B {background-color:#F26E50} /* color red*/


```
Note: Your A and B are no longer lined up vertically
It's lining up horizontally now

{: .note }
The items / the divs inside the flex-container are now, flex-items


### From Youtube by Coding Startup - 2a - Flex-Container discussion