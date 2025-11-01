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
   - **Driving based on LIDAR (Wall Following):** The robot makes left, right, or stop decisions based on LIDAR distance readings from surrounding walls and obstacles. For example, if the front distance is approximately 0.5 m, the left distance lies between 0.9 m and 1.0 m, and the right distance is greater than 2 m, the robot turns right to locate a wall and begin wall-following. If an object appears very close in front of the robot (e.g., 0.1 m), it stops immediately and resumes motion once the obstacle is removed. In general, the robot continuously avoids obstacles and navigates safely through the environment using this logic. [Follow_Wall_Code](https://github.com/nirbhayborikar/Turtlebot_Navigation/tree/main/wall_follow_with_Lidar/autorace_real/autorace_real).
   
   <p class="text-center">
     <video controls loop autoplay muted style="max-width: 80%; height: auto;">
       <source src="https://nirbhayborikar.github.io/assets/turtlebot/wall.mp4" type="video/mp4">
       Your browser does not support the video tag.
     </video>
   </p>
   
   - **Driving based on Camera Input (Track Following):** Using OpenCV with ROS2, the robot detects track lines from the camera feed and computes an offset for steering. It continuously adjusts its position and automatically corrects its direction when it gets too close to the line. [Track_Following_Code](https://github.com/nirbhayborikar/Turtlebot_Navigation/tree/main/track_lane_detection_navigation_only_camera/track_line_detection_driving/autorace_real/autorace_real).
   

   <p class="text-center">
     <video controls loop autoplay muted style="max-width: 80%; height: auto;">
       <source src="https://nirbhayborikar.github.io/assets/turtlebot/track.mp4" type="video/mp4">
       Your browser does not support the video tag.
     </video>
   </p>

   - Simultaneously detect tunnel sign based on **ROS2 CV bridge module**. It detect sign based on **template matching algorithm** written in **OpenCV**.
   - Once the tunnel sign detected, it drive safely inside the tunnel and navigate to othe pathways.
   - [Detect_Tunnel_Sign_Code](https://github.com/nirbhayborikar/Turtlebot_Navigation/tree/main/enter_tunnel_sign_detection_camera_lidar/tunnel_sign_detection/autorace_real/autorace_real).

3. **Integrated Simulation and Real world:**
   - Full simulation environment built with **Gazebo**, featuring realistic objects, rooms, and obstacles.
   - **Rviz visualization** of turtlebot sensor data, TF frames, maps, and planned navigation.
   - With ssh the Real turtlebot was launched and all the task mention above was performed in real bot also.

4. **Multi-threaded, Modular Software Architecture:**
   - Uses **ROS2 multithreading** capabilities for concurrent processes such as sensor data, transformation listening, and navigation feedback.
  
5. **Educational Project Context:**
   - Part of a Master subject called **Autonomous Robot**. All task code scripts are available here and also the docker files. [Github_Repository](https://github.com/nirbhayborikar/Turtlebot_Navigation).

6. **Development Environment:**
  - Linux OS with **Docker containerization** for consistent, reproducible ROS2 workspace setup.