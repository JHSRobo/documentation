# Using Software
This file contains instructions for launching our software, and some important ROS commands that you will find useful. You will want to read architecture.md before reading this document.
### Launching ROS
We have aliases listed in ~/.bashrc for starting ROS on topside and bottomside. Pretty much everything is done in a **CLI** (Command Line Interface).
Running our full ROS system will require multiple terminal windows or tabs. Because topside is run on the TCU, you can just open a terminal window on the TCU and run it. Bottomside is on the ROV, so to launch bottomside, you will need to `ssh`. We've listed bottomside's IP in /etc/hosts on the TCU, 
> `ssh bottomside`
> Password: JHSRobo
> SSH lets you remotely access the CLI of another computer connected to the same network by IP.
### Accessing Cameras

To launch ROS on topside, type `topside`. To launch ROS on bottomside, (once you `ssh` into bottomside) type `bottomside`. `topside` and `bottomside` are custom commands that we've specified in **~/.bashrc**. In reality, the commands are running the files topside.yaml and bottomside.ymal respectively.
> .bashrc is a bash file that runs every time you open a new terminal window. We use it to write shortcuts, configure settings, and automate things.

> In linux, ~ siginifies the home directory and . before the name of a file means that it is hidden.
### Useful Commands
We recommend that you read ros_structure.md before reading this part. This document does not contain instructions on how to use each command, just a list of commands it is helpful to know of.
  * `ros2 topic list` lists all running topics in your ROS instance
  * `ros2 topic echo` allows you to view what is being published to a topic
  * `ros2 topic pub` lets you publish a value to a topic from command line
  * `ros2 node list` lists all running nodes in your ROS instance
  * `ros2 run` lets you run a node in your ROS instance
  * `ros2 launch` lets you start your ROS instance from a launch file
  * `rosdep install --from-paths src --ignore-src -r -y` installs all dependencies listed in package.xml in your system packages.


