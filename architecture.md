# Architecture
We recommend you read ros_structure.md before this section.
Rovotics' Architecture is called ROVMIND. It was created by Michael Equi, updated by James Randall, and updated again by Jack Frings.

There are two sides of ROVMIND. **Topside**, which runs on the TCU laptop above the water, and **Bottomside**, which runs on the ROV beneath the water.
Each side runs an instance of **ROS**.
### Topside:
There are 3 permanent packages running on topside.
  * **motion_control** handles ROV motion. It takes pilot input and turns that into a Twist containing a linear and angular vector.
  * **gripper_control** controls the Phidgets (and by extension the grippers) based on pilot input.
  * **pilot_gui** runs the camera viewer scripts. It also sends the camera feed to opside. 
### Bottomside:
There are 3 permanent packages running on bottomside.
  * **thruster_interface** recieves a vector from motion_control, converts that vector into thruster effort values, and interfaces with the ROV to spin the thrusters.
  * **sensor_interface** takes input from various sensors and broadcasts the sensor data to the rest of the software environment. Currently, the ROV takes input from a depth_sensor, an imu sensor, a leak sensor, and temperature sensors.
  * **gpio_interface** toggles RPi GPIO status. Currently, it is not used for anything. 

### File Structure
The **corews** repository is cloned in the home directory. Within corews, there is the **src** directory that contains all of our packages. The TCU src file is shown below.
![File Tree example on TCU](https://github.com/JHSRobo/documentation/blob/main/pictures/tcuFiletree.png) 
Each package has its own repository on GitHub, and they're cloned into **src** by scripts in the **scripts** directory
>Within each package, there are several important folders and files, and you can read more about what each of those are in implementing_code.md.
### Network
Inside the TCU, there is a router. It's not connected to the internet, but it gives IPs to all of the machines in the system (TCU, ROV, Cameras). IPs are addressed as follows:
  * 192.168.1.100: Topside
  * 192.168.1.111: Bottomside
  * 192.168.1.94-99: Cameras

This lets different machines communicate with each other. All data transfer is done over ethernet, and the router acts as a central hub.
### Cameras
With the exception of the **pilot_gui** package on topside, our vision system runs outside of ROS. Each camera has a Raspberry Pi Zero 2W inside. The Pi runs a script contained within the **camera_stream** package that streams video to an IP. The viewer program on Topside listens to these IPs and displays them to the pilot. For more information about how this works,check out the readme for **pilot_gui**.

