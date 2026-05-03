# Robosort Vision Conveyor System (RVCS)

## Automated Robotic Vision System for Shape and Color-Based Object Sorting on a Conveyor using ESP32-CAM and Edge Impulse with a 3D-Printed Robotic Arm

---

## Project Overview

The **Automated Robotic Vision System for Shape and Color-Based Object Sorting on a Conveyor using an ESP32-CAM and Edge Impulse with a 3D-printed robotic arm**, shortly termed as the **Robosort Vision Conveyor System (RVCS)**, is an intelligent automation platform developed for real-time identification, classification, and sorting of objects based on their **shape and color**.

The system combines embedded artificial intelligence, computer vision, robotic manipulation, and conveyor automation by integrating an ESP32-CAM, Edge Impulse, Arduino, and a custom-designed **5-DoF 3D-printed robotic arm**. Objects transported through the conveyor are captured in a designated vision zone, classified in real time using an onboard TinyML model, and automatically sorted into predefined bins using inverse kinematics-based robotic manipulation.

The Robosort Vision Conveyor System demonstrates the interdisciplinary integration of:

- Embedded AI (TinyML)
- Computer Vision
- Robotics
- Additive Manufacturing
- Motion Control
- Industrial Automation
- Smart Manufacturing

providing a scalable solution for next-generation **Industry 4.0 automated sorting applications**.

---

## Project Highlights

- Designed and developed an automated robotic vision system for shape and color-based object sorting on a conveyor using **ESP32-CAM** and **Edge Impulse TinyML**.

- Designed a **5-DoF robotic arm** and conveyor system using **SolidWorks** and fabricated components through **FDM 3D printing (PLA)** with Cura slicing.

- Developed an embedded machine vision pipeline by training a **CNN-based TinyML classification model** using Edge Impulse and deployed it on ESP32-CAM for real-time object classification.

- Transmitted classification results to an Arduino via **UART communication** to control servo motor positions of the robotic arm for automated sorting operations.

---
 
# Features

## 1. Real-Time Object Detection

Captures live images of moving objects using the ESP32-CAM and performs real-time classification.

## 2. Shape and Color Classification

Objects are classified based on:

- Cube
- Cuboid
- Cylinder
- Hexagon
- Parallelogram

with multiple color classes.

## 3. TinyML Edge Deployment

CNN-based TinyML model deployed directly on ESP32-CAM for onboard inference.

## 4. Automated Pick-and-Place

5-DoF robotic arm autonomously sorts classified objects.

## 5. Conveyor-Based Automation

Objects move continuously through the detection zone.

## 6. Inverse Kinematics Motion Control

Joint angles are computed for accurate arm positioning.

θ = f(x,y,z)

## 7. UART Communication

Classification results are transmitted from ESP32-CAM to Arduino.

---

# Mechanical Design

The robotic arm and conveyor assembly were designed using SolidWorks and fabricated using **FDM-based 3D printing with PLA**.

---

## Figure 1: Complete CAD Assembly
<img width="904" height="536" alt="724a5b15-1353-4c9d-b955-33319c63106c" src="https://github.com/user-attachments/assets/e5fd0b9a-9675-4975-9142-4c029d6a7dd3" />
Shows:
- Conveyor system
- Camera mount
- Sorting bins
- Robotic arm
- Electronics mounting

---

## Figure 2: Prototype Hardware Setup

📍 *Insert actual prototype image here*

Shows:

- Fabricated robotic arm
- Working conveyor
- Sorting bins
- Physical implementation

---

# Robotic Arm Specifications

| Joint | Function |
|-------|----------|
| Base | Rotation |
| Shoulder | Vertical movement |
| Elbow | Reach extension |
| Wrist | Orientation |
| Gripper | Object gripping |

---

## Dimensions

- Base Diameter = 120 mm
- Base Height = 100 mm
- Shoulder Link = 160 mm
- Elbow Link = 160 mm

---

## Figure 3: Robotic Arm Dimensions

📍 *Insert robotic arm dimension image here*

---

# Embedded Vision System

The embedded vision system uses an ESP32-CAM mounted above the conveyor capture zone.

The module captures images of moving objects and performs onboard inference.

---

# TinyML Workflow

A complete Edge AI workflow was developed using Edge Impulse.

## Workflow Steps

### 1. Dataset Collection

Images of different shapes and colors were collected.

### 2. Data Annotation

Each object was labeled according to:

- Shape
- Color

### 3. Feature Extraction

Image preprocessing and feature extraction.

### 4. CNN Training

TinyML object classification model.

### 5. Deployment

Model deployed to ESP32-CAM.

---

## Figure 4: Edge Impulse Workflow

📍 *Insert TinyML workflow image here*

---

# Dataset Visualization

Dataset includes:

- Multiple object shapes
- Multiple object colors
- Different lighting conditions
- Different orientations

---

## Figure 5: Feature Explorer

📍 *Insert feature explorer image here*

---

# Model Performance

The trained TinyML model achieved:

- **Validation F1 Score = 66.7%**

The confusion matrix validates classification performance.

---

## Figure 6: Model Performance Metrics

📍 *Insert confusion matrix image here*

---

# System Architecture

```text
Object on Conveyor
       ↓
IR Sensor Detection
       ↓
ESP32-CAM Image Capture
       ↓
TinyML CNN Inference
(Edge Impulse)
       ↓
UART Communication
       ↓
Arduino Controller
       ↓
Inverse Kinematics
       ↓
Servo Motor Actuation
       ↓
5-DoF Robotic Arm
       ↓
Sorting Bin
```

---

# Hardware Setup

## Electronics

| Component | Purpose |
|-----------|---------|
| ESP32-CAM | Vision + Inference |
| Arduino | Motion Control |
| Servo Motors | Joint Actuation |
| IR Sensor | Object Detection |
| DC Motor | Conveyor Drive |
| Power Supply | System Power |

---

## Mechanical Components

| Component | Purpose |
|-----------|---------|
| 3D Printed Arm | Manipulation |
| Conveyor | Object Transport |
| Gripper | Object Gripping |
| Sorting Bins | Object Storage |

---

# Hardware Assembly Procedure

### Step 1

Assemble the 5-DoF robotic arm.

### Step 2

Mount servo motors at each joint.

### Step 3

Install conveyor motor.

### Step 4

Mount ESP32-CAM above the detection zone.

### Step 5

Install IR sensor.

### Step 6

Connect Arduino and power circuits.

---

# Software Setup

Required Software:

- Arduino IDE
- SolidWorks
- Edge Impulse
- Cura

---

# How It Works

## Step 1 — Object Entry

Objects are placed on the conveyor.

## Step 2 — Detection

IR sensor detects object arrival.

## Step 3 — Image Capture

ESP32-CAM captures object image.

## Step 4 — Classification

TinyML model classifies:

- Shape
- Color

Example:

```cpp
BLUE_CUBE
GREEN_CUBOID
WHITE_HEXAGON
```

## Step 5 — Communication

Classification result is sent to Arduino via UART.

## Step 6 — Motion Planning

Arduino calculates joint angles.

## Step 7 — Pick and Place

Robotic arm grips the object and places it into the corresponding sorting bin.

---

## Figure 7: Sorting Operation

📍 *Insert sorting operation image here*

---

# Applications

- Smart Manufacturing
- Warehouse Automation
- Automated Inspection
- Packaging Industries
- Educational Robotics
- Industry 4.0 Demonstrators

---

# Future Enhancements

- Multi-object simultaneous detection
- Higher accuracy CNN models
- ROS2 integration
- Industrial servo motors
- Cloud-based analytics
- Reinforcement learning grasping

---

# Conclusion

The **Automated Robotic Vision System for Shape and Color-Based Object Sorting on a Conveyor using an ESP32-CAM and Edge Impulse with a 3D-printed robotic arm**, termed the **Robosort Vision Conveyor System (RVCS)**, successfully demonstrates the practical implementation of embedded artificial intelligence, computer vision, robotic manipulation, and industrial automation within a compact smart manufacturing platform.

By integrating the ESP32-CAM for real-time image acquisition and onboard inference, Edge Impulse for TinyML model development, Arduino for motion control, and a custom-designed **5-DoF 3D-printed robotic arm**, the system autonomously detects, classifies, and sorts objects based on shape and color with minimal human intervention.

The Robosort Vision Conveyor System establishes a strong foundation for scalable **Industry 4.0 intelligent sorting systems**, with potential applications in smart manufacturing, warehouse automation, automated inspection, and educational robotics.

---
