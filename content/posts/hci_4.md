+++ 
date = "2023-01-29"
title = "HCI Lab4 - VR Game"
description = "This is about how I created VR Game and the questions that arose during my creation process"
authors = "Xuefeng Wei"
slug = "HCI Lab4"
+++


## 1. Build the VR Game

In this one lab, I created a simple vr game, which is different from a normal unity3D game, it requires the use of virtual reality devices, in my case I used oculus.In order to play VR games, we need to pour in XR related packages, such as XR intreaction toolkit latter XR Foundation and so on, in these packages contain a lot of scripts that have been written in advance for developers to use, it is worth noting that in order to use VR for games, you need to delete the Camera that comes with it, and then create XR Origion as the player

First of all, in order to make the user's game experience stronger, I use the hand instead of the controller as the user's "hand" in the virtual space, and by adding the model, the user's hand is shown as follows.
![截屏2023-01-30 03.41.26.png](https://s2.loli.net/2023/01/30/Zzaech86rXW4TEo.png)

Look, isn't it more realistic!

After creating a realistic hand, we want to interact with the object, which requires the use of ray interaction in XR or direct interaction. Ray interaction is often simpler and more convenient. I only need to add an interactale script to the object, then Interaction and teleeportation can be achieved, as shown in the figure below.
![截屏2023-01-30 03.46.58.png](https://s2.loli.net/2023/01/30/3yJzXTgNiQV5DoM.png)

Finally, I implemented player control, continuous movement, turning and interaction with objects, I experimented with these features in a simple scene and it all worked, here is a demo video.
https://youtu.be/x-4LteGI6TA

## 2. Problem I met durng this lab 
In this one lab, I encountered the problem of not being able to move into the VR game. I found that the problem often occurs due to incorrect package import and not having the Open XR option properly enabled in the project settings. It is also easy to make mistakes when interacting with objects, especially when the object is in a different position in the hand, resulting in a less interactive experience.
