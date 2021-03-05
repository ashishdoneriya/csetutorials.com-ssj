---
title: Customize and Improve Button Theme in WordPress
created: 2016-07-12T18:57:31+05:30
author: ashishdoneriya
description: Modify wordpress button theme, give it a dark look and improve its font and readability.
permalink: /customize-improve-button-theme-wordpress.html
tags:
  - Button Theme
  - Wordpress
updated: 2016-07-12T18:57:31+05:30
categories:
  - wordpress
---
Steps to clustomize button theme in wordpress.

1. [Install](https://wordpress.com/themes/button/) and active button theme.
2. Now goto `Appearance > Editor`
3. Replace all contents of Stylesheet (style.css) with the follwing css and save it. 
```css
/*
Theme Name: Button
Theme URI: https://wordpress.com/themes/button/
Description: A stylish, lighthearted theme for crafters, hobbyists, and creatives.
Version: 1.0.4
Author: Automattic
Author URI: http://automattic.com
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Text Domain: button
*/

/*--------------------------------------------------------------
&gt;&gt;&gt; TABLE OF CONTENTS:
----------------------------------------------------------------
# Normalize
# Typography
# Elements
# Forms
# Navigation
	## Links
	## Menus
# Accessibility
# Alignments
# Clearings
# Widgets
# Content
    ## Posts and pages
	## Asides
	## Comments
# Infinite scroll
# Media
	## Captions
	## Galleries
--------------------------------------------------------------*/
/*--------------------------------------------------------------
# Normalize
--------------------------------------------------------------*/
@import url(https://fonts.googleapis.com/css?family=Roboto:400,300,500,700|Ubuntu+Mono|Oswald:400,700);
html {
  font-family: sans-serif;
  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%; }

body {
  margin: 0; }

article,
aside,
details,
figcaption,
figure,
footer,
header,
main,
menu,
nav,
section,
summary {
  display: block; }

audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline; }

audio:not([controls]) {
  display: none;
  height: 0; }

[hidden],
template {
  display: none; }

a {
  background-color: transparent; }

a:active,
a:hover {
  outline: 0; }

abbr[title] {
  border-bottom: 1px dotted; }

b,
strong {
  font-weight: bold; }

dfn {
  font-style: italic; }

h1 {
  font-size: 2em;
  margin: 0.67em 0; }

mark {
  background: #ff0;
  color: #000; }

small {
  font-size: 80%; }

sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline; }

sup {
  top: -0.5em; }

sub {
  bottom: -0.25em; }

img {
  border: 0; }

svg:not(:root) {
  overflow: hidden; }

figure {
  margin: 1em 40px; }

hr {
  box-sizing: content-box;
  height: 0; }

pre {
  overflow: auto; }

code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em; }

button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0; }

button {
  overflow: visible; }

button,
select {
  text-transform: none; }

button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer; }

button[disabled],
html input[disabled] {
  cursor: default; }

button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0; }

input {
  line-height: normal; }

input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0; }

input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto; }

input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box; }

input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none; }

fieldset {
  border: 1px solid silver;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em; }

legend {
  border: 0;
  padding: 0; }

textarea {
  overflow: auto; }

optgroup {
  font-weight: bold; }

table {
  border-collapse: collapse;
  border-spacing: 0; }

td,
th {
  padding: 0; }

/*--------------------------------------------------------------
# Typography
--------------------------------------------------------------*/
body,
button,
input,
select,
textarea {
  color: #777777;
  font-family: Lato, Helvetica, sans-serif;
  font-size: 16px;
  font-size: 1rem;
  line-height: 1.6; }

h1, h2, h3, h4, h5, h6 {
  clear: both;
  font-family: Lora, Garamond, serif;
  font-style: italic;
  font-weight: normal;
  line-height: 1.2; }

h1 {
  font-size: 3.052em; }

h2 {
  font-size: 2.441em; }

h3 {
  font-size: 1.953em; }

h4 {
  font-size: 1.563em; }

h5 {
  font-size: 1.25em; }

h6 {
  font-size: 1em; }

p {
  margin-bottom: 1.5em; }

dfn, cite, em, i {
  font-style: italic; }

blockquote {
  margin: 0 1.5em; }

address {
  margin: 0 0 1.5em; }

pre {
  background: #f3f3f3;
  font-family: "Courier 10 Pitch", Courier, monospace;
  font-size: 15px;
  font-size: 0.9375rem;
  line-height: 1.6;
  margin-bottom: 1.6em;
  max-width: 100%;
  overflow: auto;
  padding: 1.6em; }

code, kbd, tt, var {
  font-family: Monaco, Consolas, "Andale Mono", "DejaVu Sans Mono", monospace;
  font-size: 15px;
  font-size: 0.9375rem; }

abbr, acronym {
  border-bottom: 1px dotted #666;
  cursor: help; }

mark, ins {
  background: #f3f3f3;
  text-decoration: none; }

big {
  font-size: 125%; }

/*--------------------------------------------------------------
# Elements
--------------------------------------------------------------*/
html {
  box-sizing: border-box; }

*,
*:before,
*:after {
  /* Inherit box-sizing to make it easier to change the property for components that leverage other behavior; see http://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/ */
  box-sizing: inherit; }

body {
  background: #f3f3f3;
  /* Fallback for when there is no custom background color defined. */
  background-size: 50px auto; }

body.user-background {
  background-size: auto auto; }

blockquote, q {
  color: #666;
  font-family: Lora, Garamond, serif;
  font-style: italic;
  font-size: 1.25em;
  quotes: "" ""; }
  blockquote:before, blockquote:after, q:before, q:after {
    content: ""; }
  blockquote blockquote, q blockquote {
    font-size: inherit; }

hr {
  background-color: #f3f3f3;
  border: 0;
  height: 1px;
  margin-bottom: 1.5em; }

ul, ol {
  margin: 0 0 1.5em 1.5em;
  padding-left: 0; }

ul {
  list-style: disc; }

ol {
  list-style: decimal; }

li &gt; ul,
li &gt; ol {
  margin-bottom: 0;
  margin-left: .75em;
  padding-left: 0; }

dt {
  font-weight: bold; }

dd {
  margin: 0 1.5em 1.5em; }

img {
  height: auto;
  /* Make sure images are scaled correctly. */
  max-width: 100%;
  /* Adhere to container width. */ }

table {
  margin: 0 0 1.5em;
  width: 100%; }

td,
th {
  border-bottom: 1px solid #dddddd;
  padding: 5px 3px; }

th {
  border-bottom: 3px solid #dddddd; }

/*--------------------------------------------------------------
# Forms
--------------------------------------------------------------*/
button,
input[type="button"],
input[type="reset"],
input[type="submit"],
#infinite-handle span button {
  border: 1px dashed;
  border-color: white;
  background: #666;
  box-shadow: none;
  color: white;
  font-size: 14px;
  font-weight: bold;
  line-height: 1;
  margin-top: 5px;
  margin-left: 5px;
  outline: 5px solid #666;
  padding: 0.75em 1em;
  text-shadow: none;
  text-decoration: none;
  text-transform: uppercase;
  transition: 0.3s; }
  button:hover,
  input[type="button"]:hover,
  input[type="reset"]:hover,
  input[type="submit"]:hover,
  #infinite-handle span button:hover {
    background: #666;
    color: white;
    outline: 5px solid #666;
    box-shadow: none; }
  button:active, button:focus,
  input[type="button"]:active,
  input[type="button"]:focus,
  input[type="reset"]:active,
  input[type="reset"]:focus,
  input[type="submit"]:active,
  input[type="submit"]:focus,
  #infinite-handle span button:active,
  #infinite-handle span button:focus {
    background: #666;
    color: white;
    outline: 5px solid #666;
    box-shadow: none; }
  button + button,
  button + input[type="button"],
  button + input[type="reset"],
  button + input[type="submit"],
  input[type="button"] + button,
  input[type="button"] + input[type="button"],
  input[type="button"] + input[type="reset"],
  input[type="button"] + input[type="submit"],
  input[type="reset"] + button,
  input[type="reset"] + input[type="button"],
  input[type="reset"] + input[type="reset"],
  input[type="reset"] + input[type="submit"],
  input[type="submit"] + button,
  input[type="submit"] + input[type="button"],
  input[type="submit"] + input[type="reset"],
  input[type="submit"] + input[type="submit"],
  #infinite-handle span button + button,
  #infinite-handle span button + input[type="button"],
  #infinite-handle span button + input[type="reset"],
  #infinite-handle span button + input[type="submit"] {
    margin-left: .75em; }

#infinite-handle span:hover button,
#infinite-handle span button:hover {
  background: #666;
  outline: 5px solid #666;
  box-shadow: none;
  border: 1px dashed;
  border-color: white;
  box-shadow: none;
  color: white;
  font-size: 14px;
  font-weight: bold;
  line-height: 1;
  margin-top: 5px;
  margin-left: 5px;
  padding: 0.75em 1em;
  text-shadow: none;
  text-transform: uppercase;
  transition: 0.3s; }

input[type="text"],
input[type="email"],
input[type="url"],
input[type="password"],
input[type="search"],
textarea {
  color: #777777;
  display: inline-block;
  background: #f3f3f3;
  border: 1px dashed #dddddd;
  border-radius: 3px; }
  input[type="text"]:focus,
  input[type="email"]:focus,
  input[type="url"]:focus,
  input[type="password"]:focus,
  input[type="search"]:focus,
  textarea:focus {
    border-color: #666;
    color: #515151;
    outline: none; }

input[type="text"],
input[type="email"],
input[type="url"],
input[type="password"],
input[type="search"] {
  padding: 0.65em 0.75em; }

textarea {
  padding-left: 3px;
  width: 100%; }

/*--------------------------------------------------------------
# Navigation
--------------------------------------------------------------*/
/*--------------------------------------------------------------
## Links
--------------------------------------------------------------*/
a {
  color: #666; }
  a:visited {
    color: #666; }
  a:hover, a:focus, a:active {
    color: #666; }
  a:focus {
    outline: thin dotted; }
  a:hover, a:active {
    outline: 0; }

/*--------------------------------------------------------------
## Menus
--------------------------------------------------------------*/
.main-navigation {
  clear: both;
  display: block;
  margin: 2.25em auto 4.5em;
  padding: 0.75em 0;
  text-transform: uppercase;
  font-size: 13px;
  font-weight: bold;
  letter-spacing: 1px;
  width: 100%; }
  .main-navigation ul {
    list-style: none;
    margin: 0;
    padding: 0; }
  .main-navigation li {
    list-style: none; }
    .main-navigation li li {
      padding-left: 1.5em; }
      .main-navigation li li li {
        padding-left: 2.25em; }
        .main-navigation li li li li {
          padding-left: 3em; }
          .main-navigation li li li li li {
            padding-left: 3.75em; }
  .main-navigation a {
    border-top: 1px dashed #dddddd;
    display: block;
    margin: 0.75em 0 0;
    padding: 0.75em 0 0;
    text-decoration: none;
    width: 100%; }
    .main-navigation a:hover, .main-navigation a:visited:hover {
      color: #666; }
    .main-navigation a:visited {
      color: #777777; }

/* Small menu. */
.menu-toggle,
.main-navigation.toggled ul {
  display: block; }

.menu-toggle {
  font-size: 16px;
  margin: 0 auto; }
  .menu-toggle:before {
    display: inline-block;
    font-family: Genericons;
    font-size: 16px;
    font-weight: normal;
    font-style: normal;
    margin-right: 6px;
    text-decoration: none;
    text-transform: none;
    line-height: 1;
    vertical-align: middle;
    position: relative;
    top: -2px;
    content: "\f419"; }

.main-navigation ul {
  display: none; }

@media screen and (min-width: 40.063em) {
  .menu-toggle {
    display: none; }

  .main-navigation {
    border-top: 1px dashed #dddddd;
    border-bottom: 1px dashed #dddddd; }

  .main-navigation ul {
    display: block; } }
.comment-navigation,
.posts-navigation,
.post-navigation {
  border-bottom: 1px dashed #dddddd;
  border-top: 1px dashed #dddddd;
  font-family: Lora, Garamond, serif;
  font-style: italic;
  padding: 0.75em 0; }
  .site-main .comment-navigation, .site-main
  .posts-navigation, .site-main
  .post-navigation {
    margin: 0 0 3em;
    overflow: hidden; }
  .comment-navigation .nav-previous,
  .posts-navigation .nav-previous,
  .post-navigation .nav-previous {
    border-bottom: 2px solid #f3f3f3;
    margin-bottom: .75em;
    padding-bottom: .75em;
    font-size: 1.25em;
    line-height: 1.3;
    width: 100%; }
  .comment-navigation .nav-next,
  .posts-navigation .nav-next,
  .post-navigation .nav-next {
    font-size: 1.25em;
    line-height: 1.3;
    text-align: right;
    width: 100%; }
  .comment-navigation .meta-nav,
  .posts-navigation .meta-nav,
  .post-navigation .meta-nav {
    clear: both;
    color: #666;
    display: block;
    font-family: Lato, Helvetica, sans-serif;
    font-size: 13px;
    font-style: normal;
    font-weight: bold;
    letter-spacing: 1px;
    text-transform: uppercase;
    width: 100%; }
  .comment-navigation a,
  .posts-navigation a,
  .post-navigation a {
    text-decoration: none;
    transition: 0.3s; }

.social-links ul a:before {
  font-family: "Genericons";
  font-size: 24px;
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  text-decoration: none;
  vertical-align: text-bottom;
  -webkit-font-smoothing: antialiased; }

.social-links {
  margin: 0 auto;
  padding: 0;
  text-align: center; }

.social-links ul {
  list-style: none;
  margin: 0 0 1.5em 0;
  padding: 0; }

.social-links ul li {
  display: inline-block;
  list-style: none;
  margin: 0 0.09375em;
  padding: 0; }

.social-links ul a {
  border-radius: 50%;
  background: #666;
  display: inline-block;
  margin-bottom: .1875em;
  position: relative;
  text-decoration: none;
  transition: 0.3s; }

.social-links ul a:before {
  color: #fff;
  display: block;
  font-size: 24px;
  padding: .5em;
  text-align: center;
  transition: 0.3s; }

.social-links ul a:after {
  content: "";
  display: block;
  border: 1px solid white;
  border-radius: 50%;
  position: absolute;
  left: 3px;
  top: 3px;
  width: 42px;
  height: 42px;
  z-index: 1; }

.social-links ul a:hover {
  background: #666;
  color: white;
  text-decoration: none;
  transition: 0.3s; }

.social-links ul a:hover:before {
  color: white; }

.social-links ul a[href*='wordpress.org']:before,
.social-links ul a[href*='wordpress.com']:before {
  content: '\f205'; }

.social-links ul a[href*='facebook.com']:before {
  content: '\f204'; }

.social-links ul a[href*='twitter.com']:before {
  content: '\f202'; }

.social-links ul a[href*='dribbble.com']:before {
  content: '\f201'; }

.social-links ul a[href*='plus.google.com']:before {
  content: '\f206'; }

.social-links ul a[href*='pinterest.com']:before {
  content: '\f209'; }

.social-links ul a[href*='github.com']:before {
  content: '\f200'; }

.social-links ul a[href*='tumblr.com']:before {
  content: '\f214'; }

.social-links ul a[href*='youtube.com']:before {
  content: '\f213'; }

.social-links ul a[href*='flickr.com']:before {
  content: '\f211'; }

.social-links ul a[href*='vimeo.com']:before {
  content: '\f212'; }

.social-links ul a[href*='instagram.com']:before {
  content: '\f215'; }

.social-links ul a[href*='codepen.io']:before {
  content: '\f216'; }

.social-links ul a[href*='linkedin.com']:before {
  content: '\f207'; }

.social-links ul a[href*='foursquare.com']:before {
  content: '\f226'; }

.social-links ul a[href*='reddit.com']:before {
  content: '\f222'; }

.social-links ul a[href*='digg.com']:before {
  content: '\f221'; }

.social-links ul a[href*='getpocket.com']:before {
  content: '\f224'; }

.social-links ul a[href*='path.com']:before {
  content: '\f219'; }

.social-links ul a[href*='stumbleupon.com']:before {
  content: '\f223'; }

.social-links ul a[href*='spotify.com']:before {
  content: '\f515'; }

.social-links ul a[href*='twitch.tv']:before {
  content: '\f516'; }

.social-links ul a[href*='dropbox.com']:before {
  content: '\f225'; }

.social-links ul a[href*='/feed']:before {
  content: '\f413'; }

.social-links ul a[href*='skype']:before {
  content: '\f220'; }

.social-links ul a[href*='mailto']:before {
  content: '\f410'; }

.social-links ul a:before {
  content: '\f415'; }

/*--------------------------------------------------------------
# Accessibility
--------------------------------------------------------------*/
/* Text meant only for screen readers. */
.screen-reader-text {
  clip: rect(1px, 1px, 1px, 1px);
  position: absolute !important;
  height: 1px;
  width: 1px;
  overflow: hidden; }
  .screen-reader-text:hover, .screen-reader-text:active, .screen-reader-text:focus {
    background-color: #f3f3f3;
    border-radius: 3px;
    box-shadow: 0 0 2px 2px rgba(0, 0, 0, 0.6);
    clip: auto !important;
    color: #666;
    display: block;
    font-size: 14px;
    font-size: 0.875rem;
    font-weight: bold;
    height: auto;
    left: 5px;
    line-height: normal;
    padding: 15px 23px 14px;
    text-decoration: none;
    top: 5px;
    width: auto;
    z-index: 100000;
    /* Above WP toolbar. */ }

/*--------------------------------------------------------------
# Alignments
--------------------------------------------------------------*/
.alignleft {
  display: inline;
  float: left;
  margin-right: 1.5em;
  margin-top: .75em;
  margin-bottom: .75em; }

.alignright {
  display: inline;
  float: right;
  margin-left: 1.5em;
  margin-top: .75em;
  margin-bottom: .75em; }

.aligncenter {
  display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: .75em;
  margin-bottom: .75em; }

/*--------------------------------------------------------------
# Clearings
--------------------------------------------------------------*/
.clear:before,
.clear:after,
.entry-content:before,
.entry-content:after,
.comment-content:before,
.comment-content:after,
.site-header:before,
.site-header:after,
.site-content:before,
.site-content:after,
.site-footer:before,
.site-footer:after {
  content: "";
  display: table; }

.clear:after,
.entry-content:after,
.comment-content:after,
.site-header:after,
.site-content:after,
.site-footer:after {
  clear: both; }

/*--------------------------------------------------------------
# Widgets
--------------------------------------------------------------*/
.widget {
  font-size: 14px;
  margin: 0 0 3em;
  /* Make sure select elements fit in widgets. */ }
  .widget select {
    margin-left: 1px;
    max-width: 100%; }
  .widget a {
    transition: 0.3s;
    text-decoration: none; }
  .widget ul {
    list-style: none;
    margin: 0;
    padding: 0; }
    .widget ul li {
      list-style: none;
      border-top: 1px dashed #dddddd;
      margin-top: .75em;
      padding-top: .75em; }
      .widget ul li li {
        padding-left: 1.5em; }
        .widget ul li li li {
          padding-left: 3em; }
          .widget ul li li li li {
            padding-left: 4.5em; }

.widget-title {
  font-style: italic;
  font-size: 1.25em;
  width: 100%; }
  .widget-title a {
    color: #777777;
    text-decoration: none; }
  .widget-title:before {
    background: url(img/button.svg) no-repeat;
    background-size: 84px 22px;
    background-position: 0 0;
    content: "";
    display: inline-block;
    float: left;
    margin-right: .45em;
    position: relative;
    top: -2px;
    width: 22px;
    height: 32px; }

/* Search widget */
.widget_search .search-field {
  box-sizing: border-box;
  width: 100%;
  max-width: 100%; }

.widget_search .search-submit {
  display: none; }

td#next {
  text-align: right; }

/* RSS */
.widget_rss cite {
  font-family: Lora, Garamond, serif; }
.widget_rss .rss-date {
  clear: both;
  color: #666;
  display: block;
  margin-bottom: .375em;
  width: 100%; }
.widget_rss .rssSummary {
  margin-bottom: .375em; }

/* Recent comments */
.widget_recent_comments td,
.widget_recent_comments td.recentcommentsavatarend,
.widget_recent_comments td.recentcommentsavatartop,
.widget_recent_comments td.recentcommentstexttop,
.widget_recent_comments td.recentcommentstextend {
  border-top: 1px dashed #dddddd !important;
  line-height: 1.5;
  padding-top: .5em;
  padding-bottom: .5em;
  vertical-align: top; }
.widget_recent_comments td.recentcommentsavatarend,
.widget_recent_comments td.recentcommentsavatartop {
  vertical-align: middle; }

/*--------------------------- -----------------------------------
# Structure
--------------------------------------------------------------*/
.site {
  background-color: white;
  margin: 0 auto;
  padding: 1.75em;
  position: relative; }

.content-area {
  float: none;
  margin: 0;
  width: 100%; }

.site-main {
  margin: 0; }

.site-content .widget-area {
  border-top: 1px dashed #dddddd;
  float: none;
  margin-top: 3em;
  padding-top: 1.5em;
  overflow: hidden;
  width: 100%; }

.site-footer {
  clear: both;
  margin: 4.5em 0 0;
  width: 100%; }

.site-header {
  text-align: center; }

.site-logo {
  margin: 0 0 0.75em; }

.header-image {
  margin: 0 0 0.375em; }

.site-title {
  font-size: 2.441em;
  font-style: italic;
  font-weight: bold;
  margin: 0; }
  .site-title a,
  .site-title a:visited {
    color: #666;
    text-decoration: none; }

.site-description {
  color: #666;
  font-size: 18px;
  font-style: italic;
  margin: 0.5em 0 0.25em; }

.hentry {
  border-bottom: 1px dashed #dddddd;
  margin: 0 0 4.5em;
  padding: 0 0 3em;
  position: relative; }
  .hentry:after {
    content: "";
    display: block;
    background-color: #fff;
    background-image: url(img/button.svg);
    background-repeat: no-repeat;
    background-size: 132px 35px;
    background-position: -46px top;
    width: 88px;
    height: 35px;
    position: absolute;
    left: 50%;
    top: 100%;
    -ms-transform: translate(-50%, -16px);
    -webkit-transform: translate(-50%, -18px);
    transform: translate(-50%, -18px); }

.sticky {
  /* Required for WP.org */ }

.error404 .page-content .search-field {
  margin-right: 5px;
  position: relative;
  top: 1px; }

.page-links {
  clear: both;
  margin: 0.75em 0; }

.page-links span.active-link {
  background-color: #666;
  border-radius: 35px;
  color: white;
  display: inline-block;
  line-height: 29px;
  margin: 0 0 3px;
  padding: 3px;
  width: 35px;
  height: 35px;
  text-align: center;
  transition: .3s;
  font-weight: bold; }

.page-links a span.active-link {
  background-color: #666;
  border-radius: 35px;
  color: white;
  display: inline-block;
  line-height: 29px;
  margin: 0 0 3px;
  padding: 3px;
  text-align: center;
  width: 35px;
  height: 35px; }

.page-links a:hover span.active-link {
  background-color: #666;
  color: white;
  transition: .3s; }

.format-link .entry-title a:after {
  font-size: 32px;
  text-align: center;
  display: inline-block;
  font-family: "Genericons";
  font-style: normal;
  font-weight: normal;
  font-variant: normal;
  line-height: 1;
  margin-left: 4px;
  text-decoration: inherit;
  vertical-align: middle;
  position: relative;
  top: -2px;
  text-transform: none;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  speak: none;
  content: "\f442"; }

.featured-image {
  line-height: 0;
  margin: 0 0 1.5em;
  position: relative;
  text-align: center; }
  .featured-image img {
    max-width: 99.9%; }
  .featured-image .shadow {
    box-shadow: inset 0 0 85px 1px rgba(0, 0, 0, 0.1);
    display: inline-block;
    position: absolute;
    z-index: 0;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0; }
  .featured-image:before, .featured-image:after {
    background-image: url(img/corner.svg);
    background-size: 45px;
    background-repeat: no-repeat;
    content: "";
    display: block;
    width: 45px;
    height: 45px;
    position: absolute;
    top: -1px;
    left: -1px;
    z-index: 1; }
  .featured-image:after {
    left: auto;
    right: -1px;
    -ms-transform: rotate(90deg);
    -webkit-transform: rotate(90deg);
    transform: rotate(90deg); }
  .featured-image &gt; .corners:before, .featured-image &gt; .corners:after {
    background-image: url(img/corner.svg);
    background-size: 45px;
    background-repeat: no-repeat;
    content: "";
    display: block;
    width: 45px;
    height: 45px;
    position: absolute;
    bottom: -1px;
    left: -1px;
    z-index: 1;
    -ms-transform: rotate(-90deg);
    -webkit-transform: rotate(-90deg);
    transform: rotate(-90deg); }
  .featured-image &gt; .corners:after {
    left: auto;
    right: -1px;
    -ms-transform: rotate(-180deg);
    -webkit-transform: rotate(-180deg);
    transform: rotate(-180deg); }

.entry-meta,
.entry-footer {
  color: #dddddd;
  font-size: 14px;
  margin-bottom: 0;
  text-align: center; }
  .entry-meta a,
  .entry-meta a:visited,
  .entry-footer a,
  .entry-footer a:visited {
    color: #666;
    transition: 0.3s;
    text-decoration: none; }
    .entry-meta a:hover,
    .entry-meta a:visited:hover,
    .entry-footer a:hover,
    .entry-footer a:visited:hover {
      color: #666; }

.entry-meta {
  margin-bottom: 1.5em; }

.entry-meta &gt; span {
  display: inline-block;
  margin: 0 0.375em; }
  .entry-meta &gt; span:after {
    content: "\00B7";
    margin-left: .75em; }
  .entry-meta &gt; span:last-of-type:after {
    display: none; }

.cat-links {
  color: #666;
  display: block;
  margin: 0 0 0.5em;
  text-align: center;
  text-transform: uppercase;
  font-size: 13px;
  font-weight: bold;
  letter-spacing: 1px; }
  .cat-links a,
  .cat-links a:visited {
    margin: 0 0.375em;
    text-decoration: none;
    transition: 0.3s; }

.tags-links,
.widget_tag_cloud {
  display: block;
  clear: both;
  margin: 0;
  width: 100%; }
  .tags-links a,
  .tags-links a:visited,
  .widget_tag_cloud a,
  .widget_tag_cloud a:visited {
    background-color: #666;
    color: white;
    display: inline-block;
    text-transform: uppercase;
    font-weight: bold;
    font-size: 13px;
    letter-spacing: 1px;
    height: 24px;
    margin-right: 1.5em;
    margin-bottom: .75em;
    padding: 2px 1px 2px 5px;
    position: relative;
    text-decoration: none;
    transition: 0.3s; }
    .tags-links a:last-of-type,
    .tags-links a:visited:last-of-type,
    .widget_tag_cloud a:last-of-type,
    .widget_tag_cloud a:visited:last-of-type {
      margin-right: 0; }
    .tags-links a:hover,
    .tags-links a:visited:hover,
    .widget_tag_cloud a:hover,
    .widget_tag_cloud a:visited:hover {
      background-color: #666;
      color: white; }
      .tags-links a:hover:after,
      .tags-links a:visited:hover:after,
      .widget_tag_cloud a:hover:after,
      .widget_tag_cloud a:visited:hover:after {
        border-left-color: #666; }
      .tags-links a:hover:before,
      .tags-links a:visited:hover:before,
      .widget_tag_cloud a:hover:before,
      .widget_tag_cloud a:visited:hover:before {
        border-top-color: #666;
        border-bottom-color: #666; }
    .tags-links a:before,
    .tags-links a:visited:before,
    .widget_tag_cloud a:before,
    .widget_tag_cloud a:visited:before {
      border-width: 12px;
      border-left-width: 8px;
      border-right-width: 0;
      border-style: solid;
      border-top-color: #666;
      border-left-color: transparent;
      border-right-color: transparent;
      border-bottom-color: #666;
      content: "";
      display: inline-block;
      margin: 0;
      position: absolute;
      left: -8px;
      top: 0;
      transition: 0.3s; }
    .tags-links a:after,
    .tags-links a:visited:after,
    .widget_tag_cloud a:after,
    .widget_tag_cloud a:visited:after {
      border-width: 12px;
      border-right-width: 0;
      border-style: solid;
      border-left-color: #666;
      border-right-color: transparent;
      border-top-color: transparent;
      border-bottom-color: transparent;
      content: "";
      display: inline-block;
      margin: 0;
      position: absolute;
      right: -12px;
      top: 0;
      transition: 0.3s; }

.widget_tag_cloud {
  margin-bottom: 3em; }
  .widget_tag_cloud a {
    font-size: 14px !important; }

.entry-summary {
  position: relative; }

a.more-link {
  box-shadow: inset 0 -80px 80px -5px rgba(255, 255, 255, 0.75);
  color: #666;
  font-family: Lora, Garamond, serif;
  font-weight: bold;
  font-style: italic;
  display: block;
  width: 100%;
  height: 124px;
  position: absolute;
  bottom: -32px;
  padding-top: 100px;
  z-index: 1;
  text-align: center;
  text-decoration: none;
  transition: 0.3s; }
  a.more-link:hover {
    color: #666;
    box-shadow: inset 0 -80px 80px -50px rgba(255, 255, 255, 0.75); }

.updated {
  display: none; }

.published.updated {
  display: inline; }

.entry-title {
  font-size: 1.563em;
  margin: 0 0 0.5em;
  text-align: center;
  font-style: italic; }
  .entry-title a,
  .entry-title a:visited {
    color: #777777;
    text-decoration: none; }
  .entry-title:after {
    background-color: #f3f3f3;
    content: "";
    display: block;
    margin: 0.5em auto;
    width: 20%;
    height: 2px; }

.entry-content {
  margin: 0 0 1.5em; }
  .entry-content a {
    word-break: break-word;
    word-wrap: break-word; }

.page-title {
  font-size: 1.563em; }

.page-header {
  border-bottom: 1px dashed #dddddd;
  margin-bottom: 3em; }

.site-footer {
  color: #666;
  font-size: 13px;
  font-weight: bold;
  letter-spacing: 1px;
  text-align: center;
  text-transform: uppercase; }
  .site-footer .sep {
    display: block;
    visibility: hidden;
    clear: both;
    width: 100%;
    height: 1px; }
  .site-footer a,
  .site-footer a:visited {
    color: #666;
    text-decoration: none;
    transition: 0.3s; }
    .site-footer a:hover,
    .site-footer a:visited:hover {
      color: #666; }

/* =Comments */
.comments-title small,
.comment-reply-title small {
  float: right; }

.comment-list,
.comment-list .children {
  list-style: none; }

.comment-list {
  margin: 0;
  padding: 0; }
  .comment-list .children {
    margin-left: 2.25em; }

.comment-list &gt; .comment:first-of-type {
  border-top: 0;
  padding-top: 0; }

.comment {
  border-top: 1px dashed #dddddd;
  margin-top: 1.5em;
  padding-top: 1.5em; }
  .comment .comment-content {
    margin-top: 1.5em; }

.comment-meta {
  color: #777777;
  display: block; }
  .comment-meta .comment-metadata {
    font-size: 13px;
    font-weight: bold;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-left: 80px; }
    .comment-meta .comment-metadata a,
    .comment-meta .comment-metadata a:visited {
      transition: 0.3s; }
      .comment-meta .comment-metadata a:hover,
      .comment-meta .comment-metadata a:visited:hover {
        color: #666; }
  .comment-meta a,
  .comment-meta a:visited {
    color: #666;
    text-decoration: none; }
  .comment-meta .comment-author .avatar {
    border: 1px dashed #666;
    padding: 3px;
    border-radius: 50%;
    display: block;
    float: left;
    position: relative;
    width: 60px;
    height: 60px; }
  .comment-meta .comment-author .fn {
    color: #777777;
    font-family: Lora, Garamond, serif;
    font-size: 1.25em;
    font-weight: normal;
    font-style: italic;
    display: block;
    margin-left: 80px;
    text-transform: none; }
    .comment-meta .comment-author .fn a,
    .comment-meta .comment-author .fn a:visited {
      color: #777777; }

.bypostauthor &gt; .comment-body:first-of-type .comment-author .avatar {
  border-color: #666; }

.comments-area .edit-link:before {
  color: #dddddd;
  content: "\00B7";
  display: inline;
  margin: 0 0.875em 0 0.75em; }

.comments-title,
h3#reply-title {
  font-size: 1.563em; }

div#respond {
  border-top: 1px dashed #dddddd !important;
  margin: 1.5em 0 0;
  padding: 1.5em 0 0; }

.comment div#respond {
  border-top: 0 none !important;
  padding-top: 0; }

.comment-form label {
  display: inline-block;
  width: 109px; }

.comment-form-author,
.comment-form-email,
.comment-form-url,
.comment-form-comment {
  margin: 0 0 1.5em;
  position: relative; }
  .comment-form-author label,
  .comment-form-email label,
  .comment-form-url label,
  .comment-form-comment label {
    font-size: 13px;
    font-weight: bold;
    letter-spacing: 1px;
    padding: 0.65em 0.75em;
    position: absolute;
    left: 0;
    top: 4px;
    text-transform: uppercase; }
  .comment-form-author input,
  .comment-form-author textarea,
  .comment-form-email input,
  .comment-form-email textarea,
  .comment-form-url input,
  .comment-form-url textarea,
  .comment-form-comment input,
  .comment-form-comment textarea {
    clear: both;
    padding-left: 6em;
    width: 100%; }
  .comment-form-author textarea,
  .comment-form-email textarea,
  .comment-form-url textarea,
  .comment-form-comment textarea {
    padding: 2em 0.75em 0.375em; }

.comment-respond {
  border-top: 1px dashed #dddddd;
  padding-top: 1.5em;
  margin-top: 1.5em; }

.comment-reply-link {
  transition: 0.3s; }

.says {
  display: none; }

.form-allowed-tags {
  color: #666; }

.no-comments {
  font-style: italic;
  text-align: center; }

.required {
  color: #666; }

/*--------------------------------------------------------------
# Infinite scroll
--------------------------------------------------------------*/
/* Globally hidden elements when Infinite Scroll is supported and in use. */
.infinite-scroll .posts-navigation,
.infinite-scroll.neverending .site-footer {
  /* Theme Footer (when set to scrolling) */
  display: none; }

/* When Infinite Scroll has reached its end we need to re-display elements that were hidden (via .neverending) before. */
.infinity-end.neverending .site-footer {
  display: block; }

#infinite-footer {
  z-index: 999; }

#infinite-footer .container {
  font-style: italic;
  position: relative;
  color: #777777;
  border-top: 1px dashed #dddddd; }

#infinite-footer .container a {
  color: #666; }

#infinite-footer .container a:hover {
  color: #666; }

#infinite-footer .blog-info a,
#infinite-footer .blog-credits {
  color: #666;
  font-style: normal;
  font-weight: bold;
  text-transform: uppercase; }

.infinite-loader {
  clear: both;
  width: 28px;
  height: 43px;
  margin: 0 auto 14px;
  padding-top: 27px; }

#infinite-handle {
  clear: both;
  width: 100%;
  margin: 0 auto;
  text-align: center; }
  #infinite-handle span {
    background: transparent;
    border: 0;
    border-radius: 0;
    color: inherit; }

.jetpack-video-wrapper {
  margin-bottom: 1.5em; }

.jetpack-slideshow.slideshow-black {
  background-color: #dddddd;
  border-color: #dddddd; }

/*--------------------------------------------------------------
# Media
--------------------------------------------------------------*/
.page-content .wp-smiley,
.entry-content .wp-smiley,
.comment-content .wp-smiley {
  border: none;
  margin-bottom: 0;
  margin-top: 0;
  padding: 0; }

/* Make sure embeds and iframes fit their containers. */
embed,
iframe,
object {
  max-width: 100%; }

figure {
  margin: 0; }

/*--------------------------------------------------------------
## Captions
--------------------------------------------------------------*/
.wp-caption {
  margin-bottom: 1.5em;
  max-width: 100%; }
  .wp-caption img[class*="wp-image-"] {
    display: block;
    margin-left: auto;
    margin-right: auto; }
  .wp-caption .wp-caption-text {
    margin: 0.8075em 0; }

.wp-caption-text {
  text-align: center;
  font-family: Lora, Garamond, serif;
  font-style: italic; }

/*--------------------------------------------------------------
## Galleries
--------------------------------------------------------------*/
.gallery {
  margin-bottom: 1.5em; }

.gallery-item {
  display: inline-block;
  text-align: center;
  vertical-align: top;
  width: 100%; }
  .gallery-columns-2 .gallery-item {
    max-width: 50%; }
  .gallery-columns-3 .gallery-item {
    max-width: 33.33%; }
  .gallery-columns-4 .gallery-item {
    max-width: 25%; }
  .gallery-columns-5 .gallery-item {
    max-width: 20%; }
  .gallery-columns-6 .gallery-item {
    max-width: 16.66%; }
  .gallery-columns-7 .gallery-item {
    max-width: 14.28%; }
  .gallery-columns-8 .gallery-item {
    max-width: 12.5%; }
  .gallery-columns-9 .gallery-item {
    max-width: 11.11%; }

.gallery-caption {
  display: block; }

/*
 * jQuery FlexSlider v2.5.0
 * http://www.woothemes.com/flexslider/
 *
 * Copyright 2012 WooThemes
 * Free to use under the GPLv2 and later license.
 * http://www.gnu.org/licenses/gpl-2.0.html
 *
 * Contributing author: Tyler Smith (@mbmufffin)
 *
 */
@font-face {
  font-family: 'flexslider-icon';
  src: url("fonts/flexslider-icon.eot");
  src: url("fonts/flexslider-icon.eot?#iefix") format("embedded-opentype"), url("fonts/flexslider-icon.woff") format("woff"), url("fonts/flexslider-icon.ttf") format("truetype"), url("fonts/flexslider-icon.svg#flexslider-icon") format("svg");
  font-weight: normal;
  font-style: normal; }

.flex-container a:hover,
.flex-slider a:hover,
.flex-container a:focus,
.flex-slider a:focus {
  outline: none; }

.slides,
.slides &gt; li,
.flex-control-nav,
.flex-direction-nav {
  margin: 0;
  padding: 0;
  list-style: none; }

.flex-pauseplay span {
  text-transform: capitalize; }

.flexslider {
  margin: 0;
  padding: 0; }

.flexslider .slides &gt; li {
  display: none;
  -webkit-backface-visibility: hidden; }

.flexslider .slides img {
  width: 100%;
  display: block; }

.flexslider .slides:after {
  content: "\0020";
  display: block;
  clear: both;
  visibility: hidden;
  line-height: 0;
  height: 0; }

html[xmlns] .flexslider .slides {
  display: block; }

* html .flexslider .slides {
  height: 1%; }

.no-js .flexslider .slides &gt; li:first-child {
  display: block; }

.flexslider {
  background-color: #dddddd;
  margin: 0;
  position: relative;
  zoom: 1; }

.flexslider .slides {
  zoom: 1; }

.flexslider .slides img {
  max-width: 99.9%;
  height: auto; }

.flex-viewport {
  max-height: 2000px;
  -webkit-transition: all 1s ease;
  transition: all 1s ease; }

.loading .flex-viewport {
  max-height: 300px; }

.carousel li {
  margin-right: 0; }

.flex-control-nav {
  width: 100%;
  position: absolute;
  bottom: 20px;
  text-align: center;
  z-index: 10; }

.flex-control-nav li {
  margin: 0 6px;
  display: inline-block;
  zoom: 1;
  *display: inline; }

.flex-control-paging li a {
  width: 14px;
  height: 14px;
  display: block;
  background: white;
  background: rgba(255, 255, 255, 0.4);
  cursor: pointer;
  text-indent: -9999px;
  border-radius: 20px; }

.flex-control-paging li a:hover {
  background: #666; }

.flex-control-paging li a.flex-active {
  background: #666;
  cursor: default; }

@media screen and (max-width: 860px) {
  .flex-direction-nav .flex-prev {
    opacity: 1;
    left: 10px; }

  .flex-direction-nav .flex-next {
    opacity: 1;
    right: 10px; } }
/*--------------------------------------------------------------
# Media queries
--------------------------------------------------------------*/
@media only screen and (min-width: 40.063em) {
  .site {
    margin: 3em auto;
    padding: 3em 2em;
    width: 80%; }

  .site-title {
    font-size: 3.052em; }

  .entry-title {
    font-size: 1.953em; }

  .featured-image {
    overflow: hidden; }
    .featured-image .post-thumbnail {
      transition: 0.5s;
      transform: scale(1.025, 1.025); }
    .featured-image:before, .featured-image:after {
      background-size: 75px;
      width: 75px;
      height: 75px; }
    .featured-image &gt; .corners {
      overflow: hidden; }
      .featured-image &gt; .corners:before, .featured-image &gt; .corners:after {
        background-size: 75px;
        width: 75px;
        height: 75px; }
    .featured-image:hover .post-thumbnail {
      transform: scale(1, 1); }

  .comment-navigation .nav-previous,
  .posts-navigation .nav-previous,
  .post-navigation .nav-previous {
    margin: 0;
    padding: 0;
    border: 0;
    float: left;
    width: 50%; }
  .comment-navigation .nav-next,
  .posts-navigation .nav-next,
  .post-navigation .nav-next {
    float: right;
    width: 50%; }

  .main-navigation {
    padding: 0;
    text-align: center; }
    .main-navigation ul {
      list-style: none; }
      .main-navigation ul ul {
        background: white;
        text-align: left;
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
        float: left;
        position: absolute;
        top: 3em;
        left: -999em;
        z-index: 99999; }
        .main-navigation ul ul ul {
          left: -999em;
          top: 0; }
        .main-navigation ul ul li {
          border-top: 0;
          border-bottom: 1px dashed #dddddd;
          margin: 0;
          padding: 0; }
          .main-navigation ul ul li:hover &gt; ul, .main-navigation ul ul li.focus &gt; ul {
            left: 100%; }
          .main-navigation ul ul li:last-of-type {
            border: 0; }
          .main-navigation ul ul li a:after {
            display: none; }
          .main-navigation ul ul li.menu-item-has-children &gt; a:before, .main-navigation ul ul li.page_item_has_children &gt; a:before {
            -webkit-transform: rotate(-90deg);
            transform: rotate(-90deg);
            top: .75em;
            right: .75em; }
        .main-navigation ul ul a {
          padding: 0.75em 1em;
          width: 200px; }
      .main-navigation ul li:hover &gt; ul,
      .main-navigation ul li.focus &gt; ul {
        left: auto; }
    .main-navigation li {
      border-top: 0;
      display: inline-block;
      margin-top: 0;
      padding: 0 0.5em;
      position: relative; }
      .main-navigation li a:after {
        content: "\00B7";
        color: #666;
        display: inline;
        margin-left: 1em; }
      .main-navigation li:last-of-type a:after {
        display: none; }
      .main-navigation li.menu-item-has-children a:after, .main-navigation li.page_item_has_children a:after {
        padding-left: 1.3em; }
      .main-navigation li.menu-item-has-children:last-of-type a:after, .main-navigation li.page_item_has_children:last-of-type a:after {
        content: "";
        display: inline-block;
        padding-left: 1.6em; }
      .main-navigation li.menu-item-has-children &gt; a:before, .main-navigation li.page_item_has_children &gt; a:before {
        font-size: 16px;
        text-align: center;
        display: inline-block;
        font-family: "Genericons";
        font-style: normal;
        font-weight: normal;
        font-variant: normal;
        line-height: 1;
        text-decoration: inherit;
        text-transform: none;
        -moz-osx-font-smoothing: grayscale;
        -webkit-font-smoothing: antialiased;
        speak: none;
        content: "\f431";
        position: absolute;
        right: 1.3em;
        top: .725em; }
    .main-navigation a {
      border: 0;
      color: #777777;
      display: block;
      margin: 0;
      padding-top: .75em;
      padding-bottom: .75em;
      text-decoration: none;
      transition: 0.3s; }
      .main-navigation a:hover, .main-navigation a:visited:hover {
        color: #666; }
      .main-navigation a:visited {
        color: #777777; }
    .main-navigation .current_page_item &gt; a,
    .main-navigation .current-menu-item &gt; a,
    .main-navigation .current_page_ancestor &gt; a {
      color: #666; } }
/* min-width 641px, medium screens */
@media only screen and (min-width: 64.063em) {
  .site {
    padding: 3em;
    max-width: 1142px; }

  .content-area {
    float: left;
    margin: 0 -25% 0 0;
    width: 90%; }

  .site-main {
    margin: 0 25% 0 0; }

  .site-content .widget-area {
    float: right;
    width: 25%;
    border-top: 0;
    margin-top: 0;
    padding-top: 0; }

  .no-sidebar .site-main,
  .page-template-full-width-page .site-main {
    margin: 0; }

  .no-sidebar .content-area,
  .page-template-full-width-page .content-area {
    float: none;
    margin: 0;
    width: 100%; }

  .site-footer .sep {
    clear: none;
    display: inline;
    margin: 0 0.75em;
    width: auto;
    height: auto;
    visibility: visible; } }
/* min-width 1025px, large screens */
@media only screen and (min-width: 75em) {
  .site {
    padding: 3em 5em; }

  .no-sidebar .site {
    width: 58.35%; } }
.site-title a, .site-title a:visited {
  color: #59554e;
  font-size: 48px;
  font-style:normal;
  font-weight:bold;
  font-family: serif  !important;
}
.site-description {
  color: #666;
}

body {
  background: #555;
}
* {
	font-family: 'Roboto', sans-serif;
  font-style: normal !important;
}
p {
    font-size:16px;
    line-height:25px;
    color:#333;
    text-align: justify;
}
article {
    font-size:18px;
    line-height:28px;
    color:#333;
    text-align: justify;
}
div p {
    font-size:18px;
    line-height:28px;
    color:#333;
    text-align: justify;
}
::selection{
    background-color: #333;
    color: #fff;
}
pre *, code *{
    font-size:18px;
    line-height:28px;
    font-family: "Ubuntu Mono"  !important;
}

pre, code{
    font-size:18px;
    line-height:28px;
    font-family: "Ubuntu Mono"  !important;
}

code {
  font-size:18px !important;
    background:#fff !important;
  font-family: "Ubuntu Mono" !important;
  padding: 2px 4px;
    border-radius:4px;
}

pre.prettyprint {
  	
}
code.border { 
    border: 1px solid #dfdfdf !important;
}
pre {
  max-height:500px;
  margin-top:20px;
  margin-bottom:20px;
}
/******************************* My Custom Part *******************************/


.widget-area a {
  font-size:16px;
  color:#333;
  }
 .entry-title, .entry-title a{
  font-family: Oswald !important;
  color:#444 !important;
  }
  .entry-meta a, .entry-meta a:visited, .entry-footer a:visited {
  color:#555 !important;
  }
.widget-title {
	font-style: normal !important;
	font-size: 18px !important;
	font-family: Roboto !important;
	color: #444 !important;
	text-align: center;
	text-transform: uppercase;
}
.widget-title::before{
	display:none;  
}
a.more-link {
  color: #666;
}
h1, h2, h3, h4, h5, h6 {
 font-family:Roboto; 
}
h3.subheading {
  font-size:18px;
  font-weight:bold;
}

.site-footer, .site-footer a, .site-footer a:visited {
 color: #444; 
}
```

4. That's it.

**Before Customization :**

<div id="attachment_270" style="width: 899px" class="wp-caption aligncenter">
  <a href="/wp-content/uploads/2016/07/button-theme.jpg"><img aria-describedby="caption-attachment-270" loading="lazy" class="size-full wp-image-270" src="/wp-content/uploads/2016/07/button-theme.jpg" alt="Button Theme" width="889" height="453" srcset="/wp-content/uploads/2016/07/button-theme.jpg 889w, /wp-content/uploads/2016/07/button-theme-500x255.jpg 500w, /wp-content/uploads/2016/07/button-theme-400x204.jpg 400w" sizes="(max-width: 889px) 100vw, 889px" /></a>
  
  <p id="caption-attachment-270" class="wp-caption-text">
    Button Theme
  </p>
</div>

**After Customization :**

<div id="attachment_280" style="width: 936px" class="wp-caption aligncenter">
  <a href="/wp-content/uploads/2016/07/modified-button-theme.jpg"><img aria-describedby="caption-attachment-280" loading="lazy" class="size-full wp-image-280" src="/wp-content/uploads/2016/07/modified-button-theme.jpg" alt="Modified Button Theme" width="926" height="451" srcset="/wp-content/uploads/2016/07/modified-button-theme.jpg 926w, /wp-content/uploads/2016/07/modified-button-theme-500x244.jpg 500w, /wp-content/uploads/2016/07/modified-button-theme-400x195.jpg 400w" sizes="(max-width: 926px) 100vw, 926px" /></a>
  
  <p id="caption-attachment-280" class="wp-caption-text">
    Modified Button Theme
  </p>
</div>

You could also change the footer. Goto `Appearance > Editor`. Open `footer.php` and replace its content with the following.

```php
<?php
/**
 * The template for displaying the footer.
 *
 * Contains the closing of the #content div and all content after
 *
 * @package Button
 */

?>

	</div><!-- #content -->

	<footer id="colophon" class="site-footer" role="contentinfo">
		<div class="site-info">
			<div style="float:left">Copyright © 2016</div>
			<div style="float:right">
				<a href="about">About</a>
				<span class="sep">|</span>
				<a href="contact">Contact</a>
				<span class="sep">|</span>
				<a href="sitemap_index.xml">Sitemap</a>
				<span class="sep">|</span>
				<a href="privacy-policy">Privacy Policy</a>
				<span class="sep">|</span>
				<a href="tos">Terms of Service</a>
			</div>
		</div><!-- .site-info -->
	</footer><!-- #colophon -->
</div><!-- #page -->

<?php wp_footer(); ?>

</body>
</html>
```

The footer will look exactly like this website.

[<img loading="lazy" class="aligncenter size-full wp-image-287" src="/wp-content/uploads/2016/07/customized-button-theme-footer.jpg" alt="customized-button-theme-footer" width="746" height="57" srcset="/wp-content/uploads/2016/07/customized-button-theme-footer.jpg 746w, /wp-content/uploads/2016/07/customized-button-theme-footer-500x38.jpg 500w, /wp-content/uploads/2016/07/customized-button-theme-footer-400x31.jpg 400w" sizes="(max-width: 746px) 100vw, 746px" />](/wp-content/uploads/2016/07/customized-button-theme-footer.jpg)

You can change the links according to your requirements

If you want to show the last updated date of post instead of published date then open file `template.tags.php` and replace its content with the following

```
<?php
/**
 * Custom template tags for this theme.
 *
 * Eventually, some of the functionality here could be replaced by core features.
 *
 * @package Button
 */

if ( ! function_exists( 'button_posted_on' ) ) :
/**
 * Prints HTML with meta information for the current post-date/time and author.
 */
function button_posted_on() {
	$time_string = '<time class="entry-date published updated" datetime="%1$s">%2$s</time>';
	if ( get_the_time( 'U' ) !== get_the_modified_time( 'U' ) ) {
		$time_string = '<time class="entry-date published" datetime="%3$s">%4$s</time><time class="entry-date updated" datetime="%3$s">%4$s</time>';
	}

	$time_string = sprintf( $time_string,
		esc_attr( get_the_date( 'c' ) ),
		esc_html( get_the_date() ),
		esc_attr( get_the_modified_date( 'c' ) ),
		esc_html( get_the_modified_date() )
	);

	$posted_on = '<a href="' . esc_url( get_permalink() ) . '" rel="bookmark">' . $time_string . '</a>';

	$byline = '<span class="author vcard"><a class="url fn n" href="' . esc_url( get_author_posts_url( get_the_author_meta( 'ID' ) ) ) . '">' . esc_html( get_the_author() ) . '</a></span>';

	$formats = get_theme_support( 'post-formats' );
	$format = get_post_format();
	$postformat = '';

	if ( $format && in_array( $format, $formats[0] ) ) {
		$postformat = sprintf( '<span class="post-format"><a href="%1$s" title="%2$s">%3$s</a></span>', // WPCS: XSS OK.
								esc_url( get_post_format_link( $format ) ),
								sprintf( esc_attr_x( 'All %1$s posts', 'post format archives link', 'button' ), get_post_format_string( $format ) ),
								esc_html( get_post_format_string( $format ) ) );
	}

	echo '<span class="posted-on">' . $posted_on . '</span><span class="byline"> ' . $byline . '</span>' . $postformat; // WPCS: XSS OK.

	if ( ! is_single() && ! post_password_required() && ( comments_open() || get_comments_number() ) ) {
		echo '<span class="comments-link">';
		comments_popup_link( esc_html__( 'Leave a comment', 'button' ), esc_html__( '1 Comment', 'button' ), esc_html__( '% Comments', 'button' ) );
		echo '</span>';
	}

	edit_post_link( esc_html__( 'Edit', 'button' ), '<span class="edit-link">', '</span>' );
}
endif;

if ( ! function_exists( 'button_entry_footer' ) ) :
/**
 * Prints HTML with meta information for the tags and comments.
 */
function button_entry_footer() {

	// Hide tag text for pages and archives
	if ( 'post' == get_post_type() && is_single() ) {
		$tags_list = get_the_tag_list( '', ' ' );
		if ( $tags_list ) {
			printf( '<div class="tags-links">%1$s</div>', $tags_list ); // WPCS: XSS OK.
		}
	}
}
endif;


if ( ! function_exists( 'button_entry_cats' ) ) :
/**
 * Prints HTML with meta information for the categories.
 */
function button_entry_cats() {
	// Hide category text for pages.
	if ( 'post' == get_post_type() ) {
		/* translators: used between list items, there is a space */
		$categories_list = get_the_category_list( esc_html__( ' · ', 'button' ) );
		if ( $categories_list && button_categorized_blog() ) {
			printf( '<span class="cat-links">%1$s</span>', $categories_list ); // WPCS: XSS OK.
		}
	}
}
endif;


/**
 * Returns true if a blog has more than 1 category.
 *
 * @return bool
 */
function button_categorized_blog() {
	if ( false === ( $all_the_cool_cats = get_transient( 'button_categories' ) ) ) {
		// Create an array of all the categories that are attached to posts.
		$all_the_cool_cats = get_categories( array(
			'fields'     => 'ids',
			'hide_empty' => 1,

			// We only need to know if there is more than one category.
			'number'     => 2,
		) );

		// Count the number of categories that are attached to the posts.
		$all_the_cool_cats = count( $all_the_cool_cats );

		set_transient( 'button_categories', $all_the_cool_cats );
	}

	if ( $all_the_cool_cats > 1 ) {
		// This blog has more than 1 category so button_categorized_blog should return true.
		return true;
	} else {
		// This blog has only 1 category so button_categorized_blog should return false.
		return false;
	}
}

/**
 * Flush out the transients used in button_categorized_blog.
 */
function button_category_transient_flusher() {
	if ( defined( 'DOING_AUTOSAVE' ) && DOING_AUTOSAVE ) {
		return;
	}
	// Like, beat it. Dig?
	delete_transient( 'button_categories' );
}
add_action( 'edit_category', 'button_category_transient_flusher' );
add_action( 'save_post',     'button_category_transient_flusher' );

if ( ! function_exists( 'button_gallery_slideshow' ) ) :

function button_gallery_slideshow() {

	global $post;

	if ( 'gallery' !== get_post_format() ) {
		return;
	}

	$images = '';
	$gallery = get_post_gallery( $post->ID, false );

	if ( ! empty( $gallery ) ) {

		echo '<div class="flexslider carousel">';
		echo '<ul class="slides">';

		$images = explode( ',', $gallery['ids'] ); // Get the gallery image IDs

		foreach ( $images as $image ) { ?>

			<li>
				<?php echo wp_get_attachment_image( $image, 'button-slideshow' ); ?>
			</li>

			<?php
		}

		echo '</ul>';
		echo '</div>';
	}
}

endif;


if ( ! function_exists( 'button_continue_reading_link' ) ) :
/**
 * Returns an ellipsis and "Continue reading" plus off-screen title link for excerpts
 */
function button_continue_reading_link() {
	return '… <a href="'. esc_url( get_permalink() ) . '" class="more-link">' . sprintf( __( 'Continue reading <span class="screen-reader-text">%1$s</span>', 'button' ), esc_attr( strip_tags( get_the_title() ) ) ) . '</a>';
}
endif; // button_continue_reading_link

/**
 * Replaces "[...]" (appended to automatically generated excerpts) with button_continue_reading_link().
 *
 * To override this in a child theme, remove the filter and add your own
 * function tied to the excerpt_more filter hook.
 */
function button_auto_excerpt_more() {
	return button_continue_reading_link();
}
add_filter( 'excerpt_more', 'button_auto_excerpt_more' );


/**
 * Returns the URL from the post.
 *
 * @uses get_the_link() to get the URL in the post meta (if it exists) or
 * the first link found in the post content.
 *
 * Falls back to the post permalink if no URL is found in the post.
 *
 * @return string URL
 */
function button_get_link_url() {
	$content = get_the_content();
	$has_url = get_url_in_content( $content );

	return ( $has_url ) ? $has_url : apply_filters( 'the_permalink', get_permalink() );
}
```
