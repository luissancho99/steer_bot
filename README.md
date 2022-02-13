# Steer Bot

Simulate a simple Ackermann steering vehicle in Gazebo using `ros_control`
the `ackermann_steering_controller` and `steer_bot_hardware_gazebo`.

## Installation

```bash
# Create a workspace folder
mkdir -p <catkin_ws>/src

# Clone the repo
cd <catkin_ws>/src
git clone https://github.com/luissancho99/steer_bot

# Checkout a version of `steer_drive_ros` patched for ROS Melodic
git clone https://github.com/tsedl/steer_drive_ros.git
cd steer_drive_ros
git checkout melodic-devel

# Check dependencies
rosdep check --from-paths src --ignore-src --rosdistro melodic

# Install dependencies
rosdep install --from-paths src --ignore-src --rosdistro melodic -y

# TEB Local Planner
sudo apt update
sudo apt full-upgrade
sudo apt-get install ros-melodic-teb-local-planner
# SBPL Lattice Global Planner
sudo apt-get install ros-melodic-sbpl
sudo apt-get install ros-melodic-sbpl-lattice-planner

# Build
cd <catkin_ws>/src
catkin build
```

## Run

Start the Gazebo and rviz simulation:

```bash
roslaunch steer_bot_gazebo steer_bot_sim_obstacles.launch
```

Start navigation:

```bash
roslaunch steer_bot_navigation move_base.launch
```

If all is working well you should see the robot in Gazebo and a custom map:

![gazebo_model](https://github.com/luissancho99/steer_bot/blob/master/images/gazebo_model.png)

The robot model and odometry can be monitored in `rviz`, where position goals can be sent: 

![rviz](https://github.com/luissancho99/steer_bot/blob/master/images/rviz.png)




## License

This software is licensed under the BSD-3-Clause license found in the
LICENSE file in the root directory of this source tree.
