# **Finding Lane Lines on the Road** 


**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on the work 

---

### Reflection

### 1. Algo pipeline

My pipeline consisted following steps. 
* First, I converted the images to grayscale
* I also keep the color image for color masking combined with region of interest
* Gaussianblur is peformed on the grayscale image to remove noise.
* Region of interest is selected using a quad as well as color information(Lane should be yellow/white in this case)
* Then Houghline detection is used in the region of interest.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by: 
* checking the slope of the line segements from the hough. The lines segments will be grouped into two arrays 
* Left and right lane is determined by slope value
* then I use numpy.polyfit to fit two lines using all the x and y from each array. 
* the line segments are averaged by least square inside np.polyfit function. 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be in the challenging case, there are quite some false positive lines, and it makes the lane jumps. 


### 3. Suggest possible improvements to your pipeline

* A possible improvement would be to further adjust the parameters of the hough, color masking and region of interest
* Another potential improvement could be to use the video sequence information so that lane cannot jump in between consequent images. 
* it is also possilbe to remove outlier lines using RANSAC or some noise filtering method so that they do not contribute to the final lanes
