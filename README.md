
# **Finding Lane Lines on the Road** 

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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I smooth the image by using the GaussianBlur function. Using the smoothed images as inputs, I detect edges in the image by selecting regions with high gradient(Canny method).
To narrow down the edges to lanes, we choose a region in the image where lanes are more likely to appear.  Within this region, we use hough transform to find possible lane segments. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first seperating the left and right lanes. This is done by utilizing the fact that right lane's gradient and left lane's gradient are of different sigh. After lines are grouped into right lane and left lane, I calculate their average parameters. With lanes' parameters, I can calculate the start points and end points of the lanes which can be used to draw the lanes.




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the cure lane marks occurs(as in the challenge video), the average approximation becomes bad.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to fit lane parameters in hough space so that the system is not limited to just straight lanes.

