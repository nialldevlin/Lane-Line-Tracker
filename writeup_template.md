# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/lines_detected.png "Detected lines"
[image2]: ./examples/lines_example.png "Example image"

---

### Reflection

### 1. Pipeline
My pipeline starts with a color image of lane lines and follows these steps.
1. Convert to grayscale
2. Blur the grayscale image with gaussian blur function
3. Detect edges with the canny function
4. Mask the image to the region of interest, ignore anything not in the area of interest
5. Find lines with the hough lines function
  Within the hough lines function I added code to sort the line segments generated into left and right lanes, then average the lines and find an equation that defines the lane. It extends this equation to cover the area included in the region of interest.
6. The function draws the lines on the canny filtered image

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

The algorithm sometimes has trouble with dotted lines and identifies them as a much more shallow line across the image. It also breaks down with curved lines.


### 3. Suggest possible improvements to your pipeline
In the intro to self driving cars nanodegree, I implemented a simple "smart thresholding" algorithm that adjusts thresholds for various values to fit each image. This lane line tracker could use a similar function to better identify lane lines.

A more robust line fit could be used to fit the resulting line to the line segments produced from the hough lines transform.
