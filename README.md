# Hierarchical Model Predictive Control for online Path planning and Tracking of Flying Robots

This repository presents the ROS simulation and details of the HMPC for path planning and tracking of the flying robots: the Cube-Drone and the Quadrotor UAVs.

## Software Requirements & Setup

In order to use this package, the following components are required:

- Ubuntu 20.04
- ROS Noetic/ C++
- Gazebo 11 (https://classic.gazebosim.org/tutorials?tut=ros_installing&cat=connect_ros)
- Casadi (https://github.com/zehuilu/Tutorial-on-CasADi-with-CPP)

Following these instructions to install the package:

```shell
# Step 1: Create and build a catkin workspace:
$ mkdir -p ~/dev_ws/src
$ cd ~/dev_ws/
$ catkin_make
$ echo "source /dev_ws/devel/setup.bash" >> ~/.bashrc
$ source ~/.bashrc

# Step 2: Clone this repo into your workspace
$ cd ~/dev_ws/src
$ git clone --recursive https://github.com/aralab-unr/Hierarchical-Model-Predictice-Control-for-Flying-Robots.git

# Step 3: Build the catkin workspace for this package
$ cd ~/dev_ws
$ catkin_make
```
The warehouse used in this package is from [AWS RoboMaker Small Warehouse World](https://github.com/aws-robotics/aws-robomaker-small-warehouse-world). Some parts of the warehouse have been removed for better visualization and to ensure the recursive feasibility of the path planning for the flying robots.
<p align="center">
  <img src="/images/warehouse.png" alt="Warehouse Environment" width="700"/>
  <br/>
  <em>Figure 1: The static warehouse environment</em>
</p>

In this package, the desired trajectory of the flying robots is  $[x_r, y_r, z_r] = [4,9,1.5] $(m)  along the $x$, $y$, and $z$-axis respectively. Therefore, we choose four obstacles inside the working spaces that are listed as follows:
| Obstacle | Shape | Position | Size |
| --- | --- | --- | --- 
| Obstacle 1 | Rectangle box | [-1.573,2.3,0.9] | [1.8,2.1,1.8] |
| Obstacle 2 | Rectangle box | [-1.49,5.22,0.75] | [2,2.2,1.5] |
| Obstacle 3 | Rectangle box | [1.58,4.40,0.925] | [2.1,1.9,1.8] |
| Obstacle 4 | Rectangle box | [3.57,0.55,1.3] | [4,0.9,2.6] |

So the nonlinear function constraints for the PMPC problem are determined by:
