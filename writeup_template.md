#**Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of 6 steps. 
1. Convert the images to grayscale
2. Blur the images by gaussian blurring
3. Apply Canny transformation to the blurred images to create edge detected images
4. Create masked images only for the area of interest to detect lane lines
5. Apply Hough transformation to the canny images to find the lane lines, and draw lane lines on images
6. Overlay the images with the lane lines on the original images

In order to draw a single line on the left and right lanes, I modified the draw_lines() function as follows.
1. Sum up the line slopes for both left and right lane lines for averaging
2. Calculate the average of the slopes
3. Based on the average of the slopes, calculate the intercepts of the lines
    `y = ax + b --> b = y - ax`
4. Use linear extrapolation to calculate the line end coordinates. Calculate only x coordinate values 
since the top and the bottom of y positions of the lines are fixed
    `y = ax + b --> x = (y - b) / a`


###2. Identify potential shortcomings with your current pipeline

1) Very rarely, the lane lines may not appear on the video for a few frames.
2) The lane lines may be completely off the actual lane lines for a few frames.

###3. Suggest possible improvements to your pipeline

A possible improvement would be to more accurately detect discrete lane lines by optimizing the parameters
of minimum line length and maximum line gap for Hough transformation.

