# **Finding Lane Lines on the Road** 

## Writeup 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[imageCurve]: ./test_results/Marked_hallenge004.jpg "Grayscale"
[imageGood]: ./test_results/Marked_solidYellowCurve2.jpg "Grayscale"

---

### Reflection

### 1. Pipeline Description. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
First, I converted the images to grayscale, then I image is smoothed using Gaussian Blur. Canny Edge detection follows it, to get the image with differential lines.
Once we have image with edges, we will zoom into the part of image defined by vertices, where we expect lanes to occur, followed by Hough Transform to draw the lines. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function. First, the plane is divided into two portion where Left  and Right lines of a Lane might be expected. The Slope is used to enhance the mapping of a line into left or right region or to ignore the line. Using these line co-ordinates, linear equation is derived, which represents the Left and Right line of the lane. Keeping fixed Y, X is driven and lines are drawn on both side of lane. 

This lined image is then used to overlay the lines over the base image.
imageGood


### 2. Shortcomings 
1. Y co-ordinates are fixed, these shall be dynamically identified so that longer or shorter lines can be drawn.
2. Curves need to be identified
imageCurve

### 3. Possible improvements 
1. Dynamically identify the region 
2. To detect curves in the road, slope handling shall be improved. On curves, -ve slope could occur on Right Line and vice versa, this handling shall also be added.