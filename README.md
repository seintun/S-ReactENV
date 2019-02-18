# S-ReactENV

### Sein's React Environment Boilerplate

S-ReactENV is a reference guide to build a boilerplate of minimalistic React Environment from scratch by using generic React, React-DOM, Webpack 4 and Babel.

## Pre-requisites

We require npm and node pre-installed on our machine before we dive into the project. If you already have npm and node pre-installed before, you can skip to Getting Started.

```sh
$ brew install node
$ npm install npm@latest -g
```

Run the following code, if npm is asking permission/ownership

```sh
$ sudo chown -R $USER:$GROUP ~/.npm
$ sudo chown -R $USER:$GROUP ~/.config
```

### Getting Started

Open your terminal and create a new folder with any name you want. I will name the folder as "react-boilerplate".

```sh
$ mkdir react-boilerplate
$ cd react-boilerplate
```

Let's create a base folder structure for our React files and components.

> react-boilerplate
> |--- src
> |--- |--- components
> |--- |--- styles

```sh
$ mkdir -p src/components src/styles
```

### Initialize the Project

All projects that uses node package manager (npm) must be initialized. Using the following command will create package.json file and adding -y flag at the end will use default iniitalization.

```sh
$ npm init -y
```

The package.json file should looks like as follow:

##### package.json

```
{
  "name": "react-boilerplate",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```

### Installing dependency packages

We will be primarily using Webpack, Babel, React and React-DOM for this guide.
| packages | Functionality |
| ------ | ------ |
| React | To definte and create elements, lifecycle hooks, etc. |
| React-DOM | The glue between React and the DOM, giving access to DOM element |
| Webpack | A static module bundler for modern JavaScript applications that bundle the project files into a single file for production |
| Babel | Since React primarily uses ES6 & JSX, we need Babel to transpile them into to ES5. |

### Installing Webpack

```sh
$ npm install webpack webpack-cli --save-dev
```

> webpack-cli allows us to use webpack in the command line

### Installing React

```sh
$ npm install react react-dom --save
```

### Installing Babel

```sh
$ npm install @babel/core babel-loader @babel/preset-env @babel/preset-react --save-dev
```

> babel-core: Transforms ES6 code to ES5
> babel-loader: Webpack helper to transpile code, given the the preset.
> babel-preset-env: Preset which helps babel to convert ES6, ES7 and ES8 code to ES5.
> babel-preset-react: Preset which Transforms JSX to JavaScript.

---

### Are you still with me?

Great! We are all set with installing most of the required dependency packages, let's create some files for entry point.
We will create an Index.js and Index.html file inside the root of /src folder

```sh
$ touch src/Index.js src/Index.html
```

Add the following code by Copy/Paste or using shortcut "!" but make sure you include <div> tag with id of "root".

##### Index.html

```
<!DOCTYPE html>

<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>React Boilerplate</title>
</head>

<body>
    <div id="root">
    </div>
</body>
</html>
```
