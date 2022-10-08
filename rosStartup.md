# Launch Topside:

### Method 1

- Open a terminal window

- Run: `topside`

### Method 2
**To be used if method 1 does not work**

Open a new terminal window

Run the following commands:
- `cd Github/ROVMIND/ros_workspace`
- `source devel/setup.bash`
- `roslaunch launch_files topside.launch`

# Launch Bottomside:

- Open a terminal window

- Run: `ssh bottomside`

if you get an error about ssh keys, run the command the error message provides you with, beginning with ssh-keygen. (This will be different depending on the system)

### Method 1

- run: `bottomside`

### Method 2

**To be used if method 1 does not work**

Run the following commands:
- `cd Github/ROVMIND/ros_workspace`
- `source devel/setup.bash`
- `roslaunch launch_files bottomside.launch`

# Enable Cameras:

- Open a terminal window
- Run: `ssh bottomside`
- Run: `cameras`

## Shortcuts:

**Open a terminal window (ctrl + alt + t)**

**ctrl + / (in topside window): Enable keyboard_teleop**

**ctrl + c: Quit a program**

**f (in camera window): Toggle Fullscreen**
