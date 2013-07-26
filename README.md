# Markdown Boilerplate

> Use Assemble to generate HTML pages from markdown content. Useful for wikis, gh-pages, documentation and blogs or sites with markdown posts.

#### Thank you to [Upstage](https://github.com/upstage) for the theme used in the [live demo](http://assemble.github.io/boilerplate-markdown) (the same used on http://assemble.io)!

This is not intended to be "documentation" for Assemble, the content used in this project is for example purposes. So you will learn by browsing the source code, rendered code, and seeing how it renders in the browser.

## Related information

* [grunt-init-assemble](https://github.com/assemble/grunt-init-assemble): use [grunt-init](http://gruntjs.com/project-scaffolding) to launch new Assemble projects in seconds.
* [Assemble's documentation](http://assemble.io): if you want to learn more about Assemble in general, this is a great place to start.
* [assemble-boilerplate](https://github.com/assemble/assemble-boilerplate): see more examples.


## What you'll see in the examples

* How to use [file globbing](https://github.com/isaacs/node-glob) to include multiple markdown files based on specified patterns.

### Rendering markdown to markdown

* How to generate markdown files from markdown pages. See [../src/content/TOC.md](../src/content/TOC.md)
* How to use markdown "includes" that either render to HTML or render as markdown
* How to use markdown layouts for generating markdown files

### Rendering markdown to HTML

* How to write markdown "inline" with HTML and have it render to HTML
* How to generate HTML files from markdown pages, layouts and content.


## Getting started

If you have trouble getting started, please visit the documentation at http://assemble.io, or [create an Issue](https://github.com/assemble/assemble/issues) at Assemble's GitHub repo, we're happy to help.

This plugin requires Grunt `~0.4.1`. If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install assemble --save-dev
```

Once the plugin has been installed, it may be enabled inside your [Gruntfile][Getting Started] with this line of JavaScript:

```js
grunt.loadNpmTasks('assemble');
```

## The "assemble" task
In your project's Gruntfile, add a section named `assemble` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  assemble: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    }
  }
});
grunt.loadNpmTasks('assemble');

grunt.registerTask('default', [
  'jshint',
  'assemble'
]);
```
Task targets, files and options may be specified according to the grunt [Configuring tasks](http://gruntjs.com/configuring-tasks) guide.


You should now be able to run `grunt assemble` to build the project.

Visit [Assemble's documentation](http://assemble.io) for more information.


## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [grunt][].

## Release History
_(Nothing yet)_
