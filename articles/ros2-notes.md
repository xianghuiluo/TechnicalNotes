# ROS2 Notes

* ros2 pkg
> ros2 pkg create --build-type ament_cmake camera --dependencies rclcpp std_msgs sensor_msgs cv_bridge

* build
> rosdep install -i --from-path src --rosdistro rolling -y\
> colcon build --packages-select camera

* ros1_bridge
```bash
source ${ROS1_INSTALL_PATH}/setup.bash
source ${ROS2_INSTALL_PATH}/setup.bash
export ROS_MASTER_URI=http://localhost:11311
ros2 run ros1_bridge dynamic_bridge
```

* ros2 topic
> ros2 topic echo /camera_image --field header.stamp

* ros2 run
> ros2 run camera camera --ros-args -p CameraURL:=http://user:passwd@192.168.0.20/video.cgi

[Back to Contents](../README.md)
