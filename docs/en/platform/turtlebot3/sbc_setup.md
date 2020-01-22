---
layout: archive
lang: en
ref: sbc_setup
read_time: true
share: true
author_profile: false
permalink: /docs/en/platform/turtlebot3/sbc_setup/
sidebar:
  title: TurtleBot3
  nav: "turtlebot3"
product_group: turtlebot3
page_number: 8
---

<div style="counter-reset: h1 6"></div>
<div style="counter-reset: h2 1"></div>

<!--[dummy Header 1]>
  <h1 id="pc-setup"><a href="#pc-setup">PC Setup</a></h1>
<![end dummy Header 1]-->

## [SBC Setup](#sbc-setup)

TurtleBot3 has a single board computer (SBC) as a main computer to use ROS 1 (or ROS 2) and its packages. 

In order to use ROS and packages, you need to install particular Linux version (such as Ubuntu, Raspbian) and ROS into the SBC.  

See the SBC Compatibility Table to verify which SBC is compatible with your own TurtleBot3, and start a setup guide depending on a SBC you have and a model of TurtleBot3.  

|          Model           | Burger | Waffle Pi | Waffle |
|:------------------------:|:------:|:---------:|:------:|
|  Raspberry Pi 4 Model B  |   O    |     O     |   X    |
|  Raspberry Pi 3 Model B  |   O    |     O     |   X    |
| Raspberry Pi 3 Model B + |   O    |     O     |   X    |
|     Intel Joule 570x     |   X    |     X     |   O    |

> SBC Compatibility Table with TurtleBot3. 

**NOTE**: Using SMPS (AC adapter) is recommended to supply Raspberry Pi with sufficient electrical power.
{: .notice--info}

### [Raspberry Pi 4](#raspberry-pi-4)

Raspberry Pi 4 Model B is compatible with TurtleBot3 Burger and Waffle Pi. If you use Raspberry Pi 4 Model B, refer to `Install Linux (Raspbian)` guide.
- [Intall Linux (Raspbian)](/docs/en/platform/turtlebot3/raspberry_pi_4_setup/).
  - The provided distro image in this manual contains ROS and dependent ROS packages. Therefore, you don’t need to install additional ROS packages of TurtleBot3.
  - See [What is the difference between the Linux distro image provided by ROBOTIS and Raspbian Buster?](/docs/en/platform/turtlebot3/faq/#what-is-the-difference-between-the-linux-distro-image-provided-by-robotis-and-raspbian-buster)  

### [Raspberry Pi 3](#raspberry-pi-3)

{% capture info_01 %}
**NOTE**: Use either of ways to install Linux and ROS on Raspberry Pi 3.
1. For Ubuntu Mate installation, read `Install Linux (Ubuntu MATE)` guide. Be sure to install ROS and dependency packages after installing the Linux images on SBC of TurtleBot. The instruction takes about 1 hour to install ROS and related packages for TurtleBot3.
2. For Linux distro image installation based on Raspbian, read `Install Linux (Raspbian)` guide. You do not have to do additional installations as the distro image contains ROS and ROS packages related to TurtleBot3.  
3. For webOS Robotics Platform, read `webOS Robotics Platform` guide. You do not need to compile packages on TurtleBot3. They will be cross-compiled using OpenEmbedded on a higher performance PC, Ubuntu 18.04 based and an image file created from them.
{% endcapture %}
<div class="notice--info">{{ info_01 | markdownify }}</div>

Raspberry Pi 3 B+ is available in TurtleBot3 Burger and Waffle Pi. If you use Raspberry Pi 3 B+, please refer to the following.

  1. [Install Linux (Ubuntu MATE)][install_linux_ubuntu_mate]

  2. [Install Linux (Raspbian)][install_linux_based_on_raspbian]

  3. [Install Linux (webOS Robotics Platform)](https://github.com/ros/meta-ros/wiki/OpenEmbedded-Build-Instructions)

### [Intel Joule 570x](#intel-joule-570x)

  - [Install Linux (Ubuntu)][install_ubuntu]

[install_linux_ubuntu_mate]: /docs/en/platform/turtlebot3/raspberry_pi_3_setup/#install-linux-ubuntu-mate
[install_linux_based_on_raspbian]: /docs/en/platform/turtlebot3/raspberry_pi_3_setup/#install-linux-based-on-raspbian
[install_linux_based_on_raspbian4]: /docs/en/platform/turtlebot3/raspberry_pi_4_setup/#install-linux-based-on-raspbian
[install_ubuntu]: /docs/en/platform/turtlebot3/joule_setup/#install-linux-ubuntu
