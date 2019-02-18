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