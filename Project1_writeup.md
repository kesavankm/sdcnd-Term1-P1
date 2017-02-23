#**Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./stage_images/after_grayscale.jpg "Grayscale"
[image2]: ./stage_images/after_gaussian_blur.jpg "Gaussian blur"
[image3]: ./stage_images/after_canny_edge.jpg "Edges"
[image4]: ./stage_images/after_region_masking.jpg "Region masked"
[image5]: ./stage_images/after_hough_transform.jpg "Hough transformation"
[image6]: ./stage_images/after_all_stages.jpg "Final"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 
1. I converted the images to grayscale.
2. I applied Gaussian blur on the image to smoothen the image
3. I applied Canny detection mechanism to detect the edges in the image
4. I applied Region masking constructed with 4 vertices of a polygon. With this I had the lanes edges for the necessary region in-front of the car.
5. using Regression and extrapolation I constructed the connected left lane and right lane based on the various detected left and right lines.
Super imposed the constructed lane image on the original image to derive the Lane line detection. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 
1. Lane line grouping
	For each lines obtained from the Hough transformation, grouped them as left or right lanes. Used slope of the line and position in the image to decide lane group for the line.
2. Extrapolation using Linear regression
    Then with the grouped lines, using linear algorithm, constructed continuous line for the left lane and right lane by calculating both ends of each lane 

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![Grayscale][image1]
![Blur][image2]
![Canny Edge][image3]
![Region masking][image4]
![Hough Transformation][image5]
![Final image][image6]

###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when Roads are curvy. Lane line detection may be incorrect.

Another shortcoming could be Edge detection when barrier is close. Barriers can also be identified as Lane edges


###3. Suggest possible improvements to your pipeline

A possible improvement would be to extend the Lane detection range.

Another potential improvement could be to reduce noise and separate left and right line processing (slope filtering and image processing)
