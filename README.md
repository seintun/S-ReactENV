# S-ReactENV

### Sein's React Environment Boilerplate

## Author: Sein Tun

## GitHub: https://github.com/seintun

## LinkedIn: https://www.linkedin.com/in/seintun

> S-ReactENV is a reference guide to build a boilerplate of minimalistic React Environment from scratch by using generic React, React-DOM, Webpack 4 and Babel.

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

react-boilerplate
|--- src
|--- |--- components
|--- |--- styles

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
| :------: | ------ |
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

### Configurations

### Webpack

We need to define the entry and output directory of our app inside the webpack.config.js so that Webpack can bundle our JavaScript files into index.bundle.js file inside the /dist directory.

```sh
$ touch webpack.config.js
```

Add this following code inside your webpack.config.js

##### webpack.config.js

```
const path = require("path");
module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.join(__dirname, "/dist"),
    filename: "index_bundle.js"
  }
};
```

### Webpack Loaders

Now add some loaders inside this file, which will be responsible for loading and bundling the source files.
Inside the webpack.config.js, add following lines of code:

##### webpack.config.js

```
const path = require("path");

module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.join(__dirname, "/dist"),
    filename: "index-bundle.js"
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: ["babel-loader"]
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"]
      }
    ]
  }
};
```

Here babel-loader is used to load our JSX/JavaScript files and css-loader is used to load and bundle all of the CSS files into one file and style-loader will add all of the styles inside the style tag of the document.

Before Webpack can use css-loader and style-loader we have to install them as a dev-dependency.

```sh
$ npm install css-loader style-loader --save-dev
```

> Keep in mind that webpack executes the loaders from last to first i.e from right to left.

### Babel

Now, let's create configurations for Babel so that we can transpile ES6 and JSX into ES5

```sh
$ echo '{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}' >> .babelrc
```

> env: This preset is used to transpile the ES6/ES7/ES8 code to ES5.
> react: This preset is used to transpile JSX code to ES5.

---

### Compiling files using Webpack

I know we have been creating directories, files, and adding configurations. Let's compile to test it out!
Add the following code inside the script object of the package.json file:

##### package.json file

```
"start": "webpack --mode development --watch",
"build": "webpack --mode production"
```

> --watch flag: Webpack to compile automatically whenever there is a change in files.
> --mode flag: Webpack 4 has two modes: production and development, allowing us to choose which mode to use

Moment of truth~

```sh
$ npm start
```

So, what just happened? Webpack just compiled and create a new folder called dist with index-bundle.js containing transpiled ES5 code from index.js, where a lot of heavy-lifting are done for you after npm start is runnning. All right, let's terminate the npm start with Ctrl+C for now.

---

### Creating the first React component, App.js and App.css

Let's start building the React component, where most actions will happen in the future.

```
$ touch src/components/App.js src/styles/App.css
```

Add the following code inside App.js and App.css respectively.

##### App.js

```
import React, { Component } from "react";
import '../styles/App.css';

class App extends Component {
    render() {
        return (
            <div>
                <h1>My S-ReactENV React App!</h1>
            </div>
        );
    }
}

export default App;
```

##### App.css

```
h1 {
    color: #27aedb;
    text-align: center;
}
```

Finally, let's import App.js inside the entry point Index.js and render on the HTML's DOM with the following code:

##### Index.js

```
import React from "react";
import ReactDOM from "react-dom";
import App from "./components/App.js";

ReactDOM.render(<App />, document.getElementById("root"));
```

It's not yet ready for rendering yet! We need to install html-webpack-plugin that will generate HTML file for us. This plugin injects the script inside the HTML file and writes to dist/index.html after compliling.

```sh
$ npm install html-webpack-plugin --save-dev
```

Update webpack.config.js file by importing html-webpack-plugin as follow:

##### webpack.config.js

```sh
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.join(__dirname, "/dist"),
    filename: "index-bundle.js"
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: ["babel-loader"]
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"]
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/index.html"
    })
  ]
};
```

```sh
$ npm start
```

You will see an index.html file will be created inside dist folder, which you will click to open and see the webpage with the text "My S-ReactENV React App!".

But this approach has a downside that you have to manually refresh the webpage, in order to see the changes you have made. To have webpack watch our changes and refresh webpage whenever any change is made to our components, we can install webpack-dev-server.

---

### Instaling Webpack-dev-server

```sh
$ npm install webpack-dev-server --save-dev
```

Update the package.json file to use webpack-dev-server

##### package.json

```
"start": "webpack-dev-server --mode development --open --hot",
```

> added two flags --open and --hot which opens and refreshes the web page whenever any change is made to components.

##### What's now?

We can do npm start at this point but, let's customize our port since webpack-dev-server comes with default port 8080.

Add the following code of "devServer object with port 3000" inside the webpack.config.js file:

##### webpack.config.js

```
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");

module.exports = {
  entry: "./src/index.js",
  output: {
    path: path.join(__dirname, "/dist"),
    filename: "index-bundle.js"
  },
  devServer: {
    port: 3000
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: ["babel-loader"]
      },
      {
        test: /\.css$/,
        use: ["style-loader", "css-loader"]
      }
    ]
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "./src/index.html"
    })
  ]
};
```

### Let's go!

```sh
$ npm start
```

You should see the browser window pops up and displays the content with localhost:3000.

# Your React Boilerplate from scratch is ready to rock!
