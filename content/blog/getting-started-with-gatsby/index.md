---

id: 728536
title: Getting started with gatsby
published_at: 2021-06-15T04:13:46.719Z
tag_list: gatsby,javascript,react,beginners

---

<img src='https://res.cloudinary.com/practicaldev/image/fetch/s--CTweNc1Y--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qsgvspnnnq6mw9zbt0v1.png' />

### Requirements

- Nodejs (download it from here https://nodejs.org/en/download/)

### Installing gatsby cli

```bash
npm i -g gatsby-cli
```

Before creating a site you should know about gatsby starters. Starters are nothing but boilerplates there are hundred's of boilerplates (starters) available from gatsby official site.

[Here you can choose Gatsby starter](https://www.gatsbyjs.com/starters/?)

### Creating new gatsby site from starter

```bash
gatsby new {name_of_your_site} {starter-repo-link}
```

Once `gatsby new` is successful then run the following commands

```bash
cd {name_of_your_site}
gatsby develop
```

Project structure will be like this

```
/
|-- /.cache
|-- /plugins
|-- /public
|-- /src
    |-- /pages
|-- /static
|-- gatsby-config.js
|-- gatsby-node.js
|-- gatsby-browser.js
```

Now you can check your site at [localhost:8000](http://localhost:8000)
