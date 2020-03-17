# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps. First, I converted the images to grayscale. Second, I applied Gaussian smoothing to remove some noise. Third, I used Canny algorithm to detect lane lines. Fourth, I masked the region of interest in the image. Fifth, I implemented a Hough Transformation on the edge detected image. Finally, I drew the lines on the edge image.

In order to draw a single line on the left and right lanes, my first attempt at modifying the draw_lines() function was by calculating the slope of each line, and then adding lines with positive slopes to one list, and negative-slope lines to another list. For the y values, I used the same y-values from my vertices used for masking. For x, I calculated the minimum and maximum x-values overall, and used those as the starting x's (i.e., x1) for each of the two lines. Then, I calculated x2 = (y2-y1)/m + x1. Anyway, this gave a good outcome. But it was a little bit wobbly. Then, I checked the forum. Someone put a link that suggested calculation of the fitness line of all points in each group (positive-slop points and negative-slope points). So, I changed my code accordingly. The outcome is a little better than before. But it's not perfect.


![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road becomes curvy 

Another shortcoming could be that even with straight road, it's still not perfect.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use higher order for fitness. For straight road I used a first order, but for a curvy road, maybe a second order should be used.

Another potential improvement could be to play more with parameters.
