---
title: How to format vue files in Visual Studio Code Editor
created: 2018-02-16T09:58:04+05:30
author: ashishdoneriya
description: Guide to format vuejs .vue files in vscode (visual studio code editor)
permalink: /format-vue-files-visual-studio-code.html
categories:
  - web-development
  - ide
tags:
  - vetur
  - vscode
  - vuejs
updated: 2018-02-16T09:58:04+05:30
---

A Guide to format vue files in visual studio code editor.

First Install the below extensions :

1. [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)  
2. [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)  
3. [Vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)

Now in your project base directory, create a file `.editorconfig` and paste the below content

```conf
root = true

[*]
charset = utf-8
indent_style = tab
indent_size = 4
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true
```


Create another file `.prettierrc` in you base directory and paste the below content

```json
{
	"useTabs": true,
	"singleQuote": true
}
```


If there is a file called `jsconfig.json` in the project base directory then add `"include": ["./src/**/*"]`. If you don't have `jsconfig.json` then create the file and paste the below content.

```json
{
	"compilerOptions": {
		"target": "es5",
		"lib": ["dom", "es2015"],
		"module": "es2015",
		"moduleResolution": "node",
		"experimentalDecorators": true,
		"allowJs": true,
		"strict": true,
		"noUnusedLocals": true,
		"noUnusedParameters": true,
		"jsx": "preserve",
		"jsxFactory": "h"
	},
	"include": ["./**/*.ts", "./src/**/*"],
	"compileOnSave": false
}
```


Now Open `File > Preferences > Settings` (User Settings) and add the following property

```json
"vetur.format.defaultFormatter": {
		"html": "prettier",
		"css": "prettier",
		"postcss": "prettier",
		"scss": "prettier",
		"less": "prettier",
		"js": "prettier",
		"ts": "prettier",
		"stylus": "stylus-supremacy"
	}
```


In my case my User Settings file look like this

```json
{
	"editor.detectIndentation": false,
	"editor.fontFamily": "Ubuntu Mono",
	"editor.fontSize": 22,
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
	"javascript.implicitProjectConfig.checkJs": true,
	"window.newWindowDimensions": "maximized",
	"window.openFoldersInNewWindow": "off",
	"workbench.activityBar.visible": true,
	"editor.quickSuggestions": {
		"strings": true
	},
	"vetur.format.defaultFormatter": {
		"html": "prettier",
		"css": "prettier",
		"postcss": "prettier",
		"scss": "prettier",
		"less": "prettier",
		"js": "prettier",
		"ts": "prettier",
		"stylus": "stylus-supremacy"
	}
}
```


That's it. So if you want to format your .vue file, then right click > Format Document.

Example Template :: <a href="https://github.com/ashishdoneriya/vue-class-component-template" rel="noopener" target="_blank">https://github.com/ashishdoneriya/vue-class-component-template</a>

In a blog post, I have created a [list of extensions](/visual-studio-code-setup.html) that would be helpful in web development. You can try out that.
