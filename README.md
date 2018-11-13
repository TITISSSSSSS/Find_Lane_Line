# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

---

**Goals:** Find Lane Lines on the Road

**Tools:** Python and OpenCV

**Techniques :**
* Color Selection
* Image transformation
* Canny Edge Detection
* Hough Transform Line Detection

In this project, i use some test images to build a pipelin and then apply to videos to find lane lines in them.

[//]: # (Image References)
[image1]: ./examples/00images.png "Initial Image"
[image2]: ./examples/gray_images.png "Grayscale Image"
[image3]: ./examples/hls_images.png "hls_images"
[image4]: ./examples/merge_images.png "merge_images"
[image5]: ./examples/canny_images.png "canny_images"
[image6]: ./examples/region_images.png "region_images"
[image7]: ./examples/lines.png "lines"
[image8]: ./examples/line_images.png "line_images"

---
## The step of building pipeline
### 1. Read all test images 
![alt text][image1]
### 2. Covert to grayscale 
**Reflection:** It is hard to tell the difference between white lines and yellow in grayscale images. Besides, grayscale images also easily fail to detect lane lines when there are some shadows due to some trees.

**Solution:** I use color selection techniques to pick White line and Yellow line
![alt text][image2]
### 3. Color selection  
#### Fristly, covert initial RGB image to HSL image
![alt text][image3]
#### Secondly, apply color selection teniques and merge with initial images
![alt text][image4]
#### Reference: https://github.com/naokishibuya/car-finding-lane-lines
### 4. Canny edge detection
* Covert masked hls images to grayscale
* Apply gaussian smoothing with kernel = 5
* Apply Canny function
![alt text][image5]
### 5. Mask region of interest
![alt text][image6]
### 6. Hough transform and Draw line
![alt text][image7]
### 7. Draw extension line

   **Approach:** Firstly, I calculated slope, intercept and length for every hough line segment (left and right) and stroe them into a list. Secondly, I utilized the length of each line segment as weight to calculate the average of slope and intercept. Finally, I use constant y1 and y2 which are relevant to the margin of the mask region and calculate x1 and x2 by using the average slope and intercept.

![alt text][image8]

---
## Videos
**Some results on test videos provided by Udacity:** 
* [solidWhiteRight](./test_videos_output/solidWhiteRight.mp4) 
* [solidYellowLeft](./test_videos_output/solidYellowLeft.mp4) 
* [challenge](./test_videos_output/challenge.mp4) 


