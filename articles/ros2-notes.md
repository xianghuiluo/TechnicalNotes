# ROS2 Notes

* ros2 pkg
> ros2 pkg create --build-type ament_cmake camera --dependencies rclcpp std_msgs sensor_msgs cv_bridge

* ros1_bridge
```bash
source ${ROS1_INSTALL_PATH}/setup.bash
source ${ROS2_INSTALL_PATH}/setup.bash
export ROS_MASTER_URI=http://localhost:11311
ros2 run ros1_bridge dynamic_bridge
```

[Back to Contents](../README.md)
