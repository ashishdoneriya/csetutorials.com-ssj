---
title: How to add linting to your Vuejs Project in vscode
created: 2018-02-19T09:48:59+05:30
author: ashishdoneriya
description: Step by step guide to add linting to your vuejs project using elint in Visual Studio Code
permalink: /add-linting-vuejs-project.html
categories:
  - web-development
  - ide
tags:
  - eslint
  - vscode
  - vuejs
updated: 2018-02-19T09:48:59+05:30
---
Hello Vue JS developers. In this post I'm going to provide a step by step guide to add linting to your vuejs project using elint in [Visual Studio Code](/visual-studio-code-setup.html) which is one of the vue developer tools.

Steps

1. Execute the command in project base directory to install the eslint related dependencies

```bash
npm install --save-dev eslint eslint-friendly-formatter eslint-loader eslint-plugin-import eslint-plugin-node eslint-plugin-promise eslint-plugin-standard eslint-plugin-vue babel-eslintbabel-eslint
```


2. Create a file `.eslintrc.js` in your project directory and put the following content

```js
// https://eslint.org/docs/user-guide/configuring

module.exports = {
	root: true,
	parserOptions: {
		parser: 'babel-eslint'
	},
	env: {
		browser: true
	},
	extends: [
		// https://github.com/vuejs/eslint-plugin-vue#priority-a-essential-error-prevention
		// consider switching to `plugin:vue/strongly-recommended` or `plugin:vue/recommended` for stricter rules.
		'plugin:vue/recommended'
	],
	// required to lint *.vue files
	plugins: ['vue'],
	// add your custom rules here
	rules: {
		"indent": "off",
		'vue/html-indent': [4, "tab", {
			attribute: 1,
			closeBracket: 0,
	  }],
		// allow async-await
		'generator-star-spacing': 'off',
		// allow debugger during development
		'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off'
	}
};
```

3. Create a file `.eslintignore` in your project directory and put the below content

```bash
/build/
/config/
/dist/
/*.js
```

4. Add <a href="https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint" rel="noopener" target="_blank">eslint plugin</a> in Visual Studio Code (vscode).

5. In Vscode, Open User Settings (File > Preferences > Settings >) and add below property

```json
"eslint.validate": [
		"javascript",
		{
			"language": "vue",
			"autoFix": true
		}
	]
```

You can also [configure](/format-vue-files-visual-studio-code.html) your vuejs project for formatting. In my case my user settings looks like this.

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
	"git.enabled": false,
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
	"extensions.ignoreRecommendations": false,
	"element-helper.version": "2.1",
	"vetur.format.defaultFormatter": {
		"html": "prettier",
		"css": "prettier",
		"postcss": "prettier",
		"scss": "prettier",
		"less": "prettier",
		"js": "prettier",
		"ts": "prettier",
		"stylus": "stylus-supremacy"
	},
	"eslint.validate": [
		"javascript",
		{
			"language": "vue",
			"autoFix": true
		}
	]
}
```


That's it. Now when you open a .vue file in vscode. It will display the number of errors/ warnings in the left sidebar of vscode. I have created a [template](https://github.com/ashishdoneriya/vue-class-component-template) on github by integrating formatter and linting.
