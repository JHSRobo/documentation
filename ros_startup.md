# Launch Topside:

### Method 1

Open a terminal window

Run: `topside`

### Method 2
**To be used if method 1 does not work**

Open a new terminal window

Run the following commands:
1. `cd Github/ROVMIND/ros_workspace`
2. `source devel/setup.bash`
3. `roslaunch launch_files topside.launch`

# Launch Bottomside:

Open a terminal window (ctrl + alt + t)

Run: `ssh bottomside`

If you get an error about ssh keys, run the command the error message provides you with, beginning with ssh-keygen. (This will be different depending on the system)

Run: cd Github/ROVMIND/ros_workspace

Run: source devel/setup.bash

Run: roslaunch launch_files bottomside.launch

# Enable Cameras:

Open a terminal window (ctrl + alt + t)

Run: ssh bottomside

Run: cameras

# Shortcuts:

**ctrl + / (in topside window): Enable keyboard_teleop

ctrl + c: Quit a program

**f (in camera window): Toggle Fullscreen**
