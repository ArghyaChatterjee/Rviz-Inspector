# Rviz Inspector
This repository is all about rviz and it's usage inspection.

## Introduction to RViz

**RViz** (ROS Visualization) is a powerful 3D visualization tool for ROS (Robot Operating System). It allows you to visualize a robot's perception of the environment, sensor data, robot model, and debug complex robotic behavior in real-time.

It is widely used in robotics for:
- Visualizing sensor data (e.g., LiDAR, camera, IMU)
- Displaying the robot's URDF model
- Monitoring coordinate frames (TF tree)
- Visualizing navigation and planning data

## Prerequisites
- ROS2 installed (e.g., ROS2 Humble or newer)
- A working ROS2 workspace with some packages
- Basic knowledge of ROS2 nodes, topics, and TF

## Installing RViz

RViz2 comes pre-installed with most ROS2 distributions. If not, you can install it via:
```bash
sudo apt install ros-humble-rviz2  # Replace "humble" with your distro
```

To run RViz:
```bash
rviz2
```

## RViz User Interface Overview

- **Displays Panel**: Add and configure what data you want to visualize.
- **3D View**: The main visualization window.
- **Tools Panel**: Select interactive tools (e.g., camera control, goal setting).
- **Time Panel**: View current simulation time and control playback if using a bag file.

## Common Displays in RViz

### 1. TF
- Visualizes coordinate frames
- Add the `TF` display to view frame transformations

### 2. RobotModel
- Visualizes your robot's URDF model
- Requires `robot_state_publisher` to be running

### 3. LaserScan
- Used to view 2D LiDAR data
- Topic: usually `/scan`

### 4. Image
- Displays images from cameras
- Topic: typically `/camera/image_raw`

### 5. PointCloud2
- For 3D sensor data (e.g., depth cameras, LiDAR)
- Topic: `/points`, `/velodyne_points`, etc.

### 6. Marker / MarkerArray
- Custom visualizations (e.g., shapes, arrows)
- Published via `visualization_msgs/Marker`

## Example Workflow: Visualizing a Robot

### Step 1: Start RViz
```bash
rviz2
```

### Step 2: Load Robot Model
Make sure your URDF is being published:
```bash
ros2 launch robot_description_package description.launch.py
```
Add the `RobotModel` display and set the **Fixed Frame** (usually `base_link` or `odom`).

### Step 3: View Sensor Data
Run a node that publishes data to topics like `/scan`, `/camera/image_raw`, or `/tf`, then add respective displays.

### Step 4: Add Interactivity
Use tools like:
- **2D Pose Estimate**: Set initial pose for localization
- **2D Nav Goal**: Send goal for navigation

## Customizing and Saving Configurations
Once your visualization is set up:
- Go to `File > Save Config As` to save an `.rviz` file.
- Load it later with:
```bash
rviz2 -d path/to/your_config.rviz
```

## Useful Tips
- Always set the **Fixed Frame** correctly (match your TF tree).
- Use the `TF` display to debug frame connectivity.
- Use `ros2 topic list` and `ros2 topic echo <topic>` to verify available data.

## Resources
- [RViz2 Documentation](https://index.ros.org/p/rviz2/)
- [RViz Tutorials - ROS Wiki](https://wiki.ros.org/rviz/Tutorials)
- [TF2 Tutorials](https://docs.ros.org/en/foxy/Tutorials/Intermediate/Tf2/Tf2-Main.html)

---

With RViz, you can inspect every aspect of your robot system in real time. It is an indispensable tool for any ROS developer, especially for debugging perception and localization/navigation tasks.


