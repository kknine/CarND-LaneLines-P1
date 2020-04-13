# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline

My pipeline consisted of 8 steps:
* Convert the image to grayscale
* Use Gaussian Blur
* Use Canny Edge Detection
* Mask the image using a triangle
* Detect line segments using Hough Line Transform
* Sort the segments into the ones belonging to the left and right lane based on the slope
* Take the endpoints of the segments and interpolate them with a line (using np.polyfit)
* Draw the lines on the image

I experimented with using a quadrilateral instead of a triangle for masking. However, I recognised that the detection becomes better the thinner the trapezoid gets. Eventually the triangle did a better job than all previous quadrilaterals.

I decided to use np.polyfit as it enables me to both "average" the segments drawn and extrapolate the lines further.

### 2. Identify potential shortcomings with your current pipeline

One of the shortcoming that I noticed on the challenge video is that the parameters I am currently using might be too restrictive and there are part of the video when no line is detected.

Another disadvantage of the current pipeline is that the line drawn has a lot of noise. It means it appears to be slighly jiggling from frame to frame.

Another shortcoming of the current approach is the fact that it only deals with straight lines. It cannot deal with curved lines.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to adjust the parameters so the algorithm can detect lines in a variety of conditions. Another one would be to smooth the lines by, for instance, averaging the lines in a few consecutive frames.
