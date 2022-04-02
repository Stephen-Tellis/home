---
layout: page
title:  "Setting up a Universal Robot in gazebo and executing trajectories with moveit"
subtitle: ""
date:   2022-02-20 21:21:21 +0530
categories: ["Robotics"]
---

The first thing you will need for this fun trial is ROS1 (Robot Operating System). If you do not have it yet, have a look at my other post where I have setup a simple bash script that will install ROS for you with a single command.

After making sure ROS works, just follow the steps below

## Setting things up

1. First create and initialize a catkin workspace with the following command. We will call ours moveit_ws  
```
mkdir -p /the/full/path/moveit_ws/src && cd /the/full/path/moveit_ws
```
```
catkin_make
```

2. Clone the universal robot description and moveit setup from fmauch's repository into src of your workspace 
```
git clone -b calibration_devel git@github.com:fmauch/universal_robot.git src/universal_robot
```

3. If you are planning to control the real robot/ur-sim (we will do that in the next article), then you will also need the following repository  
```
git clone https://github.com/UniversalRobots/Universal_Robots_ROS_Driver.git src/Universal_Robots_ROS_Driver
```

4. We have to install dependencies before we can make the packages. Thanks to rosdep that is simple  
```
rosdep install --from-paths src --ignore-src -r -y
```

5. We are only one step away from actually running the robot at this stage, make your packages with the following command and remember to source your setup
```
catkin_make
```

## Getting the robot to move

1. First we need to launch the robot simulation. This is our robot in the virtual world  
```
roslaunch ur_gazebo ur10e_bringup.launch
```

2. Now we launch the entire moveit pipeline
```
roslaunch ur10e_moveit_config ur10e_moveit_planning_execution.launch sim:=true
```

3. The most straightforward way to plan and execute robot motion is to do it via rviz. Let us bring that up now.
```
roslaunch ur10e_moveit_config moveit_rviz.launch rviz_config:=$(rospack find ur10e_moveit_config)/launch/moveit.rviz
```

You should now be able to simply click and drag the big green blob (or the arrows around it) to set your desired pose and click on the button *Plan and Execute*. Remember to set the planning group to manipulator.

Now that we have control over the robot, we can use this workspace to build more complex and super interesting packages on top of it. We will also have a look at the python interface to moveit call the *moveit_commander*.



Ideas? comments? suggestions for improvement?   
Feel free to reach me on my E-mail
