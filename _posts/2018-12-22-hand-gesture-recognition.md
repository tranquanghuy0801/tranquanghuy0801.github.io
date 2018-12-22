---
layout: post
title: Hand Gesture Recognition 
---

![Web App Demo Hand Gesture](/images/hand-gesture.png)

Participating in the Vacation Summer Research Student (VRES) Program at my university, I am doing the project Social Robot Interactivity Using Verbal/Non-Verbal Methods. This post is going to present about how I propose an approach to this project.

In the context, I was assigned by my VRES mentor to develop a model to detect the thumbs up/thumbs down hand gesture to advance the tablet application on Pepper robot. Personally, my overall approach is using two models for achieving this task. The first model is used to segment the human hands out of the full image and analyse those by the second model to determine the gesture. The first model I chose is **[pretrained Real-Time Neural Networks Hand Detector Using Tensorflow](https://github.com/victordibia/handtracking)**, which was trained on **[Egohands Datasets](http://vision.soic.indiana.edu/projects/egohands/)**, a dataset containing 48 Google Glass video of complex and  first-person interactions between two people. Despite accurately detecting the hand as the image below, its result showed low-quality output hand images for the next step processing as the input image is about 240 x 240 pixels. For this reason, I have to think about another approach for this project. 

![Hand Detected By SSD Neural Networks](/images/handtracking-jackie-chan.png)

Next approach, I seached on Github models of hand pose estimation for hand gesture recognition. To explain, hand pose estimation is to localize 2D or 3D keypoints on hands based on Neural Networks approach for many purposes such as sign language recognition, object handover in robotics and learning from demonstration. Finally, I found a model associated with a paper called **[Learning to Estimate 3D Hand Pose from Single RGB Images](https://arxiv.org/abs/1705.01389)**. This papper demonstrates an approach to learn full 3D hand pose estimation from single color images consisting of three deep neural networks for covering each sub task. 
