# **Finding Lane Lines on the Road**

## Writeup

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[original]: ./writeup_images/original.png "Original"
[gray]: ./writeup_images/gray.png "Grayscale"
[blur]: ./writeup_images/blur.png "Gaussian Blur"
[canny]: ./writeup_images/canny.png "Canny"
[masked]: ./writeup_images/masked.png "Masked"
[lines]: ./writeup_images/lines.png "Lines"
[final]: ./writeup_images/final.png "Final"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consists of X steps, but firstly the image comes in as standard 3 channel rgb image.

![original]

#### Step 1: Grayscale image

The first step is to grayscale the image to make it easier to find the edges.

![gray]

#### Step 2: Blur image

Next, I blur the image using a guassian blur to remove all the insignificant detail of the image, again this is to make it easier to find the edges.  (It's kind of hard to see in the image below, but if you look closely it's there)

![blur]

#### Step 3: Canny Transform

Thirdly, A Canny Transform is applied to the image to extract the edges.

![canny]

#### Step 4: Mask image

A mask is then applied to the image to remove all data not pertaining to the lane lines.

![masked]


#### Step 4: Extract lines

Next, a Hough Transform is applied to convert the edges to line segments, these line segments are then separated based on their slope into right & left groups, these groups are then averaged and extrapolated to come up with the two lane lines.

![lines]

#### Step 5: Overlay lines

Finally, the lines are overlayed onto the original image.

![final]

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be the lack of support for any sort of curved lane lines.

Another shortcoming could be that if the lane lines aren't distinct enough they may not be picked up by the edge detection.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be ignore the outliers of the line segments whether they are much shorter than other lines or pointing in a drastically different direction they're probably something else that's being misclassified & should be ignored.

