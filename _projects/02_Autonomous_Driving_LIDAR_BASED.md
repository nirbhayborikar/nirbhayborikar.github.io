---
name: Autonomous Driving, Lidar Based
tools: [ROS2, Nav2, Linux, CV, Image_Template]
image: https://nirbhayborikar.github.io/assets/gifs/track_following_Autonomous_Robot.gif
description: Developed algorithm to navigate in the environment using ROS2, Nav2, Computer Vision. Performed SLAM of the environment, drive based on LIDAR data input. Used CV Bridge for tracking lane with camera via template matching in OpenCv, also used camera for tunnel sign detection and then navigating in tunnel. Small autobot called turtlebot is used for all the operation.
---
# Autonomous Driving With Turtlebot, (LIDAR & Camera Based)

<br>

<!-- <p class="text-center">
{% include elements/button.html link="https://drive.unnel.com/file/d/1mgIZ6jfwOep7Z3avsALZiHS2C05CURlU/preview" text="Working video" %}
</p> -->

## Overview



![Turtlebot](https://nirbhayborikar.github.io/assets/images/Turtlebot_Arena.png)

## Key Features

1. **Comprehensive Robot Navigation:**
   - Autonomous navigation in a real and simulated environment using ROS2 Navigation Stack, SLAM for mapping and localization, and based on LIDAR and camera data.
   - Robust obstacle avoidance via LIDAR sensor developed.

2. **Advanced Operations:**
   - Driving based on LIDAR, the bot turn left right based on the distance of wall from the sensor. For example: If front distance is 0.5m and left distance is in between 0.9 to 1.5 , and the right distance more than 2 m then the robot will take turn on right and try to find wall and start following it. [Follow_Wall_Code](https://github.com/nirbhayborikar/Turtlebot_Navigation).
   
   ![Execution_Video](https://nirbhayborikar.github.io/assets/gif/Autonomous_Robot_Turtlebot_wall_follow.gif).
   
   - Driving based on only camera input, such as track following (driving in between the track lines), OpenCv is used with ROS2 to detect the track lines color and then adjusting position of frame the robot should follow that is collecting by camera, and from the line some offset also given, and also it auto adjust when it get close to track lines.

   ![Turtlebot_Track_Following](https://nirbhayborikar.github.io/assets/gif/track_following_Autonomous_Robot.gif)

   - Simultaneously detect tunnel sign based on ROS2 CV bridge module. It detect sign based on template matching algorithm written in OpenCV.
   - Once the tunnel sign detected, it drive safely inside the tunnel and navigate to othe pathways.

3. **Integrated Simulation and Real world:**
   - Full simulation environment built with Gazebo, featuring realistic objects, rooms, and obstacles.
   - Rviz visualization of turtlebot sensor data, TF frames, maps, and planned navigation.
   - With ssh the Real turtlebot was launched and all the task mention above was performe in real bot also.

4. **Multi-threaded, Modular Software Architecture:**
   - Uses ROS2 multithreading capabilities for concurrent processes such as sensor data, transformation listening, and navigation feedback.
  
5. **Challenges and Solutions:**
   - Addressed grasp precision and object slipping by fine-tuning gripper control parameters and contact modeling.
   - Managed occasional motion planning failures by refining start states and improving collision modeling.
   - Implemented pre-grasp approach strategies and waypoint navigation to minimize collisions and improve reliability.

6. **Educational Project Context:**
   - Part of a Master subject called Autonomous Robot.  All task code scripts are available here and also the docker files. [Github_Repository](https://github.com/nirbhayborikar/Turtlebot_Navigation).

## Technical Details

- **Development Environment:**
  - Linux OS with Docker containerization for consistent, reproducible ROS2 workspace setup.
  