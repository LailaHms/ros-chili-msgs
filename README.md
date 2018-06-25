## Generic ROS message types

Similar to ros::std_msgs but all messages contain header with timestamp and id field

## Building

 - Clone the repo into the `src` directory of your catkin workspace
 - Run `catkin_make` from the root of your catkin workspace
 - Run `catkin_make -DCMAKE_INSTALL_PREFIX=/opt/ros/<distro> install` or simply copy `*.h` files to the `include` folder of your ROS installation
 