---
name: Autonomous Driving, Lidar Based
tools: [ROS2, Nav2, Linux, CV, Image_Template]
image: https://nirbhayborikar.github.io/assets/gifs/track_following_Autonomous_Robot.gif
description: Autonomous Driving based on LIDAR data and camera input using Turtlebot with ROS2 stack. Simultaneously performing computer vision task, through ROS2 CV bridge module.
---
# Autonomous Driving With Turtlebot, (LIDAR & Camera Based)

<br>

## Overview

- Developed algorithm to navigate in the environment using **ROS2**, **Nav2**, and **Computer Vision**. Performed **SLAM** of the environment, driving based on **LIDAR data input**. Used **CV Bridge** for tracking lane with camera via **template matching** in **OpenCV**, also used camera for tunnel sign detection and then navigating in tunnel. A small autobot called **Turtlebot** is used for all the operation.

![Turtlebot](https://nirbhayborikar.github.io/assets/images/Turtlebot_Arena.png)

---

## Key Features

1. **Comprehensive Robot Navigation:**
   - Autonomous navigation in a real and simulated environment using **ROS2 Navigation Stack**, SLAM for mapping and localization, and based on LIDAR and camera data.
   - Robust obstacle avoidance via LIDAR sensor developed.

2. **Advanced Operations:**
   - **Driving based on LIDAR (Wall Following):** The bot turns left/right based on the distance of the wall from the sensor. For example: If front distance is $0.5 \text{m}$ and left distance is between $0.9 \text{m}$ to $1.5 \text{m}$, and the right distance is more than $2 \text{m}$, the robot will take turn on right and try to find wall and start following it. [Follow_Wall_Code](https://github.com/nirbhayborikar/Turtlebot_Navigation).
   
   <p class="text-center">
     <video controls loop autoplay muted style="max-width: 100%; height: auto;">
       <source src="https://nirbhayborikar.github.io/assets/turtlebot/wall.mp4" type="video/mp4">
       Your browser does not support the video tag.
     </video>
   </p>
   
   - **Driving based on Camera Input (Track Following):** OpenCv is used with **ROS2** to detect the track lines color and then adjusting position of frame the robot should follow that is collecting by camera, and from the line some offset also given, and also it auto adjust when it get close to track lines.

   <p class="text-center">
     <video controls loop autoplay muted style="max-width: 100%; height: auto;">
       <source src="https://nirbhayborikar.github.io/assets/turtlebot/track.mp4" type="video/mp4">
       Your browser does not support the video tag.
     </video>
   </p>

   - Simultaneously detect tunnel sign based on **ROS2 CV bridge module**. It detect sign based on **template matching algorithm** written in **OpenCV**.
   - Once the tunnel sign detected, it drive safely inside the tunnel and navigate to othe pathways.

3. **Integrated Simulation and Real world:**
   - Full simulation environment built with **Gazebo**, featuring realistic objects, rooms, and obstacles.
   - **Rviz visualization** of turtlebot sensor data, TF frames, maps, and planned navigation.
   - With ssh the Real turtlebot was launched and all the task mention above was performe in real bot also.

4. **Multi-threaded, Modular Software Architecture:**
   - Uses **ROS2 multithreading** capabilities for concurrent processes such as sensor data, transformation listening, and navigation feedback.
  
5. **Educational Project Context:**
   - Part of a Master subject called **Autonomous Robot**. All task code scripts are available here and also the docker files. [Github_Repository](https://github.com/nirbhayborikar/Turtlebot_Navigation).

---

## Technical Details

- **Development Environment:**
  - Linux OS with **Docker containerization** for consistent, reproducible ROS2 workspace setup.