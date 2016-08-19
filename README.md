# Frontend
Frontend Development

In order to learn frontend development one just has to start!

# References
- [Frontend Development](http://weaintplastic.github.io/web-development-field-guide/Development/Frontend_Development/)
- [Nodejs](https://nodejs.org/)
- [Bower](https://bower.io/)

# Prerequisits
Building and managing frontend applications is complicated because there are a lot of resources involved. The tooling used to do this consists of
- Nodejs
- Bower
- Gulp

## Nodejs
See [Nodejs](https://nodejs.org/en/) for a description howto install nodejs on the environment.

## Bower
Bower is used to manage dependencies between all packages used in the project. Install bower, using an account with sufficient privileges. 

```
[root@pluto ~]# npm install -g bower
/usr/bin/bower -> /usr/lib/node_modules/bower/bin/bower
/usr/lib
└── bower@1.7.9 

```

## Gulp
Gulp is used to automate the build workflow for this project. Install gulp, using an account with sufficient privileges.

```
[root@pluto ~]# npm install --global gulp
```

# Project structure
The default structure of the project will be
```
    project
    |
    |-- source
    |
    |-- templates
    |       |
    |       |-- dist
    |       |
    |       `-- src
    |
    |-- bower.js
    |-- gulpfile.js
    |-- package.json
    `-- README.md
```
- **source** holds the source files. This is the project's webroot containing all files that the project needs to be able to run. Usually this is where your server side system like a CMS or Web App is installed.
- **templates** The templates folder is where you basically will work as a Frontend Developer. It contains just static files without any dependencies on a feature rich server side system like a Content Management System or Web Application Framework. Your templates folder is subdivided into two main folders: src and dist.
    - src folder holds all your frontend development files like LESS/SASS files, your structured Javascript, Fonts and Images and HTML and HTML partials
    - dist contains your compiled and minified CSS, your optimized Javascript and Images, your Fonts and your compiled HTML files.
- **bower.js** is the configuration file for your frontend dependencies managed with Bower
- **gulpfile.js** is the description file for your build task runner based on Gulp
- **package.json** is the dependency description file for NodeJS packages
  

Create the directories

```
[bvpelt@pluto frontend]$ mkdir -p source templates/dist templates/src 
[bvpelt@pluto frontend]$
```

# Initializing a project
## npm init
To initialize a project use npm

```
[bvpelt@pluto frontend]$  npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg> --save` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
name: (frontend) 
version: (1.0.0) 
description: Learning frontend development
entry point: (index.js) 
test command: 
git repository: (https://github.com/bvpelt/frontend.git) 
keywords: learning frontend development
author: Bart van Pelt (bart.vanpelt@gmail.com)
license: (ISC) MIT
About to write to /home/bvpelt/Develop/frontend/package.json:

{
  "name": "frontend",
  "version": "1.0.0",
  "description": "Learning frontend development",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/bvpelt/frontend.git"
  },
  "keywords": [
    "learning",
    "frontend",
    "development"
  ],
  "author": "Bart van Pelt (bart.vanpelt@gmail.com)",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/bvpelt/frontend/issues"
  },
  "homepage": "https://github.com/bvpelt/frontend#readme"
}


Is this ok? (yes) 
[bvpelt@pluto frontend]$ 
```

## bower init
To initialize a new project start use `bower init`

```
[bvpelt@pluto frontend]$ bower init
? name frontend
? description Learning frontend development
? main file index.html
? keywords learning frontend development
? authors Bart van Pelt <bart.vanpelt@gmail.com>
? license MIT
? homepage https://github.com/bvpelt/frontend
? set currently installed components as dependencies? Yes
? add commonly ignored files to ignore list? Yes
? would you like to mark this package as private which prevents it from being accidentally published to the registry? Yes

{
  name: 'frontend',
  homepage: 'https://github.com/bvpelt/frontend',
  authors: [
    'Bart van Pelt <bart.vanpelt@gmail.com>'
  ],
  description: 'Learning frontend development',
  main: 'index.html',
  keywords: [
    'learning',
    'frontend',
    'development'
  ],
  license: 'MIT',
  private: true,
  ignore: [
    '**/.*',
    'node_modules',
    'bower_components',
    'test',
    'tests'
  ]
}

? Looks good? Yes
[bvpelt@pluto frontend]$ 
```

# Adding a javascript package
To add a javascript package use: `$ bower install <package> --save`
This adds dependencies to bower.json. The installed packages are saved in your projects root folder named bower_components. 
The complete package is copied in the bower_components directory. Usually you only use need a subset of all the copied files. Make sure the files you
need can be found by your build system.

To find the angular package use `$ bower search angular`. It shows a list of packages starting with angular, only angularjs is needed.

In the frontend I will use angularjs

```
[bvpelt@pluto frontend]$ bower install angularjs --save
bower cached        https://github.com/angular/bower-angular.git#1.5.5
bower validate      1.5.5 against https://github.com/angular/bower-angular.git#*
bower new           version for https://github.com/angular/bower-angular.git#*
bower resolve       https://github.com/angular/bower-angular.git#*
bower checkout      angularjs#v1.5.8
bower resolved      https://github.com/angular/bower-angular.git#1.5.8
bower install       angular#1.5.8

angular#1.5.8 bower_components/angular
[bvpelt@pluto frontend]$ 
```

# Setup build system

```
[bvpelt@pluto frontend]$ npm install gulp --save
npm WARN deprecated minimatch@2.0.10: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
npm WARN deprecated minimatch@0.2.14: Please update to minimatch 3.0.2 or higher to avoid a RegExp DoS issue
npm WARN deprecated lodash@1.0.2: lodash@<3.0.0 is no longer maintained. Upgrade to lodash@^4.0.0.
npm WARN deprecated graceful-fs@1.2.3: graceful-fs v3.0.0 and before will fail on node releases >= v7.0. Please update to graceful-fs@^4.0.0 as soon as possible. Use 'npm ls graceful-fs' to find it in the tree.
[3141673]   WARN - pl.local.NativeFileWatcherImpl - Watcher terminated with exit code 3 e_modul
frontend@1.0.0 /home/bvpelt/Develop/frontend
... 
[bvpelt@pluto frontend]$
```