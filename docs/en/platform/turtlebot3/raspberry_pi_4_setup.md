---
layout: archive
lang: en
ref: raspberry_pi_4_setup
read_time: true
share: true
author_profile: false
permalink: /docs/en/platform/turtlebot3/raspberry_pi_4_setup/
sidebar:
  title: TurtleBot3
  nav: "turtlebot3"
product_group: turtlebot3
page_number: 9
---

<div style="counter-reset: h1 6"></div>
<div style="counter-reset: h2 2"></div>
<div style="counter-reset: h3 0"></div>

<!--[dummy Header 1]>
  <h1 id="setup"><a href="#setup">Setup</a></h1>
  <h2 id="sbc-setup"><a href="#sbc-setup">SBC Setup</a></h2>
<![end dummy Header 1]-->

### [Raspberry Pi 4 Setup](#raspberry_pi_4_setup)

{% capture notice_01 %}
**WARNING**:
- The contents in this chapter corresponds to the `Raspberry Pi 4` which will be the main computer of **TurtleBot3 Burger and Waffle Pi**. Do **NOT** apply this instruction to your Remote PC (your desktop PC or laptop).
- Setup work requires Power and Time. So battery is not suitable. We recommend using SMPS (AC adapter) during this work.
{% endcapture %}
<div class="notice--warning">{{ notice_01 | markdownify }}</div>


{% capture info_01 %}
**NOTE**: Use the following way to install Linux and ROS on Raspberry Pi 4
- For Linux distro image installation based on Raspbian, read `Install Linux (Raspbian)` guide. You do not have to do additional installations as the distro image contains ROS and ROS packages related to TurtleBot3.  
{% endcapture %}
<div class="notice--info">{{ info_01 | markdownify }}</div>

{% capture info_02 %}
**NOTE**: Raspberry Pi 4 B is available in TurtleBot3 Burger and Waffle Pi. If you use Raspberry Pi 4 B, please refer to the following.
{% endcapture %}
<div class="notice--info">{{ info_02 | markdownify }}</div>

  1. [Install Linux (Raspbian)][install_linux_based_on_raspbian]

#### [Install Linux based on Raspbian](#install-linux-based-on-raspbian)

**WARNING**: The SDcard should have at least **16 GB** of empty space in order to install Linux on Raspberry Pi 4.
{: .notice--warning}

We provide the Linux distro image based on Raspbian. They are pre-installed with ROS and ROS-packages related TurtleBot3. It supports the TurtleBot3 Burger and Waffle Pi model.  

##### Remote PC
- Download the Linux distro image based on Raspbian for TurtleBot3
  - [download link](http://www.robotis.com/service/download.php?no=new_address_for_raspberry_pi_4)
  - SHA256: 2ec261a23546c191deede49bba91aeeb385d28e743fcb3eb7d1f837ff25079a3
- After download, unzip the downloaded file.
- Guide to burn the image to SD card
  - Visit [etcher.io](https://etcher.io/) and download and install the Etcher SD card image utility.
  - Run Etcher and select the Linux image you downloaded on your computer or laptop.
  - Select the SD card drive.
  - Click Burn to transfer the image to the SD card.
- (other methods to burn) You can use 'dd' command in Linux or use application 'win32 Disk Imager' in Windows. For a complete guide, take a look [here](https://elinux.org/RPi_Easy_SD_Card_Setup#Using_the_Linux_command_line) (for Linux users) and [here](https://elinux.org/RPi_Easy_SD_Card_Setup#Using_the_Win32DiskImager_program) (for Windows users)

##### TurtleBot PC
- After the installation, you can login with username **pi** and password **turtlebot**. In this case, you have to connect your Raspberry Pi to your monitor using an HDMI cable, and connect your keyboard and mouse to the Raspberry Pi.

- Expand filesystem to use a whole SD card.
  ```
  sudo raspi-config
  (select 7 Advanced Options > A1 Expand Filesystem)
  ```

- [Guide to connecting to a wireless network](https://www.raspberrypi.org/learning/software-guide/wifi/)

- Synchronize and set computers' date and time by querying a Network Time Protocol (NTP) server
  ```
  sudo apt-get install ntpdate
  sudo ntpdate ntp.ubuntu.com
  ```

- If you want to change the Password, Locale and Timezone setting (Optional):
  1. sudo raspi-config > 1 Change User Password
  1. sudo raspi-config > 4 Localisation Options > I1 Change Locale
  1. sudo raspi-config > 4 Localisation Options > I2 Change Timezone

- Network configuration for ROS [(reference link)][network_configuration]
	```
	nano ~/.bashrc
	(modify `localhost` to REMOTE_PC_IP and RASPBERRY_PI_4_IP)

	export ROS_MASTER_URI=http://REMOTE_PC_IP:11311
	export ROS_HOSTNAME=RASPBERRY_PI_4_IP
	```

	```
	source ~/.bashrc
	```

##### Remote PC
- Once you're done the wireless configuration, you can connect to Raspberry Pi via SSH from your desktop or laptop [(reference link)][enable_ssh_server_in_raspberry_pi]:
  ```
  ssh pi@192.168.xxx.xxx (The IP 192.168.xxx.xxx is your Raspberry Pi's IP or hostname)
  ```

{% capture notice_03 %}
**NOTE**: **Differences from the official Raspbian Stretch**
- It based on [Raspbian Buster with desktop](https://www.raspberrypi.org/downloads/raspbian/), the Raspbian based on Debian Buster
- Enabled SSH and Camera function using raspi-config
- Change the password: **turtlebot**
- Installed software for ROS and TurtleBot3
  - [ROS Melodic Morenia](http://wiki.ros.org/melodic) and dependency software
  - [raspicam_node](https://github.com/UbiquityRobotics/raspicam_node) package for Raspberry Pi Camera
  - [hls_lfcd_lds_driver](https://github.com/ROBOTIS-GIT/hls_lfcd_lds_driver) package for Laser Distance Sensor
  - [turtlebot3](https://github.com/ROBOTIS-GIT/turtlebot3) and [turtlebot3_msgs](https://github.com/ROBOTIS-GIT/turtlebot3_msgs) packages for TutleBot3
  - Installed ROS Packages (129 packages): actionlib, actionlib_msgs, angles, bond, bond_core, bondcpp, bondpy, camera_calibration_parsers, camera_info_manager, catkin, class_loader, cmake_modules, common_msgs, compressed_image_transport, control_msgs, cpp_common, cv_bridge, diagnostic_aggregator, diagnostic_analysis, diagnostic_common_diagnostics, diagnostic_msgs, diagnostic_updater, diagnostics, dynamic_reconfigure, eigen_conversions, executive_smach, filters, gencpp, geneus, genlisp, genmsg, gennodejs, genpy, geometry, geometry_msgs, hls_lfcd_lds_driver, image_transport, joint_state_publisher, kdl_conversions, kdl_parser, kdl_parser_py, log, message_filters, message_generation, message_runtime, mk, nav_msgs, nodelet, nodelet_core, nodelet_topic_tools, orocos_kdl, pluginlib, python_orocos_kdl, python_qt_binding, raspicam_node, robot, robot_state_publisher, ros, ros_base, ros_comm, ros_core, ros_environment, rosbag, rosbag_migration_rule, rosbag_storage, rosbash, rosboost_cfg, rosbuild, rosclean, rosconsole, rosconsole_bridge, roscpp, roscpp_core, roscpp_serialization, roscpp_traits, roscreate, rosgraph, rosgraph_msgs, roslang, roslaunch, roslib, roslint, roslisp, roslz4, rosmake, rosmaster, rosmsg, rosnode, rosout, rospack, rosparam, rospy, rosserial_msgs, rosserial_python, rosservice, rostest, rostime, rostopic, rosunit, roswtf, self_test, sensor_msgs, shape_msgs, smach, smach_msgs, smach_ros, smclib, std_msgs, std_srvs, stereo_msgs, test_results, tf, tf2, tf2_kdl, tf2_msgs, tf2_py, tf2_ros, tf_conversions, topic_tools, trajectory_msgs, turtlebot3, turtlebot3_bringup, turtlebot3_msgs, urdf, urdf_parser_plugin, urdfdom_py, visualization_msgs, xacro, xmlrpcpp  
{% endcapture %}
<div class="notice--info">{{ notice_03 | markdownify }}</div>

[install_linux_based_on_raspbian]: /docs/en/platform/turtlebot3/raspberry_pi_4_setup/#install-linux-based-on-raspbian
[install_ubuntu]: /docs/en/platform/turtlebot3/joule_setup/#install-linux-ubuntu

[appendix_raspi_cam]: /docs/en/platform/turtlebot3/appendix_raspi_cam/#raspberry-pi-camera
[pc_network_configuration]: /docs/en/platform/turtlebot3/pc_setup/#network-configuration
[network_configuration]: /docs/en/platform/turtlebot3/raspberry_pi_3_setup/#5-network-configuration
[enable_ssh_server_in_raspberry_pi]: /docs/en/platform/turtlebot3/faq/#enable-ssh-server-in-raspberry-pi
