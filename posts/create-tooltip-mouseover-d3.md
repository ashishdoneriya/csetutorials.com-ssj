---
title: How to create tooltip on mouseover in d3
created: 2016-04-19T21:11:31+05:30
author: ashishdoneriya
description: Example for creating tool tip for d3 graph, charts or any visualization.
permalink: /create-tooltip-mouseover-d3.html
tags:
  - angularjs
  - css
  - d3
  - html
  - javascript
  - tooltip
updated: 2016-04-19T21:11:31+05:30
categories:
  - web-development
---
Steps to create tooltip.

1. Add this html in your code 
```html
<div id="tooltip"></div>
```

2. Add this css
```css
#tooltip {
	opacity: 0;
	position: fixed;			
	text-align: left;				
	padding: 5px;				
	font: 14px sans-serif;
	color:#fff;		
	background: #333;	
	border: 0px;		
	border-radius: 2px;			
	pointer-events: none;
	z-index: 1099;
}
```


3. Now in d3 
  
```js
var tooltip = document.getElementById('tooltip');

vis.append('svg:path')
    .attr('d', lineGen(ddArray))
    .attr("transform", "translate(0,-" + 40 + ")")
    .attr('stroke', function() {
        return color[i % color.length];
    })
    .attr('stroke-width', 3)
    .data(ddArray)
    .on("mousemove", function(d) {
    	tooltip.innerHTML = 'Value : ' + d.value;

    	var left = d3.event.pageX;
		var tooltipWidth =  parseInt(tooltip.style.width, 10);
		var screenWidth = document.documentElement.clientWidth;
		if ((left + tooltipWidth) > screenWidth) {
			left = screenWidth - tooltipWidth - 20;
		}
		tooltip.style.left = left + 'px';
		tooltip.style.top = (d3.event.pageY + 20) + 'px';
		
		tooltip.style.opacity = 1;
    })
    .on("mouseout", function() {
        tooltip.style.opacity = 0;
    });
```


You can change code according to your requirements. You can use this tooltip in multiple places also. It is effective in case if you have to update you graph at regular interval because in most of the example you find on other sites, they add tooltip by appending element html at runtime through code which is very costly when you update your graph frequently and that increases the size of html and in long time maybe your browser could crashed. Therefore write html code for this once and use it multiple times like in the above example.

Below is the example to add a tooltip on any html element **without d3**

```html
<!DOCTYPE html>
<html>
<style>
#tooltip {
	opacity: 0;
	position: fixed;
	text-align: left;
	padding: 5px;
	font: 14px sans-serif;
	color: #fff;
	background: #333;
	border: 0px;
	border-radius: 2px;
	pointer-events: none;
	z-index: 1099;
}
</style>

<body>
	<h1 onmousemove="showTooltip(event, 'This is Tooltip')"
		onmouseleave="hideTooltip()">Heading</h1>
	<div id="tooltip"></div>
	<script>
	var tooltip = document.getElementById('tooltip');

	function showTooltip(event, label) {
		tooltip.innerHTML = label;
		tooltip.style.left = event.pageX + 'px';
		tooltip.style.top = (event.pageY + 20) + 'px';
		tooltip.style.opacity = 1;
	}
	function hideTooltip() {
		tooltip.style.opacity = 0;
	}
	</script>
</body>
</html>
```


Below is the example to add a tooltip on any html element using **Angularjs**

```html
<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.8/angular.min.js"></script>
<style>
#tooltip {
  opacity: 0;
  position: fixed;
  text-align: left;
  padding: 5px;
  font: 14px sans-serif;
  color: #fff;
  background: #333;
  border: 0px;
  border-radius: 2px;
  pointer-events: none;
  z-index: 1099;
}
</style>

<body>
  <div ng-app="myApp" ng-controller="myCtrl">
    <h1 ng-mousemove="showTooltip($event, 'This is tooltip')"
        ng-mouseleave="hideTooltip()">Testing</h1>
    <div id="tooltip"></div>
  </div>
  <script>
  angular.module("myApp", [])
    .controller("myCtrl", function($scope) {
      var tooltip = document.getElementById('tooltip');

      $scope.showTooltip = function(event, label) {
        tooltip.innerHTML = label;
        tooltip.style.left = event.pageX + 'px';
        tooltip.style.top = (event.pageY + 20) + 'px';
        tooltip.style.opacity = 1;
      }

      $scope.hideTooltip = function() {
        tooltip.style.opacity = 0;
      }

    });
  </script>
</body>

</html>
```

