# ROS_Canboat
*Severn Lortie <severn.lortie@queensu.ca>*

## Description

This is a tiny wrapper around the [Canboat repository](https://github.com/canboat/canboat) for building with ROS 2's Colcon.

## How to use in your ROS 2 Project

### Add `ros_canboat` to your `.repos` file

your_project.repos:
```
repositories:
  ros_canboat:
    type: git
    url: https://github.com/robotic-esp/ros_canboat.git
    version: main
```

### Instruct users to import your external depdencies
In order to use your project, users will need to run:

```
vcs import src < your_project.repos
```
before building your project.