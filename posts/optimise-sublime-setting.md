---
title: Improve Sublime according to your requirements.
created: 2016-04-28T14:37:07+05:30
author: ashishdoneriya
description: 'Maybe sublime is a good text editor. But we all know that nothing is almighty. Therefor here are some recommendations that would make life easy. '
permalink: /optimise-sublime-setting.html
categories:
  - web-development
tags:
  - sublime
  - text editor
updated: 2016-04-28T14:37:07+05:30
---

<img loading="lazy" src="/wp-content/uploads/2016/04/sublime-text-editor.png" alt="Sublime" width="663" height="373" class="aligncenter size-large wp-image-45" srcset="/wp-content/uploads/2016/04/sublime-text-editor.png 1366w, /wp-content/uploads/2016/04/sublime-text-editor-500x281.png 500w, /wp-content/uploads/2016/04/sublime-text-editor-1024x576.png 1024w, /wp-content/uploads/2016/04/sublime-text-editor-982x552.png 982w, /wp-content/uploads/2016/04/sublime-text-editor-400x225.png 400w" sizes="(max-width: 663px) 100vw, 663px" />

Maybe Sublime is a good text editor. But we all know that nothing is almighty. Therefor here are some recommendations that would make life easy.

1. Open `Preferences > Settings - user` and put the following settings. 
```css
{
	"font_face": "Ubuntu Mono",
	"font_size": 16,
	"caret_style": "phase",
	"hot_exit": false,
	"remember_open_files": false,
	"tab_size": 4,
	"translate_tabs_to_spaces": false,
	"word_wrap": true,
	"highlight_line": true,		//Highlight current line
	"line_padding_bottom": 1,	//Increase the line height
	"line_padding_top": 1,		//Increase the line height
	"fade_fold_buttons": false,	//The arrows aren’t visible until you hover.
	"draw_white_space": "all",
	"color_scheme": "Packages/Color Scheme - Default/Monokai.tmTheme"
}
```
  
Change the settings according to your requirements
  
2. Install package installer for sublime

3. Press <code>(ctrl+`)</code> or <code>View > Show Console</code> and type
```bash
import urllib.request,os,hashlib; h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

4. After installing package manager install package [HTML-CSS-JS Prettify](https://packagecontrol.io/packages/HTML-CSS-JS%20Prettify). To install goto `Preferences > Package Control`. A box will be opened. Select Install Package, search preetify and install that. Preetify is used to beautify your code.

5. Now open `Preferences > Package Settings > HTML/CSS/JS preetify > Set preetify Preferences`. Replace the content with the following
```json
{
  // The plugin looks for a .jsbeautifyrc file in the same directory as the
  // source file you're prettifying (or any directory above if it doesn't exist,
  // or in your home folder if everything else fails) and uses those options
  // along the default ones.

  // Details: https://github.com/victorporof/Sublime-HTMLPrettify#using-your-own-jsbeautifyrc-options
  // Documentation: https://github.com/einars/js-beautify/
  "html": {
  "allowed_file_extensions": ["htm", "html", "xhtml", "shtml", "xml", "svg"],
  "brace_style": "collapse", // [collapse|expand|end-expand|none] Put braces on the same line as control statements (default), or put braces on own line (Allman / ANSI style), or just put end braces on own line, or attempt to keep them where they are
  "end_with_newline": false, // End output with newline
  "indent_char": "\t", // Indentation character
  "indent_handlebars": false, // e.g. {{#foo}}, {{/foo}}
  "indent_inner_html": false, // Indent &lt;head> and &lt;body> sections
  "indent_scripts": "keep", // [keep|separate|normal]
  "indent_size": 1, // Indentation size
  "max_preserve_newlines": 0, // Maximum number of line breaks to be preserved in one chunk (0 disables)
  "preserve_newlines": true, // Whether existing line breaks before elements should be preserved (only works before elements, not inside tags or for text)
  "unformatted": ["a", "span", "img", "code", "pre", "sub", "sup", "em", "strong", "b", "i", "u", "strike", "big", "small", "pre", "h1", "h2", "h3", "h4", "h5", "h6"], // List of tags that should not be reformatted
  "wrap_line_length": 0 // Lines should wrap at next opportunity after this number of characters (0 disables)
  },
  "css": {
  "allowed_file_extensions": ["css", "scss", "sass", "less"],
  "end_with_newline": false, // End output with newline
  "indent_char": "\t", // Indentation character
  "indent_size": 1, // Indentation size
  "newline_between_rules": true, // Add a new line after every css rule
  "selector_separator": " ",
  "selector_separator_newline": true // Separate selectors with newline or not (e.g. "a,\nbr" or "a, br")
  },
  "js": {
  "allowed_file_extensions": ["js", "json", "jshintrc", "jsbeautifyrc"],

  // Set brace_style
  //  collapse: (old default) Put braces on the same line as control statements
  //  collapse-preserve-inline: (new default) Same as collapse but better support for ES6 destructuring and other features. https://github.com/victorporof/Sublime-HTMLPrettify/issues/231
  //  expand: Put braces on own line (Allman / ANSI style)
  //  end-expand: Put end braces on own line
  //  none: Keep them where they are
  "brace_style": "collapse-preserve-inline",

  "break_chained_methods": false, // Break chained method calls across subsequent lines
  "e4x": false, // Pass E4X xml literals through untouched
  "end_with_newline": false, // End output with newline
  "indent_char": "\t", // Indentation character
  "indent_level": 1, // Initial indentation level
  "indent_size": 1, // Indentation size
  "indent_with_tabs": false, // Indent with tabs, overrides `indent_size` and `indent_char`
  "jslint_happy": false, // If true, then jslint-stricter mode is enforced
  "keep_array_indentation": false, // Preserve array indentation
  "keep_function_indentation": false, // Preserve function indentation
  "max_preserve_newlines": 0, // Maximum number of line breaks to be preserved in one chunk (0 disables)
  "preserve_newlines": true, // Whether existing line breaks should be preserved
  "space_after_anon_function": false, // Should the space before an anonymous function's parens be added, "function()" vs "function ()"
  "space_before_conditional": true, // Should the space before conditional statement be added, "if(true)" vs "if (true)"
  "space_in_empty_paren": false, // Add padding spaces within empty paren, "f()" vs "f( )"
  "space_in_paren": false, // Add padding spaces within paren, ie. f( a, b )
  "unescape_strings": false, // Should printable characters in strings encoded in \xNN notation be unescaped, "example" vs "\x65\x78\x61\x6d\x70\x6c\x65"
  "wrap_line_length": 0 // Lines should wrap at next opportunity after this number of characters (0 disables)
  }
}
```

I have changed `indent_char` and `indent_size`. 
  
5. Now to beautify you code press `Ctrl`+`alt`+`H` or go to `Preferences > Package Settings > HTML/CSS/JS preetify > Preetify Code`. Your code will be beautified. Make sure you have replaced all spaces with tabs before ( `Viez > Indentation > Convert Spaces to Tabs`)
6. Install Package [Alignment](https://packagecontrol.io/packages/Alignment). Goto `Preferences > Package Settings > Alignment > Settings - User` and paste the following content.
```json
{
	// The mid-line characters to align in a multi-line selection, changing
	// this to an empty array will disable mid-line alignment
	"alignment_chars": [
		"=", ":"
	]
}
```

For more information about alignment plugin, read from [this website](http://www.granneman.com/webdev/editors/sublime-text/packages/how-to-install-and-use-sublime-alignment/) 
  
7. You can also use [Eslint](/how-to-use-eslint.html) if you want.
  
You can find more plugins in [Google Developer Site](https://developers.google.com/web/shows/ttt/series-1/sublime-text-plugins).  

Some other packages are :
 
* [SublimeCodeIntel](https://packagecontrol.io/packages/SublimeCodeIntel)
* [jQuery](https://packagecontrol.io/packages/jQuery)
* [DocBlockr](https://packagecontrol.io/packages/DocBlockr)
* [ColorHighlighter](https://packagecontrol.io/packages/Color%20Highlighter)
* [BracketHighlighter](https://packagecontrol.io/packages/BracketHighlighter)
* [Bootstrap 3 Sublime Plugin](https://github.com/JasonMortonNZ/bs3-sublime-plugin)
* [CSScomb for Sublime Text](https://github.com/csscomb/sublime-csscomb)
