---
layout: post
title: "Fake Miniaturization"
date: 2014-12-10
image: /img/city-mini.jpg
---
This was one of the choices for a final project for my [computational photography class](http://inst.eecs.berkeley.edu/~cs194-26/fa14/). It was particularly interesting to me because I used to adore this effect, and have built my own [ghetto tilt-shift lenses](http://cow.mooh.org/projects/tiltshift/diyexamples.html) in the past.

Doing this in Matlab is slightly different. The user draws a box for the focus region, and this part stays in focus. From here, there are two approaches. The first one blurs the rest of the image in bands corresponding to the distance from the focus region. The second (more intelligent) way blurs the image corresponding to a rudimentary depth map, and blurs things that have a different depth (where depths have been binned). The pieces are then blended together using a Gaussian mask.

I tried out both approaches, but the final interface that I built used the second one; though the first one is much simpler, it didn't perform very well on some images and focus regions. Especially with a thin focus region, it would tend to overblur sections of the image.

Check out the full results on our [final webpage](https://inst.eecs.berkeley.edu/~cs194-26/fa14/upload/files/projFinalUndergrad/cs194-fr/howard_nguyen_jason_won_final/tilt-shift.html), or view more information about the project [here](http://graphics.cs.cmu.edu/courses/15-463/2010_spring/hw/proj2/index.html)!
