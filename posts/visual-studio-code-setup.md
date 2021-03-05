---
title: Visual Studio Code Editor Setup and Tweaks
created: 2016-07-12T17:46:30+05:30
author: ashishdoneriya
description: Customize and Tweak visual studio code and make the most out of it.
permalink: /visual-studio-code-setup.html
categories:
  - web-development
  - ide
tags:
  - vscode
updated: 2016-07-12T17:46:30+05:30
---
Below are the settings and extensions for visual studio code editor (vscode) to make the most out of it. These are the optimized settings for vscode to make the life of web developers easy.

Goto `File > Preferences > User Settigs` and paste the following Settings in User Settings

```json
// Place your settings in this file to overwrite the default settings
{
	"editor.detectIndentation": false,
	"editor.fontFamily": "Ubuntu Mono",
	"editor.fontSize": 20,
	"editor.lineHeight": 24,
	"editor.formatOnType": true,
	"editor.insertSpaces": false,
	"editor.tabSize": 4,
	"editor.wordWrap": "on",
	"files.trimTrailingWhitespace": true,
	"html.format.indentInnerHtml": true,
	"html.format.preserveNewLines": true,
	"html.format.unformatted": "code",
	"html.format.wrapLineLength": 0,
	"telemetry.enableTelemetry": false,
	"javascript.implicitProjectConfig.checkJs" : true,
	"window.newWindowDimensions": "maximized",
	"window.openFoldersInNewWindow": "off",
	"workbench.activityBar.visible": true,
	"files.hotExit": "off",
	"window.restoreWindows": "none"
}
```


**Note :** The setting `files.exclude` is especially for Angular 2. If you need git you set the value of `git.enabled` to true.

Another minimal settings for vscode. It will not auto format code. :

```json
{
	"editor.detectIndentation": true,
	"editor.fontFamily": "Ubuntu Mono",
	"editor.fontSize": 24,
	"editor.formatOnPaste": false,
	"editor.formatOnSave": false,
	"editor.formatOnType": false,
	"editor.insertSpaces": false,
	"editor.tabSize": 4,
	"editor.wordWrap": "on",
	"html.format.enable": false,
	"javascript.format.enable": false,
	"telemetry.enableTelemetry": false,
	"javascript.implicitProjectConfig.checkJs" : true,
	"typescript.check.tscVersion": false,
	"window.newWindowDimensions": "maximized",
	"window.openFoldersInNewWindow": "off"
}
```


Extensions  
1. AB HTML Formatter  
2. Auto Close Tag  
3. Auto Rename Tag  
4. Bracket Pair Colorizer  
5. EditorConfig for Visual Studio Code  
6. HTML Snippets  
7. JavaScript (ES6) snippets  
8. JS, CSS, HTML Formatting  
9. Open in Browser  
10. Prettier &#8211; Code Formatter  
11. Whitespacer  
12. [Monaki Black theme](https://marketplace.visualstudio.com/items?itemName=vip32bit.theme-monokai-black)

For Nodejs code to work

```bash
npm install typings -g -S
```

