# Setup Instructions

This document guides you through downloading necessary repositories and applying required modifications.

---

## 1. Clone Repositories

Please clone the following repositories:

```bash
git clone https://github.com/marcomoralesut/glovebox_pkg.git
git clone https://github.com/Kinovarobotics/ros2_kortex.git
```

---

## 2. Modify Robotiq 2F-85 Macro

Edit the file:

```
ros2_kortex/kortex_description/grippers/robotiq_2f_85/urdf/robotiq_2f_85_macro.xacro
```

Replace the existing snippet with the following:

```xml
name="RobotiqGripperHardwareInterface"
prefix="${prefix}"
parent="${parent}"
include_ros2_control="${include_ros2_control}"
com_port="${com_port}"
use_fake_hardware="${use_fake_hardware}"
fake_sensor_commands="${fake_sensor_commands}"
sim_isaac="${sim_isaac}">
  <origin xyz="0 0 0" rpy="0 0 0" />
```

---

## 3. Remove Plugin Block in Kortex ROS2 Control

In the file:

```
kortex_description/arms/gen3/7dof/urdf/kortex.ros2_control.xacro
```

Remove the following XML block:

```xml
<xacro:if value="${use_fake_hardware}">
  <plugin>mock_components/GenericSystem</plugin>
  <param name="fake_sensor_commands">${fake_sensor_commands}</param>
  <param name="state_following_offset">0.0</param>
</xacro:if>
```
