# **Finding Lane Lines on the Road** 

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

To complete the project, two files will be submitted: a file containing project code and a file containing a brief write up explaining your solution. We have included template files to be used both for the [code](https://github.com/udacity/CarND-LaneLines-P1/blob/master/P1.ipynb) and the [writeup](https://github.com/udacity/CarND-LaneLines-P1/blob/master/writeup_template.md).The code file is called P1.ipynb and the writeup template is writeup_template.md 

To meet specifications in the project, take a look at the requirements in the [project rubric](https://review.udacity.com/#!/rubrics/322/view)


Pipeline
---
1. Convert the image to gray scale
2. Apply Gaussian Blur
3. Apply canny edge detection
4. Cut out the ROI
5. Lines detection using Hough algorithm
6. Select lines with reasonable slope and draw on image

Tricks to draw a single line on the left and right lanes
---
1. Filter out all lines that are not with a slope within 20 to 90 degree or -20 to -90 degree.
2. A line with a slope within 20 to 90 degree goes to the right line group, one within -20 to -90 go to the left group.
3. Average the starting points and ending points in each of the right and left group, and calculate the slope according
to the averaged points.
4. Draw line with the information of the slope and an averaged point, for both left and right.

Potential shortcomings
---
If it's really bright on the road, like a segment in the challenge vedio, it's then really hard to detect yellow lines' edges, which would lead to a total failure of finding lane lines. So there would be something to improve, like using another color system like HSV, with which is convinient to filter out the irrelevant colors and only let white and yellow stay.



