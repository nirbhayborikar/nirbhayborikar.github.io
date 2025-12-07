---
name: KUKA Robot Arm – Ball Sorting Automation
tools: [KRL, Industrial Robotics, Simulation, Gripper Control, Sensor Integration]
image: https://nirbhayborikar.github.io/assets/gifs/industrial_robot/Sorting.gif
description: Developed a ball-sorting automation system using KUKA KR robot, gripper, and color-sensor in simulation and on industrial hardware using KRL.
---

# KUKA Industrial Robot – Ball Sorting Automation

## Overview  
As part of a Master's program in Robotics, I worked with industrial robots and developed an automated **ball-sorting system** using a **KUKA KR robotic arm**. The task involved simulation, **KRL programming**, and real robot execution with a gripper and color sensor.

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/kuka/kuka.png" width="600">
</p>

---

## Key Features

### ✅ **Automated Pick-Sort-Place**
- Robot picks balls from a feeding station  
- Reads ball color using a color sensor  
- Places the ball into corresponding pallet position  
- Repeats until feeder is empty or pallet is full  
- Returns safely to **HOME** position

### ✅ **Simulation + Real Hardware**
Simulation environment:

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/kuka/Simulation.jpeg" width="600">
</p>

Top View:
<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/kuka/Simulation2.jpeg" width="600">
</p>

### ✅ **Operation Flow**

1. Move robot to **HOME**
2. Move above feeder → open gripper
3. **PTP** to pick position → **LIN** down → close gripper
4. Move to color sensor → **LIN** down → read digital color signal
5. Move to appropriate pallet position based on color
6. Place ball → return to feeder for next ball
7. Stop when feeder empty or pallet full → go **HOME**

### ✅ **Tools Used**
- KUKA Teach Pendant (KCP/KUKA SmartPad): 

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/kuka/Controller.jpeg" width="600">
</p>

- KRL programming
- Color sensor with digital I/O
- Pneumatic / servo gripper

### ✅ **Speed**
Robot tested at 40–100% operating speed depending on workspace clearance.
Full Operation Video:

Sorting Ball -

<p class="text-center">
  <video controls loop autoplay muted style="max-width: 80%; height: auto;">
    <source src="https://nirbhayborikar.github.io/assets/gifs/industrial_robot/Sorting_Ball_Front.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</p>

Tool Teaching (It's a basic task given to get familiar with Robots) -

<p class="text-center">
  <video controls loop autoplay muted style="max-width: 80%; height: auto;">
    <source src="https://nirbhayborikar.github.io/assets/gifs/industrial_robot/Tool_teaching.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</p>


---

## 🧠 **Challenges & Solutions**
- Color detection timing --> Added delay + signal valid check.
- Precise pallet placement --> Wrote custom pallet indexing function.
- Safe motion --> Used PTP for long moves, LIN for pick/drop accuracy.

---

