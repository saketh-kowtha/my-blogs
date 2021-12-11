---
id: 754689
title: Building multiple themes with CSS..
description: This article is about building a site with multiple color schemes. It will change the theme without...
published_at: 2021-07-09T13:33:26.884Z
tag_list: html,css,beginners,webdev
---

This article is about building a site with multiple color schemes. It will change the theme without reloading the document, without adding theme class names dynamically and without duplicating the code.

I am using CSS variables in this example. You can try this even if you are using SASS or LESS.

In this example we will create a document that has background color, Dropdown (to pick scheme) , card, heading and paragraph. Here I am creating six color schemes and have given random names to them. Below are the names

- Light
- Dark
- Sunset
- Moon light
- Cartoon
- bluecrystal

In dropdown you will find the system option i.e., your OS theme. If your are using Dark mode in your OS, it will be Dark. Else, it will be `Light`.

For each scheme i defined four colors

- --main-bg-color (Body backgound color)
- --card-shadow-color (Card shadow)
- --primary-text-color (Heading text color)
- --secondry-text-color (Paragraph text color)

#### Important

- We are getting system theme with the help of `prefers-color-scheme` media query.
- I am using `data-theme` attribute to set color scheme. Whenever scheme changes just we need to update `data-theme` attribute value.

Here is the Codepen. You can find color schemes and some other styles for Card, Heading and Paragraph in CSS section.

{% codepen https://codepen.io/saketh-kowtha/pen/OJmXGXN %}
