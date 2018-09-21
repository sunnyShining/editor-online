---
author: sunny
title: 在线代码编辑器
date: 2018-09-21 20:27:52
tags: javascript
categories: 编程
---

## 背景

纯粹为了在自己博客实现一个代码编辑器，方便在线测试各种代码。

## ace介绍

ACE 是一个开源的、独立的、基于浏览器的代码编辑器，可以嵌入到任何web页面或JavaScript应用程序中。ACE支持超过60种语言语法高亮，并能够处理代码多达400万行的大型文档。ACE开发团队称，ACE在性能和功能上可以媲美本地代码编辑器（如Sublime Text、TextMate和Vim等）。

## 步骤

**1.编写代码编辑器样式**

<!-- more -->

![屏幕快照 2018-09-21 下午8.21.06.png](https://upload-images.jianshu.io/upload_images/4605151-b201cabc89add913.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**2.引入ace.js**

```html
    <script type="text/javascript" src="./src-noconflict/ace.js"></script>
    <script type="text/javascript" src="./src-noconflict/ext-language_tools.js"></script>
```
**3.调用ace api实现代码编辑功能

```html
<script type="text/javascript">
    (function() {
        var editor1 = ace.edit("editor1", {
            theme: "ace/theme/monokai",
            mode: "ace/mode/html",
            wrap: true,
            autoScrollEditorIntoView: true,
            enableBasicAutocompletion: true,
            enableSnippets: true,
            enableLiveAutocompletion: true
        });
        var editor2 = ace.edit("editor2", {
            theme: "ace/theme/monokai",
            mode: "ace/mode/css",
            autoScrollEditorIntoView: true,
            enableBasicAutocompletion: true,
            enableSnippets: true,
            enableLiveAutocompletion: true
        });
        var editor3 = ace.edit("editor3", {
            theme: "ace/theme/monokai",
            mode: "ace/mode/javascript",
            autoScrollEditorIntoView: true,
            enableBasicAutocompletion: true,
            enableSnippets: true,
            enableLiveAutocompletion: true
        });
        var submit = document.querySelector('#submit');
        submit.addEventListener('click', function() {
            var htmlValue = editor1.getValue();
            var cssValue = editor2.getValue();
            var jsValue = editor3.getValue();
            var htmlStr = '<!DOCTYPE html>' +
                '<html>' +
                '<head>' +
                '<meta charset="utf-8" />' +
                '<title>代码测试</title>' +
                '<meta http-equiv="Content-Type" content="text/html; charset=utf-8"/>' +
                '<meta name="format-detection" content="telephone=no" />' +
                '<meta name="apple-mobile-web-app-status-bar-style" content="black" />' +
                '<meta name="apple-mobile-web-app-capable" content="yes" />' +
                '<meta http-equiv="X-UA-Compatible" content="chrome=1,IE=edge"/>' +
                '<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0, user-scalable=0"/>' +
                '<style type="text/css">' +
                cssValue +
                '</style>' +
                '<script type="text/javascript" src="https://cdn.bootcss.com/vConsole/3.2.0/vconsole.min.js">' +
                '</' +
                'script>' +
                '<script type="text/javascript">' +
                'new window.VConsole();' +
                '</' +
                'script>' +
                '</head>' +
                '<body>' +
                htmlValue +
                '<script type="text/javascript">' +
                jsValue +
                '</' +
                'script>' +
                '</body>' +
                '</html>';
            document.getElementById('preview').srcdoc = htmlStr;
        })
    })()
```

**4.将写好的代码放入iframe中运行

```js
document.getElementById('preview').srcdoc = htmlStr;
```

[源码](https://github.com/sunnyShining/editor-online)

效果见我的博客https://sunnyshining.github.io/lab/index.html
