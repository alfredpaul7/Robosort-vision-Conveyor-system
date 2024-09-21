
# Robosort Vision Conveyor System

## Overview
The **Robosort Vision Conveyor System** is an automated system that integrates a 5-DOF (Degrees of Freedom) 3D-printed robotic arm, computer vision, and machine learning to identify and sort objects being manufactured and transported via a conveyor system. By leveraging machine learning and computer vision, the system is able to recognize different objects and place them into predefined slots based on their classifications.

## Features
- **Object Detection**: The system uses machine learning models to detect and classify objects on the conveyor belt.
- **Robotic Arm Sorting**: A 5-DOF robotic arm, 3D printed and controlled by servos, picks up the classified objects and places them into designated slots.
- **Computer Vision**: An ESP32-CAM module captures the real-time video feed for object detection and recognition.
- **Conveyor System**: The objects move along a conveyor belt, where they are detected, classified, and sorted.
- **Edge Impulse Integration**: Object detection models are trained and deployed using Edge Impulse, enabling accurate and real-time classification.

## Technologies and Components Used
- **Programming Language**: C++ for logic and control of the robotic arm, conveyor, and sensor systems.
- **Computer Vision**: ESP32-CAM module for real-time video feed and object detection.
- **Machine Learning**: Object detection and classification via Edge Impulse software.
- **Microcontroller**: Arduino for controlling the servo motors, sensors, and conveyor system.
- **Sensors**: IR sensors for detecting the presence of objects on the conveyor.
- **Robotic Arm**: 5-DOF 3D-printed robotic arm controlled by servo motors.
- **Servo Motors**: Used for controlling the movements of the robotic arm.
- **3D Printed Components**: The robotic arm structure is custom-designed and 3D-printed for precise object sorting.
  
## Components List
- **ESP32-CAM Module**: For capturing video of objects on the conveyor belt.
- **Arduino**: Central controller for the system, managing servos, sensors, and communication.
- **IR Sensor**: To detect objects passing on the conveyor belt.
- **Servo Motors**: Control the 5-DOF robotic arm for picking and placing objects.
- **3D Printed Robotic Arm**: A custom-made robotic arm used to perform pick-and-place operations.
- **Conveyor Belt**: A system that moves objects to the detection zone for classification.
  
## System Architecture
1. **Object Detection**: The ESP32-CAM captures images of the objects as they move on the conveyor. The images are fed into a machine learning model trained via Edge Impulse to classify the objects.
2. **IR Sensor**: An IR sensor detects the presence of objects on the conveyor belt and triggers the vision system to analyze them.
3. **Classification**: Using computer vision and machine learning, the system identifies and classifies objects.
4. **Robotic Arm Sorting**: Based on the classification, the 5-DOF robotic arm picks up the object and places it into the appropriate slot.
  
## Setup Instructions
### Hardware Setup
1. **Assemble the Robotic Arm**: 3D print the parts of the robotic arm and mount the servos in the correct locations.
2. **Conveyor System**: Set up a motorized conveyor to move objects to the detection area.
3. **Wiring**: Connect the ESP32-CAM, Arduino, IR sensors, and servo motors as per the circuit diagram (to be provided).
4. **Mount Components**: Attach the camera, sensors, and robotic arm in the correct positions relative to the conveyor belt.

### Software Setup
1. **Arduino IDE**: Use the Arduino IDE to upload the necessary control code for the servo motors, IR sensors, and conveyor system.
2. **Edge Impulse**: Train a machine learning model to classify objects and deploy it on the ESP32-CAM module for real-time object detection.
3. **Control the System**: Once deployed, the system will detect objects, classify them, and control the robotic arm to sort them into the appropriate slots.

## How It Works
1. **Object Detection**: As objects move along the conveyor, the ESP32-CAM captures images and feeds them into the machine learning model, which detects and classifies the objects.
2. **IR Sensor Trigger**: The IR sensor triggers the object detection process as the object enters the detection zone.
3. **Classification and Sorting**: Based on the classification results, the robotic arm picks up the object and places it into the corresponding slot.
4. **Real-Time Operation**: The entire process is automated, running in real-time as objects are detected and sorted.

## Circuit Diagram
(Circuit diagram coming soon)

## Future Enhancements
- **Multi-object Classification**: Extend the system to classify and sort more types of objects.
- **Larger Conveyor System**: Upgrade to a larger conveyor system for industrial applications.
- **Advanced Machine Learning Models**: Improve object classification accuracy by training more advanced models.

## Conclusion
The **Robosort Vision Conveyor System** integrates modern technologies like machine learning, computer vision, and robotic automation to create an efficient and scalable object sorting system. This project demonstrates the power of combining 3D printing, robotics, and AI for smart manufacturing solutions.
