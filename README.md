#Website Performance Optimzation

###Overview

As a part of [Udacity's](http://www.udacity.com) Front-end Web Developer Nanodegree I was challenged to optimize a website created by course developer *Cameron Pittman* that contained many performance-related issues. 

###Getting Started

#####Original

Cam's original live version can be found [here](http://cameronwp.github.io/udportfolio/)
This is a link to the GitHub [repo](https://github.com/udacity/frontend-nanodegree-mobile-portfolio)

#####Optimized

My optimized version is linked [here](https://megdollar.github.io/Pizzeria_portfolio/)
This is a link to my GitHub [repo](https://github.com/megdollar/Pizzeria_portfolio)

###Optimization

####Index Page

The index page orginially had a [Google Page Speed Insights](https://developers.google.com/speed/pagespeed/insights/) score of 28/100 mobile and 30/100 desktop. After implementing the following optimizations I was able to achieve a score of 93/100 on mobile and 94/100 on desktop.

######JavaScript
Minified the Javascript using this [tool](https://javascript-minifier.com/) and added the [async](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script) attribute to all script tags.

######CSS
Minified the CSS using this [tool](https://cssminifier.com/) and inlined it as well. Added the `media = "print"` attribute to the external print style sheet linked. 

######Images

Large images were compressed and re-sized using this [site](http://www.imageoptimizer.net/Pages/Home.aspx).

######Font

Removed the link to Google Fonts and instead applied the font style directly in the CSS
`body, button, input, select, textarea { font-family: 'Open Sans', sans-serif; color: #333; }`


