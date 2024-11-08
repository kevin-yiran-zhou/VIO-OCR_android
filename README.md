# VIO+OCR for Indoor Localization and Navigation
This project proposes a **Visual-Inertial Odometry (VIO)** based indoor localization solution enhanced by **Optical Character Recognition (OCR)** for room label recognition. By integrating VIO with OCR-based room detection, the system aims to provide accurate indoor localization without relying on additional hardware, making it a cost-effective and robust approach for various indoor settings.

## Key Components:
**1. Visual-Inertial Odometry (VIO):**
Use VIO to estimate device movement by fusing data from the IMU (accelerometer and gyroscope) with visual features from the camera feed.
Calculate relative movement to update the device’s position in real-time, ensuring continuous localization in dynamic indoor environments.

**2. Semantic Mapping with Room Labels:**
Each room is marked with a visible, printed number at the entrance, serving as a unique identifier for that location.
The semantic map stores each room’s label and corresponding coordinates, as well as the relative layout of corridors, exits, and key areas to support efficient navigation.

**3. OCR for Room Number Recognition:**
Utilize OCR to detect and recognize room numbers from the camera feed, identifying the room label directly.
When a labeled room is detected, OCR matches the room number to its corresponding location on the semantic map, recalibrating the VIO-based position to reduce drift.

**4. Localization and Navigation:**
VIO tracks movement, and upon detecting a known room label via OCR, the system recalibrates its position relative to the semantic map.
The map’s relational data (e.g., distances and directions between rooms) supports navigation, allowing the system to suggest routes accurately without requiring complex 3D modeling.

## Timeline: 
**Phase 1: Room Label Recognition**

**1. App for Text Recognition**
- Develop an app to recognize room labels using OCR.
- Set up testing with various room labels to ensure high accuracy.
  
**2. Boundary Detection Improvement**
- Enhance the app to detect room label boundaries, identifying clear boundary boxes.
  
**3. Boundary-Based Relative Positioning**
- Create an algorithm to use the detected boundary to estimate the camera's distance and angle relative to the label.

**Phase 2: VIO and Mapping**

**1. Visual-Inertial Odometry (VIO) Study and Implementation**
- Study VIO principles and techniques.
- Integrate VIO to track movement in real-time.

**2. Enhanced Map Builder**
- Update the map builder to store room label locations and sizes.
- Ensure that the map can handle semantic and spatial data effectively.

**Phase 3: Navigation and System Integration**

**1. Pathfinder Algorithm Enhancement**
- Improve the pathfinder to leverage the enhanced map data, supporting more accurate routing.

**2. Integration and Testing**
- Combine VIO, OCR, and mapping components.
- Conduct comprehensive testing across various indoor settings, focusing on accuracy and robustness.


## Why Choose OCR Over STR for Room Label Detection?
Optical Character Recognition (OCR) is favored over Scene Text Recognition (STR) in this project due to several key factors aligning with the project’s needs:
- **Controlled Environment and Consistent Labels:** Indoor environments typically provide stable lighting and limited variation in text orientation or style, especially when room labels are standardized as black text on white or gray backgrounds. OCR is particularly suited for such high-contrast, simple text layouts, ensuring accurate detection with minimal error.
- **Efficiency and Resource Optimization:** OCR is generally lightweight, requiring fewer computational resources than STR, which relies on deep learning models. This choice is ideal for a mobile application, as it allows real-time processing without heavy power and memory usage, extending device battery life and performance.
- **Rapid Deployment and Ease of Integration:** OCR has well-established libraries and APIs, such as Tesseract and Google Vision, which offer straightforward integration into mobile applications. This simplifies the development and reduces deployment time, making OCR a pragmatic choice for fast, reliable room label detection.
- **Accuracy in Standard Text Layouts:** Since OCR is optimized for printed and well-aligned text, it provides reliable performance in recognizing simple, high-contrast room numbers, reducing the need for STR’s robustness against complex layouts and diverse text orientations.

