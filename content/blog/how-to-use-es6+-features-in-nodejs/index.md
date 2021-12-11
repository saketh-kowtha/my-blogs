---
id: 881397
title: How to use ES6+ features in nodejs
description: This article is about how to use es6+ in nodejs project Initialising project with...
published_at: 2021-10-29T17:06:49.650Z
tag_list: javascript,webdev,node,beginners
---

This article is about how to use `es6+` in nodejs project

#### Initialising project with npm

```bash
npm init -y
```

#### Installing babel plugins for es6+ features

```bash
npm i -D @babel/cli @babel/core @babel/plugin-proposal-class-properties @babel/plugin-transform-runtime @babel/preset-env
```

#### Adding babel support for project

```bash
touch .babelrc
```

Paste the following content in `.babelrc`

```javscript
{
    "presets": ["@babel/preset-env"],
    "plugins": ["@babel/plugin-proposal-class-properties", "@babel/transform-runtime"]
}

```

Babel is not a compiler or interpreter it is just a transpiler so we have to transpile `es6` to `es5` using babel then we have to execute that transpiled code. For that we can write npm script.

Add the following script to `package.json`

```bash
"build": "babel src -d dist",
"start": "npm run build && node dist"
```

Now create `src` folder and start writing `es6+` code inside that folder. Run `npm start` it will create `dist` folder inside that folder we can find transpiled code.

Cheers!!!
You can now extend your support by buying me a Coffee.

<a href="https://www.buymeacoffee.com/sakethk" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-blue.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
