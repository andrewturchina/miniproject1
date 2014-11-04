ME495 Tag Tracking
========================

![Image](http://www.qrstuff.com/images/sample.png)

## Mini Project 1

This is a project from ME495: Embedded Systems in Robotics. In this project, a variety of pre-existing packages for tracking objects using a single monocular camera. We ran experiments to quantifiably and qualitatively compared object tracking packages.


## Checking the hardware

A Logitech HD webcam C310 was used in this demonstration. Any camera driver node satisfying the [standard ROS camera interface](http://wiki.ros.org/image_pipeline#Hardware_Requirements) could be used. The [usb_cam package](http://wiki.ros.org/usb_cam) is required. 

Let's see where our camera lives:  
	$cd /dev  
	$ls  
Now identify your camera, hint it will be in the form video*. You may need to run the command above before and after the usb is inserted.

Let's test the video output of our webcam:  
	$rosrun usb_cam usb_cam_node _video_device:=/dev/video*  
	$rosrun image_view image_raw image:=/usb_cam/image_raw

## Calibrate the camera

###Austin insert steps Need a checkerboard pattern
Using the checkerboard, you will run through the [monocular calibration tutorial](http://wiki.ros.org/camera_calibration/Tutorials/MonocularCalibration)

###Austin do we need to add any steps here other than follow tutorial? pictures

## Packages used

[ar_sys](http://wiki.ros.org/ar_sys)  
[visp_auto_tracker](http://wiki.ros.org/ar_sys)  
[ar_pose](http://wiki.ros.org/ar_sys)  
[ar_track_alvar](http://wiki.ros.org/ar_sys)  

You will need to either install the package if it has been released or clone it from github.



## Quantifiable results

**Pose estimate noise**

**Tracking distance**

**Marker size**

**Camera frequency**



## Quantitative results

**Ease of use**

**Light sensitivity**

**Marker orientation**

**Lost markers**

**Multiple tags**


## Installation of tag tracking packages

**ar_sys**

**visp_auto_tracker**

**ar_pose**

**ar_track_alvar**




## Resources and Notes


