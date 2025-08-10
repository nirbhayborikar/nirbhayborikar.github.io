---
name: KUKA Robot Arm Ball Sorting
tools: [KRL, Color Sorting]
image: https://nirbhayborikar.github.io/assets/gifs/industrial_robot/Sorting.gif
description: Developed algorithm to grasp object with manipulation planning in ROS 2 using PyMoveIt2. Performed SLAM, TF-based localization, and target identification in Gazebo/Rviz; containerized workspace via Docker.TIAGO Robot from PAL Robotics used for testing medical assistant feature.
---
# Industrial KUKA Robot, controling

<br>
<p class="text-center">
{% include elements/button.html link="https://drive.google.com/file/d/13ziPAswNSWEmpfW1nK2dU9DGyQdSlSdv/preview" text="Working video" %}
</p>

## Overview

This project is about generating a successful algorithm for TIAGO Robot arm using PyMoveIt2 to reach any object automatically once the camera detects position of the object with the help of tf transformation.

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/kuka/kuka.png" alt="KUKA Robot" width="400">
</p>


## Key Features

1. **Comprehensive Robot Manipulation and Navigation:**
   - Autonomous navigation in a simulated environment using ROS2 Navigation Stack and SLAM for mapping and localization.
   - Robust AprilTag detection integrated with TF transformations to accurately locate objects and waypoints relative to the robot.
   - Dynamic collision object handling to ensure safe motion planning and prevent collisions during manipulation tasks.

2. **Advanced Pick-and-Place Operation:**
   - Utilizes the PyMoveIt2 framework to control TIAGO’s robotic arm for precise grasping and placing of objects.
   - Real-time pose estimation from AprilTag detections guides arm movement, ensuring accurate object manipulation.
   - Collision-aware motion planning to avoid obstacles, including virtual objects dynamically added to the environment.

3. **Integrated Simulation and Visualization Tools:**
   - Full simulation environment built with Gazebo, featuring realistic objects, rooms, and obstacles.
   - Rviz visualization of robot sensor data, AprilTags, TF frames, maps, and planned trajectories for comprehensive monitoring.

4. **Multi-threaded, Modular Software Architecture:**
   - Uses ROS2 multithreading capabilities for concurrent processes such as motion planning, transformation listening, and navigation feedback.
   - Python-based scripts for high-level control with PyMoveIt2, enabling rapid development and easy integration.

5. **Challenges and Solutions:**
   - Addressed grasp precision and object slipping by fine-tuning gripper control parameters and contact modeling.
   - Managed occasional motion planning failures by refining start states and improving collision modeling.
   - Implemented pre-grasp approach strategies and waypoint navigation to minimize collisions and improve reliability.

6. **Educational Project Context:**
   - Part of an intelligent robotics course project, demonstrating integration of perception, planning, and control for autonomous manipulation.
   - All task action videos and demonstrations are available [here](https://drive.google.com/drive/folders/1ePXDNSp5Fpw2DYeY8WG5IXis6DZvU1pJ/preview).

## Technical Details

- **Development Environment:**
  - Linux OS with Docker containerization for consistent, reproducible ROS2 workspace setup.
  - Core middleware is ROS2, orchestrating control, navigation, and perception nodes within isolated containers.

- **Simulation and Visualization:**
  - Gazebo for 3D environment simulation, including robot movement, sensor emulation, and collision object insertion.
  - Rviz for real-time visualization of robot states, sensor data, TF frames, maps, AprilTags, and planned paths.

- **Perception and Localization:**
  - SLAM for building and localizing within an unknown map using sensor data.
  - AprilTag detection combined with TF2 for precise coordinate transformations and pose extraction.

- **Robot Manipulation:**
  - PyMoveIt2 framework used for high-level arm motion planning and execution with collision awareness.
  - Python scripts handle motion commands, TF data processing, collision object management, and gripper control.

- **Multithreading and Concurrency:**
  - ROS2 MultiThreadedExecutor enables simultaneous execution of callbacks—such as listening for transformations while executing motion plans.
  - This design improves responsiveness and real-time performance in complex robotic tasks.

