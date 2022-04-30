## Launch Topside:
Open a terminal window (ctrl + alt + t)
Run: topside
## Launch Bottomside:
Open a terminal window (ctrl + alt + t)
Run: ssh bottomside
If you get an error about ssh keys, run the command the error message provides you with, beginning with ssh-keygen. (This will be different depending on the system)
Run: cd Github/ROVMIND/ros_workspace
Run: source devel/setup.bash
Run: roslaunch launch_files bottomside.launch
## Enable Cameras:
Open a terminal window (ctrl + alt + t)
Run: ssh bottomside
Run: cameras
## Shortcuts:
**ctrl + / (in topside window): Enable keyboard_teleop
ctrl + c: Quit a program
f (in camera window): Toggle Fullscreen**
