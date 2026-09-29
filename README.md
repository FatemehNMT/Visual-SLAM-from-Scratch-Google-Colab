# Visual SLAM from Scratch — Google Colab

An educational, step-by-step implementation and study project for understanding the core concepts and components of a stereo Visual SLAM system, developed and executed in Google Colab.

This project was developed as a personal learning project alongside the study of *Visual SLAM* and the concepts presented in *slambook2*. Rather than treating SLAM as a black-box system, the goal is to understand how the major components work, how they interact, and how a complete SLAM pipeline is gradually built from the ground up.

---

## 🎯 Project Goal

The main goal of this repository is to study and implement the fundamental components of a Visual SLAM system in a structured and practical way.

The project focuses on understanding:

- Stereo camera geometry
- Feature extraction and matching
- Feature-quality improvement
- Disparity and triangulation
- 3D MapPoint generation
- Map management
- Camera tracking
- Local optimization
- Bundle Adjustment
- Sliding-window optimization
- Marginalization
- Loop Closure
- Pose Graph optimization
- Visualization and debugging of SLAM results

The emphasis is on **understanding the algorithms and their relationships**, rather than simply reproducing an existing implementation.

---

## 🧠 Learning Approach

This repository follows a gradual learning-by-implementation approach.

Each major SLAM component was studied conceptually first and then connected to the corresponding implementation.

The project was developed step by step, with intermediate experiments, debugging, visualization, and verification used to understand how each component contributes to the overall SLAM system.

The implementation and exercises were developed with ChatGPT as part of the learning process. The goal was not only to obtain working code, but to use each implementation step as an opportunity to understand the underlying robotics, geometry, optimization, and C++ concepts.

---

## ☁️ Why Google Colab?

The project is intentionally organized around **Google Colab**.

One of the goals was to make the learning material easily accessible without requiring a specific local computer configuration or a complicated robotics software installation.

Running the project in Colab makes it possible to:

- experiment with the code using a standard web browser;
- avoid lengthy dependency installation on local machines;
- reproduce the experiments on different computers;
- focus on understanding the algorithms rather than system configuration;
- make the learning material easier to share with other students and robotics enthusiasts.

The repository therefore serves both as a personal learning project and as a potentially accessible starting point for others studying Visual SLAM.

---

# 🏗️ Project Structure

The project was developed progressively, following the structure below.

## 1. SLAM Essentials

Before implementing the pipeline, the fundamental concepts required for Visual SLAM were reviewed and organized.

Topics include:

- Coordinate systems
- Camera geometry
- Projection
- Stereo vision
- Feature-based perception
- Motion estimation
- Map representation
- Optimization
- State estimation

---

## 2. Environment Setup

The project was prepared to run in Google Colab.

Main steps include:

- Mounting Google Drive
- Installing required dependencies
- Preparing the project structure
- Preparing documents and folders
- Organizing datasets and input files

---

## 3. Data Preparation

Stereo image data is prepared for the SLAM pipeline.

The preprocessing stage provides the input required for subsequent feature extraction and stereo reconstruction.

---

## 4. Feature Extraction

Visual features are extracted from the stereo image pairs.

The purpose is to obtain stable image features that can subsequently be matched between frames and between the left and right cameras.

---

## 5. Feature Matching

Feature correspondences are established between images.

These correspondences form the basis for:

- stereo reconstruction;
- motion estimation;
- tracking;
- MapPoint creation.

---

## 6. Improving Feature Quality — ROI and Mask

Feature extraction is improved by introducing spatial constraints such as:

- Region of Interest (ROI)
- Masks

The objective is to reduce unsuitable or irrelevant features and improve the quality of the visual measurements used by the SLAM system.

---

## 7. Improving Feature Quality — Angle Filtering

Additional geometric filtering is applied to improve feature quality.

This stage investigates how geometric constraints can be used to reject undesirable feature configurations and obtain more reliable correspondences.

---

## 8. Disparity and Triangulation

Stereo correspondences are converted into 3D information.

The project studies:

- disparity;
- stereo geometry;
- triangulation;
- depth estimation;
- conversion from image observations to 3D MapPoints.

This stage provides the initial geometric structure of the map.

---

## 9. MapPoint and Map

The reconstructed 3D points are organized into a map representation.

The project explores the relationship between:

- Frames
- MapPoints
- Observations
- Camera poses
- The global/local map

---

## 10. Map Visualization

The reconstructed map and camera trajectory are visualized to verify the geometric behavior of the system.

Visualization is used as an important debugging and learning tool rather than only as a final presentation step.

---

## 11. Tracking, Observation and Tracking Preprocessing

The system is extended from isolated stereo reconstruction toward continuous SLAM.

This stage deals with:

- frame-to-frame tracking;
- observations;
- feature correspondences;
- pose estimation;
- tracking preprocessing;
- maintaining the relationship between frames and MapPoints.

The goal is to establish the frontend required for a continuous SLAM pipeline.

---

## 12. Backend and Local Bundle Adjustment

A backend optimization component is introduced and connected to the frontend.

The project studies:

- nonlinear optimization;
- graph-based optimization;
- g2o;
- Bundle Adjustment;
- pose and landmark optimization;
- local optimization.

The backend refines the estimated state using the available observations.

---

## 13. Sliding Window and Marginalization

The project then moves toward an incremental optimization framework.

The sliding-window approach is studied to keep optimization computationally manageable while retaining recent information that is important for accurate state estimation.

Marginalization is studied as a mechanism for removing older variables from the active optimization problem while preserving their information through the resulting prior.

This stage provides a conceptual bridge between local optimization and a more complete incremental SLAM backend.

---

## 14. Loop Closure

Loop Closure is introduced to address accumulated drift when the system revisits previously observed areas.

The project studies:

- recognizing previously visited areas;
- establishing loop constraints;
- incorporating loop information into the optimization problem;
- understanding the role of global consistency in SLAM.

---

## 15. Pose Graph Optimization

The project concludes the main SLAM pipeline with pose-graph optimization.

The workflow includes:

- constructing pose constraints;
- adding loop constraints;
- optimizing the pose graph;
- visualizing the optimized trajectory;
- studying how loop closure can correct accumulated drift.

A lazy pose-graph approach was also explored as part of understanding the global optimization stage.

---

# 🗺️ Overall SLAM Pipeline

The main development path can be summarized as:

```text
Stereo Images
      │
      ▼
Data Preparation
      │
      ▼
Feature Extraction
      │
      ▼
Feature Matching
      │
      ▼
Feature Quality Filtering
      │
      ▼
Disparity & Triangulation
      │
      ▼
MapPoints & Map
      │
      ▼
Tracking & Observations
      │
      ▼
Pose Estimation
      │
      ▼
Local Backend / Bundle Adjustment
      │
      ▼
Sliding Window
      │
      ▼
Marginalization
      │
      ▼
Loop Closure
      │
      ▼
Pose Graph Optimization
      │
      ▼
Consistent Trajectory & Map
```

Each stage was studied and implemented before being connected to the next stage.

This makes the repository useful not only as a code project, but also as a record of the learning process.

---

## 🛠️ Development Environment

The project is designed to run primarily in **Google Colab**.

### Why Google Colab?

One of the main design goals was accessibility.

Computer vision and SLAM projects can require a considerable amount of software configuration, including:

* Python packages
* C++ libraries
* Eigen
* OpenCV
* optimization libraries
* visualization tools
* compiler configuration
* system dependencies

Setting up these environments locally can become a significant barrier for someone who simply wants to study and experiment with the algorithms.

Therefore, this project was organized around Google Colab so that the notebooks can be executed with minimal local setup.

The broader goal is:

> **Make the implementation accessible to anyone who wants to study and experiment with visual odometry without first having to build a complicated robotics environment.**

---

## 🧩 Main Topics

The project covers concepts including:

### Stereo Vision

* Stereo camera geometry
* Camera coordinate systems
* Image coordinates
* Disparity
* Depth estimation
* Triangulation

### Feature-Based Visual Odometry

* Feature detection
* Feature description
* Feature matching
* Match filtering
* Geometric consistency
* Motion estimation

### 3D Geometry

* Camera projection
* Back-projection
* 2D–3D relationships
* Coordinate transformations
* Rigid-body transformations

### Motion Estimation

* Relative camera motion
* Rotation and translation
* Pose estimation
* Transformation matrices
* SE(3) representations

### Visualization and Verification

* Feature visualization
* Matching visualization
* 3D point visualization
* Camera trajectory
* Intermediate-result verification

---

## 📂 Project Structure

The project is organized progressively so that the reader can follow the development of the system rather than encountering one large implementation at the beginning.

Each notebook/section corresponds to a particular stage of the learning process.

The structure is intentionally educational:

```text
Foundations
    ↓
Individual Components
    ↓
Component Verification
    ↓
Integration
    ↓
Complete Visual Odometry Pipeline
```

---

## 🔬 From Theory to Implementation

A central principle of this project is connecting equations to actual implementation.

For each major concept, the learning process focuses on three questions:

### 1. What is the mathematical idea?

Understanding the underlying geometry, probability, optimization, or estimation problem.

### 2. Why do we need it?

Understanding the role of the component inside the complete visual odometry pipeline.

### 3. How does it become code?

Translating the mathematical formulation into an executable implementation and verifying the result.

This approach is particularly important in robotics, where individual algorithms are rarely useful in isolation.

---

## 🧪 Verification and Debugging

The project also emphasizes intermediate verification rather than only checking the final trajectory.

For example, intermediate stages can be inspected through:

* feature visualizations,
* matching results,
* filtered correspondences,
* reconstructed 3D points,
* estimated poses,
* trajectory visualization,
* and other intermediate outputs.

This helps identify where an algorithm fails instead of treating the complete pipeline as a black box.

---

## 👩‍💻 Personal Learning Project

This repository represents a stage in my personal transition toward research and development in robotics, computer vision, and autonomous systems.

The project was developed as a **structured, step-by-step learning exercise**, with the implementation, exercises, explanations, debugging strategy, and progression designed collaboratively with ChatGPT as part of my learning process.

The purpose of this collaboration was not simply to obtain working code, but to understand the underlying concepts and progressively become able to implement, inspect, debug, and explain the system independently.

---

## 🚀 Why This Project?

Visual odometry is an important building block of autonomous robotic systems.

Understanding it provides a foundation for studying larger systems such as:

* Visual SLAM
* Visual-Inertial Odometry
* State Estimation
* Sensor Fusion
* Robot Localization
* Autonomous Navigation
* 3D Reconstruction
* Multi-Sensor Perception

This project therefore serves as one step toward a broader understanding of autonomous robotic perception.

---

## 📖 Learning Philosophy

The main philosophy of this repository is:

> **Don't just run the algorithm — understand why it works.**

The implementation therefore focuses on:

* understanding before abstraction,
* equations before black-box functions,
* visualization before assuming correctness,
* debugging before moving forward,
* and connecting individual concepts into a complete robotic system.

---

## 💻 Running the Project

The notebooks are intended to be executed in **Google Colab**.

A local installation is therefore not required for the intended learning workflow.

Each notebook contains the required setup and execution steps so that the reader can progressively reproduce the experiments.

---

## 🔗 Related Work

This project is part of a broader learning and research path involving:

* Visual SLAM
* Robotic Perception
* Multi-Object Tracking
* Multi-Camera Multi-Person Tracking
* State Estimation
* Autonomous Robotics

The projects are developed with the long-term goal of understanding intelligent perception and autonomous robotic systems from both algorithmic and engineering perspectives.

---

## ⚠️ Project Status

This is an **educational implementation and learning project**, rather than a production-ready visual odometry system.

The emphasis is on:

* understanding,
* implementation,
* experimentation,
* visualization,
* and progressive development.

Further improvements and extensions may be added as the learning process continues.

---

## 📜 Acknowledgment

The project was developed alongside the study of:

**Visual SLAM: From Theory to Practice (slambook2)**

by **Gaoxiang Zhang and Huaiqian Yuan**.

The repository is an independent educational implementation and is not affiliated with the authors of the book.
