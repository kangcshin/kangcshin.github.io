---
title: 'Lane Line Detection'
subtitle: 'A pipeline to identify the lane boundaries in a video from a front-facing camera on a car.'
date: 2019-11-16 00:00:00
description:
featured_image: 'images/lane-finding/car_lanes.jpg'
---

![](/images/lane-finding/lane-finding.gif)

## Overview
The steps of this project are the following:
* Compute the camera calibration matrix and distortion coefficients with a set of chessboard images.
* Apply a distortion correction to raw images.
* Use color transforms, gradients, etc., to create a thresholded binary image.
* Apply a perspective transform to rectify binary image ("birds-eye view").
* Detect lane pixels and fit to find the lane boundary.
* Determine the curvature of the lane and vehicle position with respect to center.
* Warp the detected lane boundaries back onto the original image.
* Output visual display of the lane boundaries and nuemerical estimation of lane curvature and vehicle position.

#### Tech Stack
* Python
* NumPy
* OpenCV

### Camera calibration using chessboard images
A set of chessboard images photographed at different angles were used for this purpose. 
![](/images/lane-finding/1.png)

There are two types of distortion in this set of calibration images.

| Tangential    | Radial           |
|:-------------:|:-------------:|
| ![](/images/lane-finding/calibration2.jpg)     | ![](/images/lane-finding/calibration1.jpg)|
| ![](/images/lane-finding/tangential_distortion_formula.png)     | ![](/images/lane-finding/radial_distortion_formula.png)      |

So for each image path:
* image is converted to grayscale using `cv2.cvtColor`
* chessboard corners are found using `cv2.findChessboardCorners`

Once the chessboard corners are found, `cv2.calibrateCamera` is called to obtain the calibration value that will be used to undistort our video images. 

### Distortion correction
Using `cv2.undistort`, the chessboard images can be undistorted.
![](/images/lane-finding/2_undistort.png)


## See it in Action

<iframe width="1905" height="763" src="https://www.youtube.com/embed/ng9edgddoms" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>