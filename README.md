# ps4_ros
Sony PlayStation 4 DualShock®4 node joy_msg to twist_msg

# Installation
1. Install __ds4dr__: `$sudo pip install ds4drv`
1. Install __ros-joy__: http://wiki.ros.org/joy
1. Go into pairing mode with PS4: Playstation button + share button for ~5 sec
1. Run `$ds4drv` from command line to connect to PS4
  1. This will output something like _Created devices /dev/input/jsX
  1. remember /dev/input/js__X__ and create and environment variable in your .bashrc, called JOY_DEV.
  	example, add following in your .bashrc
  	`export JOY_DEV=/dev/input/js`
     NOTE: If your device jsX number changes at some point, you will have to adjust it accordingly.
  1. `$sudo chmod a+rw /dev/input/jsX`

# Starting
## roslaunch
1. `$roslaunch ps4_ros ps4`

This will load the key mappings for the ps4 conrtoller, launch the ps4 controller driver, the pepper joy node, joy node, ps4 ros node.

## One by one (if needed)
1. `$ds4drv` if it is not running already.
1. `$rosparam set joy_node/dev "/dev/input/jsX"`
1. `$rosrun joy joy_node`
1. `$rosrun ps4_ros ps4_ros`




* One can adjust the following parameter inside the launch file or use rosparam by using the _one by one_ start procedure

  * ``<param name="scale_angular" value="1.5"/>``

  * ``<param name="scale_linear" value="0.5"/>``

# Troubleshooting

* Display raw _ds4drv_ data
  * `$sudo jstest /dev/input/jsX`
  
# To Do (v.2.0)
* [ ] Pan-and-Tilt on second joystick
