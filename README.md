# Hector-SLAM

## Using Hector SLAM

For using Hector SLAM on husky, change line 5 and line 6 in the mapping_default.launch

>  Change "base_frame" to "base_link"

>  Change "odom_frame" to "odom"

## Turtlebot3

> export TURTLEBOT3_MODEL=burger
> roslaunch turtlebot3_gazebo turtlebot3_world.launch

> export TURTLEBOT3_MODEL=burger
> roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=hector

> export TURTLEBOT3_MODEL=burger
> roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

> rosrun map_server map_saver -f ~/map

## Husky Robot from Clearpath robotics

Add 2D liDAR 

> export HUSKY_LMS1XX_ENABLED=1

> roslaunch husky_gazebo husky_playpen.launch

> roslaunch hector_mapping mapping_default.launch

> rosrun rviz rviz

Add robot and map in Rviz with topic /map.

> rosrun teleop_twist_keyboard teleop_twist_keyboard.py cmd_vel:=/husky_velocity_controller/cmd_vel

> rosrun map_server map_saver -f ~/map

## Build a map using rosbag

- Get rosbag file (In this example, I used the Schloss Dagstuhl Neubau datase bagfile. More datsets are available on https://code.google.com/archive/p/tu-darmstadt-ros-pkg/downloads)

> wget https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/tu-darmstadt-ros-pkg/Team_Hector_MappingBox_Dagstuhl_Neubau.bag

- Start Hector SLAM system

> roslaunch hector_slam_launch tutorial.launch

- Play data

> rosbag play Team_Hector_MappingBox_Dagstuhl_Neubau.bag  --clock