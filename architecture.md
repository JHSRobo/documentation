# Architecture
We recommend you read ros_structure.md before this section.
Rovotics' Architecture is called ROVMIND. It was created by Michael Equi and was re-released by James Randall.

There are two sides of ROVMIND. **Topside**, which runs on the TCU above the water, and **Bottomside**, which runs on the ROV beneath the water.
Each side runs an instance of **ROS**.
### Topside:
There are 3 permanent packages running on topside.
  * **rov_control** handles ROV motion. It takes pilot input and turns that into effort values for each thruster.
  * **copilot_interface** runs the GUI (graphical user interface) and broadcasts settings to the rest of the software environment.
  * **cameras** runs the camera viewer script. It also contains programs to be run on the cameras themselves (more on that later).
### Bottomside:
There are 3 permanent packages running on bottomside.
  * **thrusters** recieves thruster effort values from **rov_control** and interfaces with ROV hardware to make the thrusters spin.
  * **depth_sensor** takes input from the ROV depth sensor and broadcasts it to the rest of the software environment. In the future, this package will expand to include various other sensors on the ROV (don't forget to update this lol).
  * **gpio_control** toggles RPi GPIO status based on input from **copilot_interface**. Used to activate tools.

>In addition,  **launch_files** is a package on both topside and bottomside. It has files that launch each instance of ROS.
### File Structure
The **ROVMIND** repository is cloned in the home directory. Within ROVMIND, there are scripts (see deployment.md) and the **ros_workspace** directory. **ros_workspace** has several folders, but you rarely need to worry about anything other than **src**. src contains all of our packages. The TCU src file is shown below.
![File Tree example on TCU](https://github.com/JHSRobo/documentation/blob/main/pictures/tcuFiletree.png "I have transparent windows on my pc so you can see my wallpaper stripes lol")

Each package has its own repository on GitHub, and they're cloned into **src** by scripts in **ROVMIND**
>Within each package, there are several important folders and files, and you can read more about what each of those are in implementing_code.md.
### Network
Inside the TCU, there is a router. It's not connected to the internet, but it gives IPs to all of the machines in the system (TCU, ROV, Cameras). IPs are addressed as follows:
  * 192.168.1.100: Topside
  * 192.168.1.111: Bottomside
  * 192.168.1.94-99: Cameras

This lets different machines communicate with each other. All data transfer is done over ethernet, and the router acts as a central hub.
### Cameras
With the exception of the **camera_view** package on topside, our vision system runs outside of ROS. Each camera has a Raspberry Pi Zero inside. The Pi runs a script contained within the **camera_stream** package that streams video to an IP. The viewer program on Topside listens to these IPs and displays them to the pilot. For more information about how this works, check out the readme for camera_viewer.

