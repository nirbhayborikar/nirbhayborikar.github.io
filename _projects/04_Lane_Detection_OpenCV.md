---
name: Lane Detection, Autonomous Driving OpenCV
tools: [OpenCV, Python]
image: https://nirbhayborikar.github.io/assets/gifs/lane_video/output_lane_detection.gif
description: Real-time lane detection system for autonomous driving using classical computer vision techniques.
---

# 🚗 Lane Detection – Autonomous Driving (OpenCV)

<br>

## 📌 Overview

This project implements a **real-time lane detection system** using **OpenCV**, designed for autonomous driving applications.  
The pipeline combines **feature extraction**, **Hough line detection**, and **lane-line optimization** to produce clean, stable lane boundaries from dashcam footage.

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/gifs/lane_video/output_video.png" alt="Lane Detection Output" style="max-width: 90%;">
</p>

---

# 🧠 1. Pre-Processing & Feature Extraction

This stage prepares the raw video frame for reliable lane detection by reducing noise, extracting edges, and isolating the road region.

### **🔹 Canny Edge Detection – `Canny_image_with_plot.png`**  
This image shows how the Canny algorithm converts the color frame into a **binary gradient map**, highlighting strong intensity changes.  
It captures high-contrast edges such as:

- Lane markings  
- Road boundaries  
- Horizon & mountains  

This step extracts the essential geometry needed for lane detection.

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/lane_detection/Canny_image_with_plot.png" alt="Canny_Image" style="max-width: 90%;">
</p>

---

### **🔹 Region of Interest Mask – `mask_image.png`**  
A polygonal ROI is applied to keep only the area directly in front of the vehicle.  
It removes:

- Sky  
- Trees  
- Mountains  
- Vehicles  
- Side scenery  

This focuses computation on the **drivable triangle** where lane lines exist.

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/lane_detection/mask_image.png" alt="Mask_Image" style="max-width: 90%;">
</p>

---

### **🔹 Isolated Edges – `isolated_image_bitwise.png`**  
A bitwise AND operation. This leaves **only road-relevant edges**, dramatically reducing noise.  
Only the edges *inside the driving region* survive.

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/lane_detection/isolated_image_bitwise.png" alt="Isolated Edges" style="max-width: 90%;">
</p>

---

# 📐 2. Line Detection & Optimization

After isolating the road edges, the next step is to detect line segments using the Hough Line Transform and convert them into clean lane markers.

### **🔹 Initial Line Segments – `marking_lines.png`**  
This output shows the raw result of **Probabilistic Hough Transform**:  
- Many short, broken line segments  
- Follow the lane markings  
- Accurate but fragmented  

This is typical because lane markings are dashed and can vary in brightness.

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/lane_detection/marking_lines.png" alt="Initial Line Segments" style="max-width: 90%;">
</p>

---

### **🔹 Lane Line Optimization – `optimize.png`**  
All detected segments are:

- Grouped by slope (left lane = negative, right lane = positive)  
- Averaged using linear regression  
- Extrapolated to span the full lane length  

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/lane_detection/optimize.png" alt="Lane Line Optimization" style="max-width: 90%;">
</p>

---

The result:  ➡ Two smooth, continuous **master lane lines** .  
This creates a robust signal for navigation and steering logic.

---

# 🎯 3. Final Integration

This step overlays the results back onto the original video and produces final, visually clean lane boundaries.

### **🔹 Raw Lines on Original Frame – `line_on_real_image_detected.png`**  
All small Hough segments are drawn onto the real frame.  
It is technically correct but:

- Fragmented  
- Visually noisy  
- Sensitive to dashed lines  

This view is great for debugging but not ideal for lane-keeping.

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/lane_detection/line_on_real_image_detected.png" alt="Raw Lines on Original Frame" style="max-width: 90%;">
</p>

---

### **🔹 Final Optimized Lane Output – `optimize_in_main_image.png`**  
The final polished output:

- Two stable, averaged lane lines  
- Clean and consistent  
- Easy for an autonomous system to interpret  
- Supports steering, navigation, and decision-making  

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/images/lane_detection/optimize_in_main_image.png" alt="Final Optimized Lane Output" style="max-width: 90%;">
</p>

---

This is the version used in **real-time driving systems**.

<p align="center">
  <img src="https://nirbhayborikar.github.io/assets/gifs/lane_video/output_lane_detection.gif" alt="Lane Detection Output" style="max-width: 90%;">
</p>
---

# 📁 Repository
  - The code and output images can be clone from this repo: https://github.com/nirbhayborikar/finding_lanes_Autonomous_Driving_OpenCV/tree/main
