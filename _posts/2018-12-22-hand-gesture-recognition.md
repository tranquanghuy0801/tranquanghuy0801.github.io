---
layout: post
title: Hand Gesture Recognition 
---

![Web App Demo Hand Gesture](/images/hand-gesture.png)

Figure 1: The Web App Demo From My Work

Participating in the Vacation Summer Research Student (VRES) Program at my university, I am doing the project Social Robot Interactivity Using Verbal/Non-Verbal Methods. This post is going to present about how I propose an approach to this project.

In the context, I was assigned by my VRES mentor to develop a model to detect the thumbs up/thumbs down hand gesture to advance the tablet application on Pepper robot. Personally, my overall approach is using two models for achieving this task. The first model is used to segment the human hands out of the full image and analyse those by the second model to determine the gesture. The first model I chose is **[pretrained Real-Time Neural Networks Hand Detector Using Tensorflow](https://github.com/victordibia/handtracking)**, which was trained on **[Egohands Datasets](http://vision.soic.indiana.edu/projects/egohands/)**, a dataset containing 48 Google Glass video of complex and  first-person interactions between two people. Despite accurately detecting the hand as the image below, its result showed low-quality output hand images and lack of hand keypoints for geometry calculations. For this reason, I have to think about another approach for this project. 

![Hand Detected By SSD Neural Networks](/images/handtracking-jackie-chan.png)

Figure 2: The Image Output From SSD Neural Networks

Next approach, I seached on Github models of hand pose estimation for hand gesture recognition. To explain, hand pose estimation is to localize 2D or 3D keypoints on hands based on Neural Networks approach for many purposes such as sign language recognition, object handover in robotics and learning from demonstration. Finally, I found a model **[Hand3D](https://github.com/lmb-freiburg/hand3d)** associated with a paper called **[Learning to Estimate 3D Hand Pose from Single RGB Images](https://arxiv.org/abs/1705.01389)**. This papper demonstrates an approach to learn full 3D hand pose estimation from single color images consisting of three deep neural networks for covering each sub task.

Three deep neural networks mentioned above include three models respectively:
- First model: provides a hand segmentation to localize the hand in the image
- Second model: localize hand keypoints in the 2D images
- Third model: finally derives the 3D hand pose from the 2D keypoints
This particular model segments the location of hand present in the picture and gives 21 various landmarks present in hand in 2D and 3D Cartesian Coordinates. Once we get the landmarks, the next step is build a mechanism to identify the formation it is making and classify the pose accordingly. There are several ways to achieve this, I choose the **[Directional orientation and curls of fingers](https://github.com/Prasad9/Classify-HandGesturePose)**. This approach does not need the training data or networks involved. The Cartesian Geometry is used to estimate the curl and directional orientations of various fingers and predict of hand which matches the best. The curl and directional orientations of fingers can be categorised like: 

![Curl of Finger](/images/curl-finger.png)

Figure 3: Categories of Curl of Fingers 

![Directional Orientations](/images/oriented-finger.png)

Figure 4: Categories of Directional Orientation of Fingers

Each category of curl and directional orientations needs a proportional weight for each finger. For example, if half curl at the middle finger is required instead of full curl or no curl, the weight of half curl is the highest of all in case of middle finger. This method can be customized to identify different hand poses as required (ex: thumbs up/down, I love you,..). 

To make the project more easily accessible and well display, I have used the Flask (a web framework using Python) to make a web app demo and web app API as a service to exchange the data with the Pepper robot in our project. The complete code can be be found at my **[forked Github Hand3D](https://github.com/tranquanghuy0801/hand3d)**. 

Run These On Command Line: 
- pip install -r requirements.txt
- python3 app.py (Web App) or python3 app_api.py (Web API and send request later)

If any errors occur with this, send me a Pull Request at Github or my email. I will process that in a short time. 

Thanks you all for reading the explaination of my work. I appreciate any feedbacks for this.



