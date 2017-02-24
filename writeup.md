#**Finding Lane Lines on the Road** 

##Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/gray_solidWhiteCurve.jpg "Grayscale"
[image2]: ./examples/blur_gray_solidWhiteCurve.jpg "Blurred Grayscale"
[image3]: ./examples/edges_solidWhiteCurve.jpg	"Canny edges"
[image4]: ./examples/masked_edges_solidWhiteCurve.jpg "Masked edges"
[image5]: ./examples/lines_solidWhiteCurve.jpg "Lines using hough transformation"
[image6]: ./examples/final_solidWhiteCurve.jpg  "Final"


---

### Reflection

###1. pipeline description.

My pipeline consisted of 5 steps(implemented in process_image method):
* I converted the images to grayscale.
* I applied gaussian blur with kernel size 5.
* I applied canny filter to detect edges on the gaussian blur.
* I selected the edges from portion of image that was of interest to us by applying a polygon filter.
* Finally, detected lines using hough transformation over the edges detected and overlayed on top of the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function to segment the lines as belonging
to left or right lines based on their slope and averaged the coordinates to get the center line and painted the line with 
desired thickness.

Here are the images corresponding to 5 steps above: 

![Gray][image1]
![Blur Gray][image2]
![Canny Edges][image3]
![Masked edges][image4]
![Lines using hough transformation][image5]
![Final][image6]



###2. Potential shortcomings with your current pipeline

* It Doesn't handle the case given in optional challenge at the end of the exercise, 
  my algo fails to detect any lines on the left in 1 of the frames and i didn't handle that case.
* My algo assumes that lines are within certain part of the frame which always won't be the case.
* My algo assumes slopes of lines fall in certain ranges for left and right lines.


###3. Possible improvements to the pipeline

* Make the algo angle of view invariant.
* Make algo work when lines are in shadows, which i am guessing is the problem that my algo is encountering with optional challenge.
* [Tech debt] Reorganize draw_lines() method by extracting formulae as their own helper methods and initialize and document the constants used in
  beginning of the module.