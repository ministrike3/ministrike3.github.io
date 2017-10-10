---
layout: post
title: "What is A Sobel Operator?"
tag: [Computer Vision, OpenCV]
category: [Computer Vision]
---
### What is A Sobel Operator?
A Sobel Operator, or Sobel Filter, is a function that can be applied on an image to detect edges.



***

### How does it work?
A Sobel Operator is a  discrete differentiation operator, computing an approximation of the gradient of the image intensity function.

It has 2 masks/kernels: one to detect horizontal edges, and one to detect vertical edges.

Essentially you take the initial image, take a point, put the 3x3 mask on top of the 3x3 grid containing the point ,compute the matrix multiplication, and the output is a crude approximation of the gradient of the image intensity function at that point.

An image gradient is a directional change in the intensity or color in an image. The image intensity function is the gradient of a two-variable function (in this case the x and y of the image), and the Sobel operator is a relatively simple, computationally inexpensive, albeit rough approximation of this gradient.

Here is an example of a sobel edge detector that worked well:

![My helpful screenshot]({{ site.url }}/public/posts/Sobel/valveOriginal.png){: .center-image }

![My helpful screenshot]({{ site.url }}/public/posts/Sobel/valveSobel.png){: .center-image }

An Example of one that didnt work well will follow shortly!
