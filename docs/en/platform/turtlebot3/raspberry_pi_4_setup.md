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

### [Raspberry Pi 4 Setup](#raspberry_pi_4_setup)

{% capture info_01 %}
**NOTE**: Using SMPS (AC adapter) is recommended to supply Raspberry Pi 4 with sufficient electrical power. <!-- // 충분한 전원공급을 위해서, AC 어댑터를 이용해라 > 내용이 필수적으로 들어가야하나요?  -->
{% endcapture %}
<div class="notice--info">{{ info_01 | markdownify }}</div>

This manual describes how to set up Raspberry Pi 4 that is a main PC of TurtleBot3 (for Burger and Waffle Pi).  

#### [Download a Linux distro image on your PC](#download-a-linux-distro-image-on-your-pc)

First, you need to download a distro image, which is made based on Raspbian Buster, in your own PC and burn it to a SD card.  

{% capture info_01 %}
**NOTE**: The provided distro image in this manual contains ROS and dependent ROS packages. Therefore, you don’t need to install additional ROS packages of TurtleBot3.
- [What is the difference between the Linux distro image provided by ROBOTIS and Raspbian Buster?](/docs/en/platform/turtlebot3/faq/#what-is-the-difference-between-the-linux-distro-image-provided-by-robotis-and-raspbian-buster) 
{% endcapture %}
<div class="notice--info">{{ info_01 | markdownify }}</div>

**[Remote PC]**

1. Download a zipped file. 
  - [Download](https://www.robotis.com/service/download.php?no=1905)
  - SHA256: 2ec261a23546c191deede49bba91aeeb385d28e743fcb3eb7d1f837ff25079a3
2. Extract the image from the zipped file. 
3. Burn the image to the SD card.
  - See [How to burn an image file?](/docs/en/platform/turtlebot3/faq/#how-to-burn-the-image-file)
 
    **WARNING**: Make sure that the SD card has enough storage space (over **16 GB**) to burn the image to the SD card.
    {: .notice--warning}
    
4. [Set up TurtleBot3 PC](#set-up-turtlebot3-pc).

#### [Set up TurtleBot3 PC](#set-up-turtlebot3-pc)

{% capture info_02 %}
**WARNING** : Be sure to keep the following to set up TurtleBot3 PC properly.
- Be sure to read [Download a Linux distro image on your PC](#download-a-linux-distro-image-on-your-pc) before you start the following instruction.
- Connect peripheral devices (such as, a computer monitor, keyboard, and mouse) with TurtleBot3 PC to start the process.
- Do not apply this instruction to Remote PC. **Use SBC** (TurtleBot3 PC.)
{% endcapture %}
<div class="notice--warning">{{ info_02 | markdownify }}</div>

Second, you need to set up TurtleBot3 PC, the Raspberry Pi 4.

**[TurtleBot3 PC]**  

1. Log in to TurtleBot3 PC using a username and password.
   - `Username`: pi 
   - `Password`: turtlebot

2. Expand filesystem, which is one of an Advanced Option of the command `sudo raspi-config`, to use a whole SD card using [Raspberry Pi configuration tool].
  ```
  sudo raspi-config
  (select 7 Advanced Options > A1 Expand Filesystem) 
  ```

3. Connect TurtleBot3 PC to a wireless network. 
   - See [Connecting to a wireless network] <!-- 이부분 링크가 이상해서, 공식홈페이지 참조하여 링크 다시 넣었습니다. 확인 부탁드립니다. -->

4. Synchronize and set a date and time by querying a Network Time Protocol (NTP) server by using the command below.
  ```
  sudo apt-get install ntpdate
  sudo ntpdate ntp.ubuntu.com
  ```

    **NOTE**: If you need to change User Password, Locale and Timezone, refer to [Raspberry Pi configuration tool]
    {: .notice--info}

5. Connect TurtleBot3 PC with Remote PC with the same WiFi router.
   - See [Network configuration for ROS]
   
	```
	nano ~/.bashrc
	(modify `localhost` to REMOTE_PC_IP and RASPBERRY_PI_4_IP)

	export ROS_MASTER_URI=http://REMOTE_PC_IP:11311
	export ROS_HOSTNAME=RASPBERRY_PI_4_IP
	```
6. Source the bash file. 
	```
	source ~/.bashrc
	```

<!-- 
https://www.raspberrypi.org/documentation/configuration/raspi-config.md#change-timezone 링크로 대체. 
**NOTE**: If you want to change the password, Locale and Timezone, use the following command:
- sudo raspi-config > 1 Change User Password
- sudo raspi-config > 4 Localisation Options > I1 Change Locale
- sudo raspi-config > 4 Localisation Options > I2 Change Timezone
-->
  
#### [Connect to Raspberry Pi 4 via SSH](#connect-to-raspberry-pi-4-via-ssh)

**WARNING**: Be sure to read [Set up TurtleBot3 PC](#set-up-turtlebot3-pc) before you start the following instruction.
{: .notice--warning}

**[Remote PC]**

Once, you are done with the wireless Configuration, you can connect Remote PC to Raspberry Pi via SSH.
- See [Enable SSH Server in Raspberry Pi](/docs/en/platform/turtlebot3/faq/#enable-ssh-server-in-raspberry-pi)

  ```
  ssh pi@192.168.xxx.xxx (The IP 192.168.xxx.xxx is your Raspberry Pi's IP or hostname)
  ```

[install_linux_based_on_raspbian]: /docs/en/platform/turtlebot3/raspberry_pi_4_setup/#install-linux-based-on-raspbian
[install_ubuntu]: /docs/en/platform/turtlebot3/joule_setup/#install-linux-ubuntu
[appendix_raspi_cam]: /docs/en/platform/turtlebot3/appendix_raspi_cam/#raspberry-pi-camera
[pc_network_configuration]: /docs/en/platform/turtlebot3/pc_setup/#network-configuration
[Network configuration for ROS]: /docs/en/platform/turtlebot3/raspberry_pi_3_setup/#5-network-configuration
[enable_ssh_server_in_raspberry_pi]: /docs/en/platform/turtlebot3/faq/#enable-ssh-server-in-raspberry-pi
[Connecting to a wireless network]: https://projects.raspberrypi.org/en/projects/raspberry-pi-using/4
[Raspberry Pi configuration tool]: https://www.raspberrypi.org/documentation/configuration/raspi-config.md#change-timezone
