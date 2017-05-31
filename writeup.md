# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

The overview of my pipeline is as follows:
1. Convert the image to grayscale
2. Use Gaussian smoothing to remove noise
3. Apply Canny algorithm to detect edges
4. Apply a hard-coded region of interest mask to filter out uninterested area 
5. Use Hough Transform to detect line segments in the ROI
6. Separate line segments by their slopes
7. Reject outliers according to their Z scores of slopes
8. Extrapolate lines to form a single solid left line and a single solid right line
9. Draw the above two lines onto the image

The single left/right line segment is the average postion of the detected line segments.

The step 7 is crucial to handle the second video (i.e. solidYellowLeft.mp4). My original code used a predefined slope to reject outliers, but I do not like anything that is hard-coded. So I googled and found the modified Z score, which is one of apporaches to detect outliers in statistics. I chose it because it can handle small samples properly. 


### 2. Identify potential shortcomings with your current pipeline

There are several shortcomings of my pipeline. First, it cannot handle the curved lane markings at all. It failed the challenge miserably.

Another shortcoming is the hard-coded region of interest. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to detect the vanishing point and use it to create the region of interest.

Another potential improvement could be to employ some curve-fitting techniques to work with the challenge video.
