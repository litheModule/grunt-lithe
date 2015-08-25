# grunt-lithe
[![Build Status](https://travis-ci.org/litheModule/grunt-lithe.png?branch=master)](https://travis-ci.org/litheModule/grunt-lithe) [![依赖模块状态](https://david-dm.org/litheModule/grunt-lithe.png)](http://david-dm.org/litheModule/grunt-lithe)

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

(required) lithe 项目的线上根路径

#### options.alias

Type: `Object`

Default value: `undefined`

lithe 的配置文件中的 alias 选项。

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

用于压缩JS文件，"require"方法名称不会在压缩中替换为其他字符

#### options.cwd

Type: `String`

lithe 项目的本地根路径

#### src

Type: `String`

原始文件的相对路径（相对于根路径）

#### dest

Type: `String`

输出的压缩文件的相对路径

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

对基于 lithe 的项目文件进行打包合并

### options.cwd

Type: `String`

lithe 项目的本地根路径

#### src

Type: `String`

原始文件的相对路径

#### dest

Type: `String`

合并后文件的输出路径

#### target

Type: `String`

页面入口文件的存放位置，相对路径

#### walk

Type: `Boolean`

是否深度遍历目标目录

#### alias

Type: `String`

填写配置文件的相对路径，用于自动获取 alias 选项

#### global

Type: `String`

公共文件的相对路径

打包输出的文件，不会合并公共文件中已定义的文件

### withoutGlobal

Type: `Array`

是一个字符串数组

每个字符串是一个相对路径

列举目录下的文件，合并时会合并所有依赖到的文件，不管其是否在公共文件中列出

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

获取所有打包依赖的文件

#### options.cwd

Type: `String`

lithe 项目的本地根路径

#### src

Type: `String`

原始文件的相对路径

#### dest

Type: `String`

选中文件的输出路径

#### alias

Type: `String`

填写配置文件的相对路径，用于自动获取 alias 选项

#### target

Type: `String`

项目入口文件的相对路径

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


