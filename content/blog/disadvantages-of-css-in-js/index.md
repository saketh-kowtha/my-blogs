---

id: 745353
title: Disadvantages of Css-in-Js ?
published_at: 2021-07-01T17:12:29.331Z
tag_list: javascript,css,react,beginners

---

<img src='https://res.cloudinary.com/practicaldev/image/fetch/s--liF9nkM1--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k6kb42s6pz04ei1f0heg.png' />
I am a big fan of `CSS-in-JS` especially `styled-components` but in this article i want to discuss about disadvantages of using CSS-in-JS.

- Difficulty to learn for the devs who are new to react syntax.
- The class names themselves are dynamically generated, too, essentially breaking caching as things can change between builds/renders.
- Css-in-js parses all the style definitions into plain vanilla CSS and put everything inside `style` tag in `index.html` file. This will increase html file size.
- Adds lots of unnecessary code while parsing to vanilla css.
- Browser will not start interpreting the styles until styled-components has parsed them and added them to the DOM, which slows down rendering.
- Most of the UI libraries and frameworks won't support this approach.
- We can't use other css utilities like SCSS, LESS and PostCSS.

<a href="https://www.buymeacoffee.com/sakethk" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
