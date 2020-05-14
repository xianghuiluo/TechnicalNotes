# ROS Notes

* rosbag
> rosbag  play  -l  data.bag  --topic  /rslidar_points  /rslidar_points:=/lidar_pointcloud

> rosbag  record  /pointcloud  -o  data1

> rosbag  record  /pointcloud  -O  data.bag

> rosbag  record  --duration=30  -a  -O  data.bag

* catkin_make
> catkin_make  --pkg  ohmio_msgs

> catkin_make install

* sudo  apt  install  ros-distro-can
* sudo  apt  install  ros-distro-can-msgs
* sudo  apt  install  ros-distro-canopen-master

* rostopic
> rostopic  echo  /pointcloud/width

> rostopic pub /speed std_msgs/Int16 -r 100 -- '-600'

> rostopic pub /track_name std_msgs/String 1F -1

> rostopic pub /localisation geometry_msgs/PointStamped "{header: auto, point: {x: -43.49358494, y: 172.54433833, z: 300}}"

* rviz -d ./ground-seg.rviz

* ROS with Python3
> sudo apt install python3-pip python3-yaml

> sudo pip3 install rospkg catkin_pkg

[Back to Contents](../README.md)