---
layout: page
title:  "Using multiple planners to control one robot arm"
subtitle: "with moveit"
date:   2022-06-28 21:21:21 +0530
categories: ["Robotics"]
---

The Hybrid Planner is being developed as a part of MoveIt2 (there have been some really cool developements, go check it [out](https://github.com/ros-planning/moveit2/issues/433). But, while we wait for it, it was time to have some fun.  

Is there really a need?  
A need for such a solution is often seen when online motion plans are required. A possible implementation of this could be querying both a global motion planner(such as PRM) as well as a local planner(such as the included pilz-industrial planner) on 2 seperate worker threads to get the fastest feasible solution.   

Is it safe though?  
Yes! Moveit checks a generated plan against the environment snapshot before returning a successful trajectory.   

Setting up such a pipeline is possible and is merely a game of namespaces and some essential remapping. Go have a look at my [repository](https://github.com/Stephen-Tellis/multiple_planners_moveit) for the code as well as demo.  

The most interesting file is perhaps `move_group.launch` in the `ur10e_moveit_config` package.   

A demo `moveit_commander` interface that allows for addressing both namespaces seperately is shown in `moveit_interface.py` of the `multi_planner_launch` package.