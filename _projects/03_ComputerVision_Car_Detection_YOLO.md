---
name: Car_Detection_With_YOLO
tools: [OpenCV, YOLO, Python]
image: https://nirbhayborikar.github.io/assets/images/car/GT_YOLO_DIST.png
description: |
  Car detection and depth estimation using YOLO 11m on the KITTI dataset.
---
# Car Detection With YOLO (Camera-Based, KITTI Dataset)

## Overview
A pretrained deep neural network, **YOLO 11m (You Only Look Once)**, was employed to detect cars and estimate the depth from the camera to the detected cars.  
This report outlines the methodologies adopted, key findings and observations, challenges encountered, outcomes achieved, and the future scope of the project. 

![Car Detection](https://nirbhayborikar.github.io/assets/images/car/GT_YOLO_DIST.png)

---

## Key Features

1. **Comprehensive Car Detection and Depth Estimation**
   - Using a deep neural network model, cars from the environment are detected. The detector performance is evaluated using **Intersection over Union (IoU)**, **Precision**, **Recall**, and **Average Precision (AP)**.  
   - Furthermore, using a **pinhole camera model** and **nearest corner method**, the depth of the car from the camera is calculated.

2. **Algorithm**
   ![Algorithm](https://nirbhayborikar.github.io/assets/images/car/Algorithm.png)

3. **The KITTI Dataset**
   - The KITTI dataset used in this project is a subset comprising 20 stereo images, corresponding ground truth values, including coordinates, and the intrinsic matrices for depth estimation.
   - The labels file in the dataset contains the object type, its ground truth coordinates (x1, y1, x2, y2), and the distance from the camera to the car.
   - Since the original KITTI dataset does not provide fixed distances for the objects, these distances were calculated as ground truth values.  
     The four corners (c1, c2, c3, c4) and four midpoints (m1, m2, m3, m4) were used, selecting the minimum of these eight values as the ground truth distance.

     ![Corner Method](https://nirbhayborikar.github.io/assets/images/car/Center_Method_Ground_Dist.png)

   - The KITTI Dataset also shows how the camera is mounted on top of the vehicle:
     ![Camera Position](https://nirbhayborikar.github.io/assets/images/car/camera_positioned.png)

4. **Choosing the YOLO 11m Model**
   - The YOLOv11 model is the latest iteration in the YOLO series, offering significant improvements in accuracy, speed, and efficiency for computer vision tasks.
   - The YOLOv11m variant was specifically chosen for this project because it provides an optimal balance between processing time and mean average precision (mAP).

5. **Detecting Cars and Drawing Bounding Boxes**
   - Using the YOLO 11m model, the function detects the object "car" and retrieves its coordinates (x1, y1, x2, y2), storing them in a list.
   - These coordinates are used to draw bounding boxes around detected cars, along with their confidence values.
   - The confidence values are subsequently used to calculate Precision and Recall metrics.

     ![Car Detection](https://nirbhayborikar.github.io/assets/images/car/Detecting_the_cars_and_drawing_Bounding_boxes.png)

6. **Evaluation of the Object Detection Algorithm**
   - Ground truth data was loaded, and corresponding green boxes were drawn using polylines.
   - To improve accuracy, detected bounding boxes without corresponding ground truth boxes were removed using the **Intersection over Union (IoU)** metric.

     The first image shows cars detected only by YOLO:  
     ![No Filtering](https://nirbhayborikar.github.io/assets/images/car/Red_only_yolo.png)

     The next image shows filtered detections after ground truth matching:  
     ![Filtering](https://nirbhayborikar.github.io/assets/images/car/green_red_overall.png)

7. **Precision and Recall**
   - IoU values for each bounding box were compared against a threshold (λ = 0.75) to ensure high-quality detections.

     - If IoU ≥ λ → **True Positive (TP)**  
     - If IoU < λ → **False Positive (FP)**  

   - Bounding boxes were sorted in descending order based on confidence values. Precision and Recall were then computed:

     ![Precision and Recall](https://nirbhayborikar.github.io/assets/images/car/Precision_And_Recall.png)

     Output plots:
     ![Precision_And_Recall_AP1](https://nirbhayborikar.github.io/assets/images/car/AP_1.png)  
     ![Precision_And_Recall_AP2](https://nirbhayborikar.github.io/assets/images/car/AP_2.png)

8. **Depth Estimation**
   - Depth estimation uses **similar triangles** and the camera's **intrinsic parameters** (especially focal length `f_y`) along with the **camera height**.  
   - By measuring the vertical position of the car’s base in the image (relative to the principal point), a geometrical ratio determines the car’s distance from the camera.

     ![Depth Estimation 1](https://nirbhayborikar.github.io/assets/images/car/GT_YOLO.png)  
     ![Depth Estimation 2](https://nirbhayborikar.github.io/assets/images/car/GT_YOLO_DIST.png)

9. **Results**
   - A plot was created with **YOLO Depth (m)** on the x-axis and **Ground Truth Depth (m)** on the y-axis.  
   - The results show YOLO’s depth estimation is accurate for objects within ~40 meters, but less reliable beyond 40–70 meters due to camera limitations.

     ![Graph](https://nirbhayborikar.github.io/assets/images/car/graph.png)

10. **Repository**
   - All code snippets, output images, and documentation related to the KITTI Dataset are available here:  
     [GitHub Repository](https://github.com/nirbhayborikar/-Car_detection_and_depth_estimation-_opencv_and_yolo11m)
