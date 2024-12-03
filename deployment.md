# Deployment
This file contains directions for setting up new TCU or ROV software environments.
Please read architecture.md and using_software.md first.
### Topside
*When following these steps, you will need to be plugged in to one of the Rovotics routers.

1. Install **Ubuntu Desktop 24.04.1 LTS** on the TCU laptop
	* When asked to fill out user details, the username should be set to jhsrobo, the password to JHSRobo, the hostname to topside, and any other information to JHSRobo.
2. Next, run these commands:
	* `sudo apt install git`
	* `git clone https://github.com/JHSRobo/corews`
	* `sudo bash ~/corews/scripts/tcu/tcu_setup.bash`
		* This one will take some time 
	* `source ~/.bashrc`
3. Disable Wi-Fi and visit [192.168.1.1](192.168.1.1)*
	* Username: Admin | Password: JHSRobo
	* Navigate to IP > DHCP Server > Leases
		* Example image shown below setup steps for bottomside
	* Click on the IP for the TCU
		* You can find the TCU's IP using the CLI command `ip a`
	* Press Make Static, hit Close, then click on the IP for the TCU again
	* Set the TCU's IP to 192.168.1.100

### Bottomside
1. Flash a micro-SD card using the [Raspberry Pi Imager](https://www.raspberrypi.com/software/) with **Ubuntu Server 24.04.1**.
	* Click the settings icon and adjust the settings
	* Create a user with username jhsrobo and password JHSRobo
	* Enable SSH with Password Authentication
	* Disable Wifi (Important)
	* Enable the locale settings
2. Install the SD card into an RPi. Finish installation if prompted.
3. If you are able to access a router, simply connect the Raspberry Pi to the Router over Ethernet
3. If you are unabled to access a router, enable internet on the Raspberry Pi
	* Directions will vary from network to network.
	* If you choose to connect to wifi, run `ip link set wlan0 up`
		* Edit `/etc/netplan/50-cloud-init.yaml` to match your network preferences. You can see an example [here](https://github.com/JHSRobo/documentation/blob/main/example_netplan)
			* You will need to change the network name, password, and default gateway.
		* Run `sudo netplan apply`. (It might hang, in that case just reboot.)
4. Run these commands:
	* `sudo apt install git`
	* `git clone https://github.com/JHSRobo/corews`
	* `sudo bash ~/corews/rov_setup.bash`
		* This will take a bit
	* `source ~/.bashrc`
5. On a separate device, connect to the router and visit the router page: [192.168.1.1](192.168.1.1)
	* Username: Admin | Password: JHSRobo
	* Navigate to IP > DHCP Server > Leases
		* Example image shown below setup steps
	* Click on the IP for the ROV
		* You can find the ROV's IP using the CLI command `ip a`
	* Press Make Static, hit Close, then click on the IP for the TCU again
	* Set the ROV's IP to 192.168.1.111

The router page should look similar to this:
![Router Page Example](https://github.com/JHSRobo/documentation/blob/main/pictures/routerScreengrab.png "Don't mind the forced dark mode lmao")

### Virtualization
If you are following the above steps in a virtual machine, there are other steps you will have to take.
1. Configure Virtual Machine settings:
	* General -> Advanced -> Shared Clipboard: Bidirectional
	* General -> Advanced -> Drag 'n' Drop: Bidirectional
	* System -> Processors: At least 2
	* Display -> Video Memory: 128 MB
2. Go to Network, and configure Adapter 1 to be a Bridged adapter attached to your Wi-Fi device. Then, configure Adapter 2 to be a Bridged adapter attached to your Ethernet device.
	* This will allow you to connect to a Rovotics Router
3. Once you are inside Ubuntu, make the following changes:
	* Navigate to Network settings, edit your network connection, and set your IP address to be manually assigned to 192.168.1.100
	* Mount the VBoxGuestAdditions iso file that came in the directory where you installed virtualbox inside your Ubuntu environment.
		* This will enable clipboard sharing and window resizing.
### Cameras
1. Flash a micro-SD card using the [Raspberry Pi Imager](https://www.raspberrypi.com/software/) with **Raspbian Bookworm Lite** (32-bit).
	* Click the settings icon and adjust the settings
	* Create a user with username jhsrobo and password JHSRobo
	* Enable SSH with Password Authentication
	* Enable WiFi and configure with appropriate settings
	* Enable the locale settings
2. Install the SD card into a Raspberry Pi Zero 2W connected to an ethernet hat.
3. Connect the Raspberry Pi Zero 2W to a router with internet-access via ethernet.
4. Run the following commands:
	* `sudo apt update`
	* `sudo apt install git`
	* `git clone https://github.com/JHSrobo/camera_stream`
    * If you are using an Arducam camera, edit /boot/config.txt based on the [official documentation](https://docs.arducam.com/Raspberry-Pi-Camera/Native-camera/5MP-OV5647/#selection-guide).
	* `sudo bash ~/camera_stream/setup.sh`
You will be disconnected from the RPi, and you will get a video feed when you run topside.

