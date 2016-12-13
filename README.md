# Website Performance Optimzation

### Overview

As a part of [Udacity's](http://www.udacity.com) Front-end Web Developer Nanodegree I was challenged to optimize a website created by course developer *Cameron Pittman* that contained many performance-related issues. 

### Getting Started

##### Original

Cam's original live version can be found [here](http://cameronwp.github.io/udportfolio/)
This is a link to the GitHub [repo](https://github.com/udacity/frontend-nanodegree-mobile-portfolio)

##### Optimized

My optimized version is linked [here](https://megdollar.github.io/Pizzeria_portfolio/)
This is a link to my GitHub [repo](https://github.com/megdollar/Pizzeria_portfolio)

### Optimization

#### Index Page

The index page orginially had a [Google Page Speed Insights](https://developers.google.com/speed/pagespeed/insights/) score of 28/100 mobile and 30/100 desktop. After implementing the following optimizations I was able to achieve a score of 93/100 on mobile and 94/100 on desktop.

###### JavaScript
Minified the Javascript using this [tool](https://javascript-minifier.com/) and added the [async](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script) attribute to all script tags.

###### CSS
Minified the CSS using this [tool](https://cssminifier.com/) and inlined it as well. Added the `media = "print"` attribute to the external print style sheet linked. 

###### Images

Large images were compressed and re-sized using this [site](http://www.imageoptimizer.net/Pages/Home.aspx).

###### Font

Removed the link to Google Fonts and instead applied the font style directly in the CSS
`body, button, input, select, textarea { font-family: 'Open Sans', sans-serif; color: #333; }`

#### Cam's Pizzeria

There were two major assignments for this page: 
  1. Resize the pizzas in < 5ms 
  2. Achieve a consistent frame rate at 60fps when scrolling
  
###### Resizing the pizzas

Initially the pizzas were resizing at 211.8ms (yikes!). After implementing the following code the pizzas are now resizing at 0.8ms. **See lines 401-452**

###### 60fps

Initialls the average time to generate the last 10 frames was around 60ms, after optimizations this number decreased to about 0.6ms for 10 frames. By utilizing Chrome Dev Tools [Timeline](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/timeline-tool) I was able to track the fps and reduce jank. Specifically changes in the `updatePositions()` function as well as adding a scroll event listener to call the rAF so the animations are requested when scrolling. This [link](https://www.html5rocks.com/en/tutorials/speed/animations/) was a great source. See lines **494-580** for detailed comments of changes.

###### Other Changes to main.js

* `querySelector` and  `querySelectorAll` were replaced with `getElementById` and `getElementsByClassName` which are much faster.
* Several variables were decared and calculated outside of loops where possible to enhance performance.
* Generate 50 pizzas on page load instead of 200 to increase speed 

###### CSS changes

After reading these [tips](https://www.sitepoint.com/introduction-to-hardware-acceleration-css-animations/) the following style attributes were added to the .movers element:
  ```transform: translateZ(0);
  -webkit-transform: translateZ(0);
  will-change: transform, opacity;```
