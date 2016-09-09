# Frontend
Frontend Development

In order to learn frontend development one just has to start!

# References
- [Frontend Development](http://weaintplastic.github.io/web-development-field-guide/Development/Frontend_Development/)
- [Nodejs](https://nodejs.org/)
- [Nodejs documentation](https://docs.npmjs.com/)
- [Bower](https://bower.io/)
- [npm-check](https://www.npmjs.com/package/npm-check)
- [openlayers angularjs integration](https://medium.com/angularjs-meetup-south-london/angular-integration-with-openlayers-3-5a6e8d29e635#.rfzdxklmy) 
- [pdok](https://media.readthedocs.org/pdf/pdok-ngr/latest/pdok-ngr.pdf)
- [pdok en tms](http://pdok-ngr.readthedocs.io/publiceren.html#openlayers-3)
- [pdok wmts example](https://gist.github.com/RaymondKroon/60f74ae45b2b67b79c45) 
- [projection viewer](http://gis.ibbeck.de/ginfo/apps/OLExamples/ol311/MapProjectionViewer/projectionViewer.asp) 

# Prerequisits
Building and managing frontend applications is complicated because there are a lot of resources involved. The tooling used to do this consists of
- Nodejs
- Bower
- Gulp

## Nodejs
See [Nodejs](https://nodejs.org/en/) for a description howto install nodejs on the environment.

## Bower
Bower is used to manage dependencies between all packages used in the project. Install bower, using an account with sufficient privileges. This only has to be done once to setup the developer environment on a specific system. Once bower is installed globally every user can use it.

```
[root@pluto ~]# npm install -g bower
/usr/bin/bower -> /usr/lib/node_modules/bower/bin/bower
/usr/lib
└── bower@1.7.9 

```

## Gulp
Gulp is used to automate the build workflow for this project. Install gulp, using an account with sufficient privileges. This only has to be done once to setup the developer environment on a specific system. Once gulp is installed globally every user can use it.

```
[root@pluto ~]# npm install --global gulp
```

# Project structure
The default structure of the project will be
```   
    project
    ├-- bower.json
    ├-- gulpfile.js
    ├-- LICENSE
    ├-- package.json
    ├-- README.md
    ├-- source
    `-- templates
        ├-- dist
        |   `-- assets
        |       ├-- css
        |       ├-- fonts
        |       ├-- img
        |       `-- js
        `-- src
            `-- assets
                ├-- fonts
                ├-- img
                ├-- js
                `-- sass
    
```


- **bower.json** is the configuration file for your frontend dependencies managed with Bower
- **gulpfile.js** is the description file for your build task runner based on Gulp
- **LICENSE** the licence file for this application
- **package.json** is the dependency description file for NodeJS packages
- **README.md** this file
- **source** holds the source files. This is the project's webroot containing all files that the project needs to be able to run. Usually this is where your server side system like a CMS or Web App is installed.
- **templates** The templates folder is where you basically will work as a Frontend Developer. It contains just static files without any dependencies on a feature rich server side system like a Content Management System or Web Application Framework. Your templates folder is subdivided into two main folders: src and dist.
    - src folder holds all your frontend development files like LESS/SASS files, your structured Javascript, Fonts and Images and HTML and HTML partials
    - dist contains your compiled and minified CSS, your optimized Javascript and Images, your Fonts and your compiled HTML files.


  

## Create the directories

```
[bvpelt@pluto frontend]$ mkdir -p templates/src/assets/{fonts,img,js,sass}
[bvpelt@pluto ngviewer]$ mkdir -p templates/dist/assets/{css,fonts,img,js}
[bvpelt@pluto frontend]$ cat > LICENSE << EOF
MIT License

Copyright (c) 2016 Bart van Pelt

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
EOF
[bvpelt@pluto frontend]$ cat > README.md <<EOF
# Readme
...
EOF
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
## Gulp
Gulp is used to automate the building proces.

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

To fix there errors (specific for my environment) I used

```
[root@pluto ~]# npm update -g minimatch@3.0.2
[root@pluto ~]# npm update -g lodash@4.0.0
[root@pluto ~]# npm update -g gracefull-fs@4.0.0
```

## Add gulp dependencies
```
[bvpelt@pluto frontend]$ npm install gulp --save
```

The gulpfile.js is your task descriptor. It tells gulp which tasks it should perform on which files. This descriptor has to be created by hand. So go to your project root folder and create a file called gulpfile.js.
 
```
[bvpelt@pluto frontend]$ touch gulpfile.js
[bvpelt@pluto frontend]$
```

Gulp itself can't do much for you. For all the hard work it needs the help of gulp plugins which cover the scope of a certain task you want to do. The functionality of plugins in combination will give you endless possibilities to setup the build script of your dreams. A full list of gulp plugins can be found [here](http://gulpjs.com/plugins/)

A prerequisit is node-gyp which must be installed global

```
[root@pluto ~]# npm install -g node-gyp
```

Create a buildscript

This buildscript usually serves as the initial setup when building a new build task for a new project. It is performing a lot of different tasks.

- watches any source files for changes and executes the build process
- compiles scss to css and injects vendor css (using gulp-inclue), auto prefixes the css and minfies it for prodction
- concatinates and minifies js and generates sourcemaps
- minifies images
- concatinates html and php files (using gulp-inclue)
- simply copy font files (this would be the perfect place to gzip your fonts)
- notfies you with system dialogs whenever an error happens
- sets up live-reload to work with the Chrome Livereload Extension


```javascript
var gulp               = require('gulp');             
var fs                 = require('fs');
var es                 = require('event-stream');
var path               = require('path');
var uglify             = require('gulp-uglify'); 
var sass               = require('gulp-sass');
var cssmin             = require('gulp-minify-css');
var rename             = require('gulp-rename'); 
var autoprefixer       = require('gulp-autoprefixer');
var include            = require('gulp-include');
var notify             = require("gulp-notify");
var imagemin           = require("gulp-imagemin"); 
var livereload         = require('gulp-livereload');
var sourcemaps         = require('gulp-sourcemaps');

var srcPath            = 'templates/src/';            // Path to the source files
var distPath           = 'templates/dist/';            // Path to the distribution files

// Paths that gulp should watch
var watchPaths        = {
    scripts:     [
        srcPath+'assets/js/*.js',
        srcPath+'assets/js/**/*.js'
    ],
    images:     [
        srcPath+'assets/img/**'
    ],
    sass:         [
        srcPath+'assets/sass/*.scss',
        srcPath+'assets/sass/**/*.scss'
    ],
    fonts:      [
        srcPath+'assets/fonts/**'
    ],
    html:          [
        srcPath+'**/*.html',
        srcPath+'**/*.php'
    ]
};

// Task for sass files
gulp.task('sass', function () {
    gulp
        .src(srcPath + 'assets/sass/styles.scss')
        .pipe(include())
        .pipe(sass())
        .on("error", notify.onError({ message: "Error: <%= error.message %>", title: "Error running sass task" }))
        .pipe(autoprefixer({ browsers: ['> 1%', 'last 2 versions'], cascade: false }))
        .on("error", notify.onError({ message: "Error: <%= error.message %>", title: "Error running sass task" }))
        .pipe(cssmin({ keepBreaks: false }))
        .on("error", notify.onError({ message: "Error: <%= error.message %>", title: "Error running sass task" }))
        .pipe(rename({ suffix: '.min' }))
        .pipe(gulp.dest(distPath + 'assets/css'));
});

// Javscript task
gulp.task('scripts', function(){
    gulp
        .src(srcPath + 'assets/js/*.js')
        .pipe(include())
        .pipe(sourcemaps.init())
        .pipe(uglify())
        .on("error", notify.onError({ message: "Error: <%= error.message %>", title: "Error running scripts task" }))
        .pipe(rename({ suffix: '.min' }))
        .pipe(sourcemaps.write('maps'))
        .pipe(gulp.dest(distPath + 'assets/js'));
});

// Font task
gulp.task('fonts', function () {
    gulp
        .src([srcPath + 'assets/fonts/**'])
        .pipe(gulp.dest(distPath + 'assets/fonts'));
});

// HTML task
gulp.task('html', function () {
    gulp
        .src([srcPath + '*.html'])
        .pipe(include())
        .on("error", notify.onError({ message: "Error: <%= error.message %>", title: "Error running html task" }))
        .pipe(gulp.dest(distPath));
});

// Images task
gulp.task('images', function () {
    gulp
        .src(srcPath + 'assets/img/**')
        .pipe(imagemin())
        .on("error", notify.onError({ message: "Error: <%= error.message %>", title: "Error running image task" }))
        .pipe(gulp.dest(distPath + 'assets/img'));
});

// Watch task
gulp.task('watch', function() {
    gulp.watch(watchPaths.scripts, ['scripts']);
    gulp.watch(watchPaths.images, ['images']);
    gulp.watch(watchPaths.sass, ['sass']);
    gulp.watch(watchPaths.html, ['html']);
    gulp.watch(watchPaths.fonts, ['fonts']);

    livereload.listen();
    gulp.watch(distPath + '**').on('change', livereload.changed);
});

// Default task
gulp.task('default', ['scripts', 'images', 'sass', 'fonts', 'html', 'watch']);
```

This gulp description will perform the default task upon execution of gulp in your command line. It will immediatley execute the sass task but also another important one – the watch task. This is a special kind of task that will watch changes to files in the given locations and executes the correspondent tasks. By setting up this task we can ensure, that our scssfile will be compiled everytime we modify it.
[Automatic deployement](http://mikeeverhart.net/2016/01/deploy-code-to-remote-servers-with-gulp-js/) 
Install gulp plugins:

```
[bvpelt@pluto frontend]$ npm install event-stream --save
[bvpelt@pluto frontend]$ npm install gulp-uglify --save
[bvpelt@pluto frontend]$ npm install gulp-minify-css --save
[bvpelt@pluto frontend]$ npm install gulp-sass --save
[bvpelt@pluto frontend]$ npm install gulp-less --save
[bvpelt@pluto frontend]$ npm install gulp-rename --save
[bvpelt@pluto frontend]$ npm install gulp-autoprefixer --save
[bvpelt@pluto frontend]$ npm install gulp-include --save
[bvpelt@pluto frontend]$ npm install gulp-notify --save
[bvpelt@pluto frontend]$ npm install gulp-imagemin --save
[bvpelt@pluto frontend]$ npm install gulp-livereload --save
[bvpelt@pluto frontend]$ npm install gulp-sourcemaps --save
```

[upgrade nodejs on fedora](http://tecadmin.net/upgrade-nodejs-via-npm/#)

```
[bvpelt@pluto frontend]$ bower install OpenLayers --save
```
