# **Finding Lane Lines on the Road**
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

# **Finding Lane Lines on the Road**

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

First I ran the pipeline similar to as described in the lesson with the following steps:

1. Convert to Grayscale
2. Blur using gaussian blur
3. Canny edge detection
4. Mask the image to the relevant area
5. Hough transform to identify the lines within the masked image1

Finally I define a special draw_lines function, draw_average_lines. This method determines the least squares fit of the lanes. The lanes are selected by simply looking for identified lines with slopes with an absolute value between .3 and .8

Then I use this least squares fit to extrapolate where the values are, drawing from the bottom of the image to where the lines intersect at the top.
<!--
If you'd like to include images to show how the pipeline works, here is how to include an image:

![alt text][image1] -->


### 2. Identify potential shortcomings with your current pipeline


There are a few lines where I am unable to identify where they sit at the bottom of the image. For these, I just use a default value, which isn't great. I ran into this with the videos. It only happens on one or two frames.

Another problem I have is that I assume the lines in front of me are straight. While lanes are generally straight, it is evident in the challenge at the end of the file that my code doesn't work with a non-centered camera on a curve.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to generalize the fit to higher degree polynomials.

Another potential improvement could be to add the ability to recognize lines reliably when they are not in the expected part of the image. Due to the masking, the code doesn't work well unless the camera is in the center of the lane.
