Download the following repos

https://github.com/marcomoralesut/glovebox_pkg.git
https://github.com/Kinovarobotics/ros2_kortex.git

*** Note in ros2_kortex/kortex_description/grippers/robotiq_2f_85/urdf/robotiq_2f_85_macro.xacro
use this snippet instead of what they have

name="RobotiqGripperHardwareInterface"
  prefix="${prefix}"
  parent="${parent}"
  include_ros2_control="${include_ros2_control}"
  com_port="${com_port}"
  use_fake_hardware="${use_fake_hardware}"
  fake_sensor_commands="${fake_sensor_commands}"
  sim_isaac="${sim_isaac}">
  <origin xyz="0 0 0" rpy="0 0 0" />

Also, remove this

<xacro:if value="${use_fake_hardware}">
  <plugin>mock_components/GenericSystem</plugin>
  <param name="fake_sensor_commands">${fake_sensor_commands}</param>
  <param name="state_following_offset">0.0</param>
</xacro:if>

in kortex_description/arms/gen3/7dof/urdf/kortex.ros2_control.xacro

***
