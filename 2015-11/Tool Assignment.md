---
title: Learn node related tools
---

In this assignment, you'll go through some usual tools used in node development.

## Background

When deploying a node.js web application, you may encounter the following concepts: package management, continous intergration, continous deployment.

As for package management, there are two aspects: backend package management and frontend package management.

- For backend package management, we use [npm](https://www.npmjs.com/) which should be include in node.js installation.

- For frontend package management, there are more than one choices, but most popular one is [bower](http://bower.io/), which is indeed a node.js package.

As for continous intergration and continous deployment, the common basis of them is build tools, there are many choices, most populars are [Grunt](http://gruntjs.com/), [Gulp](http://gulpjs.com/). For intergration, some code quality tools should be taken at a glance:

- Lint tools:
  - [JSHint](http://jshint.com/)
  - [ESLint](http://eslint.org/)
- Test tools:
  - [mocha](http://mochajs.org/)
  - [Istanbul](https://github.com/gotwarlost/istanbul)

## Assignment

This assignment can be done with the following steps:

0. Install [yeoman](http://yeoman.io/) and webapp generator.
- Use webapp generator to start a new project.
- Try the command `grunt server`, `grunt test`, `grunt dist` and read the results.
- Read the Gruntfile.js carefully and anwser the following questions:
  - How many tasks does this Gruntfile.js define? What are they?
  - How does grunt plugins are loaded? (Hint: see [jit-grunt](https://github.com/shootaroo/jit-grunt))
  - Explain config for each plugin.
  
## Submission

Fork this repo and add your submission in this folder, named with `[your github id].md`, then open a pull request.
