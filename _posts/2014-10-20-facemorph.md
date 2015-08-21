---
layout: post
title: "Face Morphing"
date: 2014-10-20
image: /img/facemorph.jpg
---

This project was centered around the notion that one can create an accurate morph between two images by cross-dissolving the image colors and warping the image shapes together. In this project, I produced face morphs between different faces, computed the mean face from a set of faces, and created caricatures of ourselves by extrapolating based on different data.

Image shapes were defined manually on each image by selecting features such as eyes, ears, mouth. These features defined a correspondence between pairs of images. After this, I computed the mean of the two point sets, computed a Delaunay triangulation on this mean, and then computed an affine transformation matrix for each triangle from the original to the mean. Finally, I created the actual mean image using an inverse warp. An inverse warp is a little easier than a forward warp because it avoids the issue of missing pixels, and you can just interpolate if your source pixels are fractional.

More information about the project can be found [here](http://inst.eecs.berkeley.edu/~cs194-26/fa14/hw/proj5-morph/index.html), and my writeup with more pictures can be found [here](https://inst.eecs.berkeley.edu/~cs194-26/fa14/upload/files/proj5/cs194-fr/jason_won_proj5/proj5.html).
