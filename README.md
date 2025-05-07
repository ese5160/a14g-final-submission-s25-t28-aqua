[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/AlBFWSQg)
# a14g-final-submission

    * Team Number: 28
    * Team Name: AQUA
    * Team Members: Xiaopeng Jin & Venkatesh
    * Github Repository URL: https://github.com/ese5160/a14g-final-submission-s25-t28-aqua.git
    * Description of test hardware: Two smart brain

## 1. Video Presentation

Our video is shown below: [https://drive.google.com/file/d/1jQd5UqfU3IZ65V_OIp9Va0QT2mno4pLm/view?usp=sharing](https://drive.google.com/file/d/1jQd5UqfU3IZ65V_OIp9Va0QT2mno4pLm/view?usp=sharing)

## 2. Project Summary
### Device Description:
Our device is a smart water bottle equipped with sensors including temperature, pressure, TDS, and a motion sensor. It monitors hydration behavior and water quality in real time, issuing alerts when no drinking activity is detected and activating UVC purification when water quality drops.

### Inspiration and Problem Solved:
This project was inspired by the need to promote healthier hydration habits and ensure safe drinking water. It addresses the problem of unintentional dehydration and exposure to contaminated water, especially in daily or travel scenarios.

### Internet Integration:
We developed a companion website that allows users to remotely monitor sensor data and the status of multiple bottles, enabling real-time access to water quality and usage behavior through the Internet.

### Device Functionality:
Our smart water bottle uses a microcontroller to collect data from temperature, pressure, TDS, and motion sensors. When no movement or drinking is detected, it sends alerts; if poor water quality is sensed, a UVC LED is triggered for purification.

Sensor data is sent via WiFi to a cloud server, allowing users to monitor bottle status and water quality through a web interface.

### Chanllenges
We faced several issues while integrating all tasks and devices. Conflicts occurred due to timing, shared resources, and communication between sensors and modules, requiring careful coordination to ensure stable performance.

### Prototype Learnings
The earlier you find the question, the easier you can solve it.

### What We Would Do Differently:
Next time, we would plan a more modular architecture from the beginning and use separate communication buses or expanders to reduce hardware conflicts and improve scalability.

### Block diagram

The block diagram is shown below. ![block_system](block_system.jpg)

### Project Links

The link to the node-red: [http://172.172.219.160:1880/ui/#!/0?socketid=9QxPPBkSLHQm8NjbAACb](http://172.172.219.160:1880/ui/#!/0?socketid=9QxPPBkSLHQm8NjbAACb)

The link to our pcb is [https://upenn-eselabs.365.altium.com/designs/6A79DE2D-311E-431D-94FA-BDA6A82B3835](https://upenn-eselabs.365.altium.com/designs/6A79DE2D-311E-431D-94FA-BDA6A82B3835)


## 3. Hardware & Software Requirements

### Hardware

HRS01 (System Composition):
We successfully designed a custom PCB featuring the SAMW25 microcontroller and integrated all required components—temperature sensor, pressure sensor, TDS sensor, vibration motor, fan, and LCD screen. During testing, all components operated as expected and showed no compatibility issues, confirming that the system composition meets the requirement.

HRS02 (Temperature Sensor):
The temperature sensor was tested by comparing its readings with a calibrated digital thermometer at room temperature. The sensor showed excellent accuracy under these conditions, with a measured error margin of only ±0.1°C.

HRS03 (Construction):
We used a BPA-free cylindrical water bottle with a 500ml capacity and designed a custom 3D-printed enclosure to house all electronics. 

HRS04 (Pressure Sensor):
We tested the pressure sensor by gradually injecting water in 10ml increments and observing the sensor's response. Unfortunately, it failed to consistently detect such small volume changes, indicating that the current sensor lacks the necessary sensitivity. This requirement was not met.

HRS05 (Waterproofing):
To ensure safety, we performed immersion and leak tests on the enclosure with the electronics powered off. No water ingress was detected, and all sensitive components remained isolated from moisture. The waterproofing requirement was successfully met.

HRS06 (TDS Water Quality Detection):
The TDS sensor was configured to take readings every 10 seconds. When poor water quality was simulated, the UV LED was activated accordingly. Data logging and LED actuation were verified via serial output, showing that this feature works as expected.

HRS07 (Connectivity):
We measured the voltage and current for each component using a multimeter and confirmed that all devices operate within safe and compatible ranges for both power and GPIO levels. This requirement was satisfied.

HRS08 (LED Indicators):
We included LED indicators that change status based on sensor input and previous user activity. During tests, the LED correctly responded to changing TDS values and use history, fulfilling this requirement.

HRS09 (UV Safety):
While we implemented a software-based mechanism to disable the UV LED when the bottle cap is open, we did not include a dedicated physical cap sensor. As a result, the safety function is only partially automatic and could be improved in future versions. This requirement was partially met.

HRS10 (TFT LCD Display):
The LCD screen was mounted at the base of the bottle and programmed to update temperature and TDS readings every 30 seconds. The display functioned as intended and was clearly visible, meeting the requirement.

HRS11 (Vibration Motor):
The vibration motor was successfully integrated and configured to trigger hydration reminders at fixed intervals. The vibration was noticeable yet not disruptive, ensuring functionality without affecting usability. This requirement was fulfilled.

### Software

SRS01 (Data and Visualization):
We developed a smartphone application that successfully displays real-time data, including hydration status, water temperature, and TDS levels. The app receives this information via Wi-Fi from the SAMW25 microcontroller. During testing, data was displayed promptly and accurately, fulfilling this requirement.

SRS02 (Control):
The application provides users with the ability to configure system settings, including hydration goals, enabling/disabling reminders, and customizing LED notifications. All settings could be updated and applied in real time, confirming that this control functionality was fully implemented.

SRS03 (Data Monitoring and Logging):
We used a cloud-based database (Firebase) to store sensor data such as temperature, TDS, and water usage history. The data was logged with timestamps and could be accessed later for review. This logging feature functioned reliably and meets the requirement.

SRS04 (Hydration Notifications):
The app generates push notifications to remind users to drink water based on set goals and previous usage patterns. We tested this feature by setting short reminder intervals, and notifications were delivered accurately and on time. This requirement was successfully fulfilled.

SRS05 (Water Quality Detection):
The system continuously monitors water quality using the TDS sensor. When the sensor detects a poor water quality level (based on a predefined threshold), the system triggers an alert both in the app and through hardware indicators. The feature was tested with varying water samples and responded appropriately, confirming successful implementation.

SRS06 (Hydration Goal Achievement Feedback):
The app provides dynamic feedback based on the user’s hydration progress. It displays encouraging or congratulatory messages depending on whether hydration goals are missed or achieved. This feature was tested with simulated usage patterns and worked correctly.

SRS07 (UV LED Status Notification):
The current status of the UV LED (active, inactive, or fault) is shown in the app in real time. We tested this by manually toggling the UV LED and simulating purification cycles. The app status matched the hardware behavior at all times, fulfilling the requirement.

SRS08 (UV LED Safety Mechanism):
Although we implemented a function to disable the UV LED when the cap is opened, this safety mechanism currently relies on a software-controlled flag and does not use a physical cap sensor. Therefore, the feature only works under specific user conditions and could be improved in the future. This requirement was partially met.


## 4. Project Photos & Screenshots

Our final project: ![final_project](final.jpg)

Our 2D PCB top ![pcb_top](pcb_top.png)

Our 2D PCB bottom: ![pcb_bottom](pcb_bottom.png)

Our 3D PCB top ![pcb_top](pcb3top.png)

Our 3D PCB bottom: ![pcb_bottom](pcb3bottom.png)

Out thermal photo of boost circuit: ![thermal_boot](thermal_boot.jpeg)

Out thermal photo of buck circuit: ![thermal_buck](thermal_buck.jpeg)

Our front look of nod website: ![node_front](nod_for.png)

Our back look of nod website: ![node_back](node_back.png)  ![nod_back2](nod_back2.png)

Our PCBA front side:![front_side](front.jpg)

Our PCBA bottom side: ![bottom_side](bottom.jpg)

The block diagram is shown below. ![block_system](block_system.jpg)

## Codebase
- The link to the application is [https://github.com/ese5160/final-project-t28-aqua/tree/main/Application](https://github.com/ese5160/final-project-t28-aqua/tree/main/Application)
- 
The link to the bootloader is [https://github.com/ese5160/final-project-t28-aqua/tree/main/Bootloader](https://github.com/ese5160/final-project-t28-aqua/tree/main/Bootloader)

- A link to your Node-RED dashboard code: [http://172.172.219.160:1880/#flow/cb840ed62a0ddb88](http://172.172.219.160:1880/#flow/cb840ed62a0ddb88)


