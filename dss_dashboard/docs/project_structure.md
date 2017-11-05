# Project Codebase Organization and Structure

## General Codebase

_Dev Notes_

- Need to move bin/, routes/ and views/ into src/.
- Need to integrate babel for ecma7/8 usage.
- JavaScript needs to transpile, minify and obfuscate into dist/ target dir.

```
.
├── app.js
├── bin                                 // any executable scripts/compiled binaries used with/built from src.
│   └── www(.js)
├── build                               // any scripts or tooling needed to build.
│   ├── tasks                           // a directory for separating tasks.
│   └── *                               // various build scripts.
├── dist                                // production ready code and compiled modules ready to use in systems.
│   ├── scripts
│   │    └── *.js                       // transpiled to ecma6.
│   └── stylesheets
│       └── style.css                   // transpiled to css3.
├── docs                                // all markdown/generated docs for the project.
│   └── * project_docs.md
├── node_modules                        // vendor dependencies, .gitignored.
│   └── * vendor_modules/
├── package.json                        // project dependencies.
├── public                              // Optimized, web ready resources.
│   ├── data                            // data sources.
│   │    └── *.csv,json,tsv,xml
│   ├── gis                             // geospatial data sources.
│   │    └── *.shp,geojson,topojson
│   ├── images                          // web optimized images for production.
│   │    └── *.jpg/png/gif/tiff
├── routes
│   ├── index.js
│   └── users.js
├── src                                 //  code that needs to be manipulated before it can be used.
│   ├── scss
│   │   ├── modules
│   │   │    └── *.scss
│   │   ├── partials
│   │   │    └── *.scss
│   │   ├── vendor
│   │   │    └── *.scss
│   │   └── style.scss
│   ├── js
│   │   ├── es6
│   │   │    └── *.js
│   │   ├── es7
│   │   │    └── *.js
│   │   ├── ts
│   │   │    └── *.ts
│   │   └── coffee
│   │        └── *.coffee
│   └── assets                          // raw uprocessed/optimized project assets.
│       ├── img
│       │    └── *.jpg/png/gif/tiff
│       ├── mov
│       │    └── *.scss
│       └── ico
│            └── *.scss
├── test                                // all the project/module's test scripts.
│   └── envs                            // any environment that's needed for testing.
│   │    └── *
│   └── integration                     // sub-directory for integration tests.
│   │    └── *
│   └── unit                            // sub-directory for unit tests.
│        └── *
└── views
    ├── error.pug
    ├── index.pug
    └── layout.pug
```

### Conventiona in Community

__Directories__

```
  - lib/ is intended for code that can run as-is
  - src/ is intended for code that needs to be manipulated before it can be used
  - build/ is for any scripts or tooling needed to build your project
  - dist/ is for compiled modules that can be used with other systems.
  - bin/ is for any executable scripts, or compiled binaries used with, or built from your module.
  - test/ is for all of your project/module's test scripts
  - unit/ is a sub-directory for unit tests
  - integration/ is a sub-directory for integration tests
  - env/ is for any environment that's needed for testing
```

__lib & src__

The difference in using lib vs src should be:

```
    lib if you can use node's require() directly
    src if you can not, or the file must otherwise be manipulated before use
```

If you are committing copies of module/files that are from other systems, the use of (lib|src)/vendor/(vendor-name)/(project-name)/ is suggested.

## SCSS

```
stylesheets/
|
|-- modules/                    # Common modules
|   |-- _all.scss               # Include to get all modules
|   |-- _utility.scss           # Module name
|   |-- _colors.scss            # Etc...
|   ...
|
|-- partials/                   # Partials
|   |-- _base.sass              # imports for all mixins + global project variables
|   |-- _buttons.scss           # buttons
|   |-- _figures.scss           # figures
|   |-- _grids.scss             # grids
|   |-- _typography.scss        # typography
|   |-- _reset.scss             # reset
|   ...
|
|-- vendor/                     # CSS or Sass from other projects
|   |-- _colorpicker.scss
|   |-- _jquery.ui.core.scss
|   ...
|
`-- main.scss                   # primary Sass file
```
