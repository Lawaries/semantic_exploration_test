# Active Semantic Mapping and Pose Graph Spectral Analysis for Robot Exploration [IROS 2024]

<p align = "center">   
  <img  src="docs/sim.png" width=500>
</p>

### Detected dependencies:
- ROS Noetic
- OctoMap
- PCL
- Eigen
- OpenCV
- Python3
---

# Dependency Installation and Checking Guide

## ### Detected Dependencies

* ROS Noetic
* OctoMap
* PCL (Point Cloud Library)
* Eigen
* OpenCV
* Python3

---

## 1. **Install All Required Dependencies**

```bash
# Update package index
sudo apt update

# Install ROS Noetic (if not already installed)
sudo apt install ros-noetic-desktop-full

# Install OctoMap packages
sudo apt install ros-noetic-octomap ros-noetic-octomap-msgs ros-noetic-octomap-server

# Install PCL and related ROS interfaces
sudo apt install libpcl-dev ros-noetic-pcl-ros ros-noetic-pcl-conversions

# Install Eigen
sudo apt install libeigen3-dev

# Install OpenCV (C++ and Python interfaces)
sudo apt install libopencv-dev python3-opencv

# Ensure Python3 is installed
sudo apt install python3 python3-pip
```

---

## 2. **Check Each Dependency**

### **2.1 ROS Noetic**

```bash
echo $ROS_DISTRO
# Expected output: noetic

roscore
# Should start ROS master; Ctrl+C to exit.
```

---

### **2.2 OctoMap**

```bash
rosrun octomap_server octomap_server_node
# If started without error, OctoMap is installed.
# Ctrl+C to exit.
```

---

### **2.3 PCL (Point Cloud Library)**

```bash
pkg-config --modversion pcl_common
# Should output a version number, e.g., 1.10.0

# Optional: check Python PCL (if needed for your project)
python3 -c "import pcl"
# No error = installed; Error = Python PCL not installed (usually not needed for ROS C++)
```

---

### **2.4 Eigen**

```bash
pkg-config --modversion eigen3
# Should output a version number, e.g., 3.4.0
```

---

### **2.5 OpenCV**

```bash
# For C++ interface
pkg-config --modversion opencv4
# Should output a version number, e.g., 4.2.0

# For Python interface
python3 -c "import cv2; print(cv2.__version__)"
# Should print the OpenCV version, e.g., 4.2.0
```

---

### **2.6 Python3**

```bash
python3 --version
# Should output a version number, e.g., Python 3.8.10
```

---

## 2.7 **Summary Table**

| Dependency | Install Command                                                                         | Check Command                                         | Expected Output      |
| ---------- | --------------------------------------------------------------------------------------- | ----------------------------------------------------- | -------------------- |
| ROS Noetic | `sudo apt install ros-noetic-desktop-full`                                              | `echo $ROS_DISTRO`<br>`roscore`                       | `noetic`, ROS master |
| OctoMap    | `sudo apt install ros-noetic-octomap ros-noetic-octomap-msgs ros-noetic-octomap-server` | `rosrun octomap_server octomap_server_node`           | No error             |
| PCL        | `sudo apt install libpcl-dev ros-noetic-pcl-ros ros-noetic-pcl-conversions`             | `pkg-config --modversion pcl_common`                  | Version number       |
| Eigen      | `sudo apt install libeigen3-dev`                                                        | `pkg-config --modversion eigen3`                      | Version number       |
| OpenCV     | `sudo apt install libopencv-dev python3-opencv`                                         | `pkg-config --modversion opencv4`<br>`python3 -c ...` | Version number       |
| Python3    | `sudo apt install python3 python3-pip`                                                  | `python3 --version`                                   | Version number       |

---

## 3. **Clone Required ROS Packages**

```
**step-by-step guide** 
---

# ROS Workspace Setup and Project Execution Guide

## 1. **Install All Dependencies**

> Make sure you have installed ROS Noetic, PCL, OctoMap, Eigen, OpenCV, Python3, and any other required system or Python dependencies.

---

## 2. **Create a Catkin Workspace**

```bash
mkdir -p ~/WS_SE/src
cd ~/WS_SE/src
```

*You can replace `WS_SE` with any workspace name you prefer.*

---

```bash
git clone <your_repository_url>
# Example:
git clone [https://github.com/BohemianRhapsodyz/semantic_exploration.git](https://github.com/Lawaries/semantic_exploration_test.git)
# Clone any other required repositories here as well
```

---

## 4. **Build the Workspace**

```bash
cd ~/WS_SE
catkin config --install
catkin build
```

---

## 5. **Source the Workspace Environment**

Before running any ROS nodes, always source the workspace’s setup file **in every new terminal**:

```bash
source ~/WS_SE/install/setup.bash
```

*Tip: You can add this line to your `~/.bashrc` to source automatically in every terminal:*

```bash
echo "source ~/WS_SE/install/setup.bash" >> ~/.bashrc
```

---

## 6. **Launch Each Node in a Separate Terminal**

Open a new terminal **for each node** you need to run, and remember to source the setup file every time.

### **Example Launch Sequence:**

#### **Terminal 1: SLAM / Localization**

```bash
cd ~/WS_SE
source install/setup.bash
roslaunch orb_slam2_ros orb_slam2_exploration.launch
```

#### **Terminal 2: Odometry Transfer Script**

```bash
cd ~/WS_SE
source install/setup.bash
python3 odom_transfer.py
```

#### **Terminal 3: Semantic OctoMap Mapping**

```bash
cd ~/WS_SE
source install/setup.bash
roslaunch semantic_octomap semantic_mapping.launch
```

#### **Terminal 4: Semantic Exploration Planning**

```bash
cd ~/WS_SE
source install/setup.bash
roslaunch semantic_exploration run_semantic_exploration.launch
```

---

## 7. **Tips**

* Always use the workspace root (e.g., `~/WS_SE`) for building with catkin.
* All your ROS packages should be inside the `src` folder.
* If you encounter errors about missing packages or nodes, ensure you have sourced the setup file and installed all dependencies.

---

## 8. **Summary Table**

| Step                                 | Command/Action                                              |
| ------------------------------------ | ----------------------------------------------------------- |
| Create workspace                     | `mkdir -p ~/WS_SE/src`                                      |
| Clone repositories                   | `git clone <repo_url>`                                      |
| Build workspace                      | `cd ~/WS_SE`<br>`catkin config --install`<br>`catkin build` |
| Source environment                   | `source ~/WS_SE/install/setup.bash`                         |
| Launch each node (separate terminal) | See above examples                                          |

---

## **Citation**
```
@inproceedings{zhang2024active,
  title={Active Semantic Mapping and Pose Graph Spectral Analysis for Robot Exploration},
  author={Zhang, Rongge and Bong, Haechan Mark and Beltrame, Giovanni},
  booktitle={2024 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)},
  pages={13787--13794},
  year={2024},
  organization={IEEE}
}

```
9. **Acknowledgments**

- [SSMI](https://ieeexplore.ieee.org/abstract/document/10057106)
- [Explorb](https://ieeexplore.ieee.org/abstract/document/10003990)
- [ORB-SLAM](https://ieeexplore.ieee.org/document/7946260)
- [Semantic mapping](https://github.com/floatlazer/semantic_slam)
```

**License**

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
## **Contributors**
<a href="https://github.com/BohemianRhapsodyz/semantic_exploration/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=BohemianRhapsodyz/semantic_exploration" />
</a>  

![Logo](https://mistlab.ca/images/mistlogo.png)
```
