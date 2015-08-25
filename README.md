# grunt-lithe
[![Build Status](https://travis-ci.org/litheModule/grunt-lithe.png?branch=master)](https://travis-ci.org/litheModule/grunt-lithe) [![依赖模块状态](https://david-dm.org/litheModule/grunt-lithe.png)](http://david-dm.org/litheModule/grunt-lithe)

[中文](https://github.com/litheModule/grunt-lithe/blob/master/docs/README_zh-cn.md)

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

## lithe multitask

In your project's Gruntfile, add a section named `lithe` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  lithe: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    }
  }
});
```

### Options

#### options.basepath

Type: `String`

Default value: `undefined`

(required) your lithe project basepath

#### options.alias

Type: `Object`

Default value: `undefined`

your lithe config alias object

#### Usage Examples

__Options__

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
});
```

## litheCompress multitask

Compress js files. The method "require" will not be compressed.

#### options.cwd

Type: `String`

Your lithe project local basepath.

#### src

Type: `String`

The relative path of original files .

#### dest

Type: `String`

The relative path of compressed files.

#### Usage Examples

__Options__

```js
var path = require('path');

grunt.initConfig({
  litheCompress : {
    options : {
      cwd: path.resolve(__dirname,'../')
    },
    publish : {
      src : 'tools/temp/trunk/js/',
      dest : 'tools/temp/compressed/js/'
    }
  }
});
```

## litheConcat multitask

Concat files according to the dependene.

### options.cwd

Type: `String`

Your lithe project local basepath.

#### src

Type: `String`

The relative path of original files .

#### dest

Type: `String`

The relative path of concated files.

#### target

Type: `String`

The relative path. Get startup files.

#### walk

Type: `Boolean`

Whether traverse the target directory.

#### alias

Type: `String`

The relative file path. Get the alias config from the file.

#### global

Type: `String`

The relative file path of global module.

The output files will not merge dependent files that were defined in global file.

### withoutGlobal

Type: `Array`

It is a string array.

Each string is a relative path.

List of files in the directory will merge all dependent files.

#### Usage Examples

__Options__

```js
var path = require('path');

grunt.initConfig({
  litheConcat : {
    options : {
      cwd: path.resolve(__dirname,'../')
    },
    publish : {
      src : 'tools/temp/temp/js/',
      dest : 'tools/temp/concat/js/',
      walk : true,
      alias : 'config.js',
      global : 'conf/global.js',
      withoutGlobal : [
        'conf/mods/',
        'conf/routes/',
        'conf/pl/'
      ],
      target : 'conf/'
    }
  }
});
```

## litheGetAllRequiredFiles multitask

Get all required files for conf files.

#### options.cwd

Type: `String`

Your lithe project local basepath.

#### src

Type: `String`

The relative path of original files .

#### dest

Type: `String`

The relative path of selected files.

#### alias

Type: `String`

The relative file path. Get the alias config from the file.

#### target

Type: `String`

The relative path. Get startup files.

#### Usage Examples

__Options__

```js
var path = require('path');

grunt.initConfig({
  litheGetAllRequiredFiles : {
    options : {
      cwd: path.resolve(__dirname,'../')
    },
    //Get all required files of js files in "conf" directory.
    packPrepare : {
      src : 'tools/temp/trunk/js/',
      dest : 'tools/temp/prepare/js/',
      alias : 'config.js',
      target : 'conf/'
    }
  }
});
```

## Contributing

In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
* 2015-08-25 v0.2.0 Add litheCompress task, add litheConcat task, add litheGetAllRequiredFiles task.
* 2014-03-26 v0.1.7 Fix filter bug .
* 2013-12-19 v0.1.6 Fix the compress file bug. Improve docs.
* 2013-12-10 v0.1.5 Fix module git uri.
* 2013-12-04 v0.1.4 The lithe task add filter option, add unit tests.
* 2013-09-26 v0.1.1 Fix the bug that 'isJs' should be used as a function.
* 2013-09-25 v0.1.0 The first official release.
