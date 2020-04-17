---
layout: post
title: Hand Gesture Recognition 
---

![Web App Demo Hand Gesture](/images/hand-gesture.png)

<p align="center">
	<b>Figure 1: The Web App Demo From My Work</b>
</p>

## Introduction

Participating in the Vacation Summer Research Student (VRES) Program at my university, I am doing the project Social Robot Interactivity Using Verbal/Non-Verbal Methods. This post is going to present about how I propose an approach to this project.

## Approaches

In the context, I was assigned by my VRES mentor to develop a model to detect the thumbs up/thumbs down hand gesture to advance the tablet application on Pepper robot. Personally, my overall approach is using two models for achieving this task. The first model is used to segment the human hands out of the full image and analyse those by the second model to determine the gesture. The first model I chose is **[pretrained Real-Time Neural Networks Hand Detector Using Tensorflow](https://github.com/victordibia/handtracking)**, which was trained on **[Egohands Datasets](http://vision.soic.indiana.edu/projects/egohands/)**, a dataset containing 48 Google Glass video of complex and  first-person interactions between two people. Despite accurately detecting the hand as the image below, its result showed low-quality output hand images and lack of hand keypoints for geometry calculations. For this reason, I have to think about another approach for this project. 

![Hand Detected By SSD Neural Networks](/images/handtracking-jackie-chan.png)

<p align="center">
 <b>Figure 2: The Image Output From SSD Neural Networks</b>
</p>

Next approach, I seached on Github models of hand pose estimation for hand gesture recognition. Hand pose estimation models can provide high-level features such as 2D or 3D keypoints localization based on Neural Networks approach for many purposes such as sign language recognition, object handover in robotics and learning from demonstration. Finally, I found a model **[Hand3D](https://github.com/lmb-freiburg/hand3d)** associated with a paper called **[Learning to Estimate 3D Hand Pose from Single RGB Images](https://arxiv.org/abs/1705.01389)**. This papper demonstrates an approach to learn full 3D hand pose estimation from single color images consisting of three deep neural networks for covering each sub task.

Three deep neural networks mentioned above include three models respectively:

- First model: provides a hand segmentation to localize the hand in the image
- Second model: localize hand keypoints in the 2D images
- Third model: finally derives the 3D hand pose from the 2D keypoints

This particular model segments the location of hand present in the picture and gives 21 various landmarks present in hand in 2D and 3D Cartesian Coordinates. Once we get the landmarks, the next step is build a mechanism to identify the formation it is making and classify the pose accordingly. There are several ways to achieve this such as Neural Networks or Support Vector Machine, I choose the **[Directional orientation and curls of fingers](https://github.com/Prasad9/Classify-HandGesturePose)** as this approach does not need the training data or networks involved, thus having no expensive computation. The Cartesian Geometry is used to estimate the curl and directional orientations of various fingers and predict of hand which matches the best. The curl and directional orientations of fingers can be categorised like:

![Curl of Finger](/images/curl-finger.png)

<p align="center">
 <b>Figure 3: Categories of Curl of Fingers</b>
</p>

![Directional Orientations](/images/oriented-finger.png)

<p align="center">
<b>Figure 4: Categories of Directional Orientation of Fingers</b>
</p>

Each category of curl and directional orientations needs a proportional weight for each finger. For example, if half curl at the middle finger is required instead of full curl or no curl, the weight of half curl is the highest of all in case of middle finger. This method can be customized to identify different hand poses as required (ex: thumbs up/down, I love you,..).

## Deployment

To make the project more easily accessible and well display, I have used the Flask (a web framework using Python) to make a web app demo and web app API as a service to exchange the data with the Pepper robot in our project. The complete code can be be found at my **[forked Github Hand3D](https://github.com/tranquanghuy0801/hand3d)**.

Run these on command line:

<script src="https://gist.github.com/tranquanghuy0801/7a47d58ced8d5684f7b42f0d88ee7e0a.js"></script>

I have deployed a web service for this with the help of my supervisor of VRES program at my university. The link is <http://cloudvis.qut.edu.au/gestureRecognition> (currently unsupported). Try and have fun!!!

If any errors occur with this, send me a Pull Request at Github or my email. I will process that in a short time.

## Conclusion

Thanks you all for reading the explaination of my work. I appreciate any feedbacks for this.

## References

- C. Zimmermann and T. Brox, “Learning to Estimate 3D Hand Pose from Single RGB Images“, ICCV 2017.
- D. Victor, "Real-time hand tracking using SSD on Tensorflow", Github Repository 2017. <https://github.com/victordibia/handtracking>
- <https://github.com/Prasad9/Classify-HandGesturePose>