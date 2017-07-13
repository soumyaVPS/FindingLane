#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

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

My pipeline consisted of 5 steps. 
1. I converted the images to grayscale, 

2. Applied gaussianblur to get a smooth image from the grayscale.

3. Applied canny edge detection on the gaussianblurred image to obtain a line image.

4. Chose/masked the edge image to a triangular region (0,h)-(w/2,h*0.58)-(w/2,h *0.58)-(w,h) of interest. 

5. Applied hough transform on the masked triangular region to obtain a list of lines that include the lines corresponding to lanes(broken lines). Updated draw_lines to join 2 lines if they have the same slope to get a contiguous line when lanes markings are broken. Obtained a line image of potentially only the lanes.

6. Blended the line image on top of the original image using weighted_image function.
 


![alt text][]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

A color change in road would be shown as a lane markings. As observed when runnint the challenge video, the car hood or the wipers also get drawn over.


###3. Suggest possible improvements to your pipeline

Play with blurring to make the road color change seemless.
triangulate a region of interest that does not include the hood and wipers
