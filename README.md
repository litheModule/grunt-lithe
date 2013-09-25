# grunt-lithe

> lithe for grunt plugin

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-lithe --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-lithe');
```

## The "lithe" task

### Overview
In your project's Gruntfile, add a section named `lithe` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  lithe: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    },
  },
})
```

### Options

#### options.basepath
Type: `String`
Default value: `undefined`

required

#### options.alias

Type: `Object`
Default value: `undefined`

required

### Usage Examples

#### Options
In this example, custom options are used to do something else with whatever else. So if the `testing` file has the content `Testing` and the `123` file had the content `1 2 3`, the generated result in this case would be `Testing: 1 2 3 !!!`

```js
grunt.initConfig({
  lithe: {
    options: {
      basepath: 'test/',
      alias:{}
    },
    files: {
      'test/tmp/': 'test/conf/'
    }
  }
})
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
0.0.1 
