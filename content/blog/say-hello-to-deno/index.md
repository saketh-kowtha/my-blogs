---

id: 345016
title: Say hello to Deno
published_at: 2020-05-27T18:29:44.464Z
tag_list: deno,javascript,ecmascript,typescript

---

<img src='https://res.cloudinary.com/practicaldev/image/fetch/s--tyKfF7fB--/c_imagga_scale,f_auto,fl_progressive,h_420,q_auto,w_1000/https://dev-to-uploads.s3.amazonaws.com/i/5ys3jcxkps12s2l274ce.png' />
**Deno** is a Javascript runtime. Some devs will say that it is an alternative for **NodeJS** but it is not an alternative it is unique. 
**Ryan Dahl** the creator of **Nodejs** created this **Deno**.
##### NODE -> NO DE -> DE NO -> DENO
### Why Deno
* It is secure (It wont give direct access for files, environment and Network etc. User needs to give permissions to use)
* Supports Typescript
* Gives single executable file
* It had built-in utils like code formatter and inspector
* Uses V8 runtime 
* Built in rust
* No need **npm**
* *package.json* not required
* dependency manager not at all required
* Gives **Zero** dependency build

### Installation

`Linux/Unix/OS X :`

```bash
curl -fsSL https://deno.land/x/install/install.sh | sh
```

`Windows Powershell :`

```
iwr https://deno.land/x/install/install.ps1 -useb | iex
```

`Other ways :`

```zsh
#Using Brew(MAC OS)
brew install deno
#Using Chocolatey (Windows)
choco install deno
```

### Running First Deno program

```bash
deno run https://deno.land/std/examples/welcome.ts
```

### Hello World with colored text on console

create a file name it `helloworld.js`

```javascript
import clc from "https://deno.land/x/color/index.ts"
console.log(clc.red.text("Hello World"))
console.log(clc.blue.text("Hello World"))
```

Run the following commands to run your first Deno program

```bash
deno run helloworld.js
```
