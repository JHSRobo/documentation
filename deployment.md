# Deployment
This file contains directions for setting up new TCU or ROV software environments.
Please read architecture.md and using_ros.md first.
### Topside
1. Install **Ubuntu Desktop 20.04 LTS** on the Intel NUC in the TCU
	* When asked to fill out user details, every option should be JHSRobo, with the exception of the username (including the password), which should be jhsrobo.
2. Next, run these commands:
	* `sudo apt install git`
	* `git clone https://github.com/JHSRobo/ROVMIND`
	* `sudo bash ~/ROVMIND/tcu_bringup.sh`
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

*If you are following these steps on a device other than the TCU, you will need to be plugged in to one of the Rovotics routers.
### Bottomside
1. Flash a micro-SD card using the [Raspberry Pi Imager](https://www.raspberrypi.com/software/) with **Ubuntu Server 20.04**.
	* Click the settings icon and adjust the settings
	* Create a user with username jhsrobo and password JHSRobo
	* Enable SSH with Password Authentication
	* Enable the locale settings
2. Install the SD card into a RPi. Finish installation if prompted.
3. Enable Internet on the Raspberry Pi
	* Directions will vary from network to network. The easiest thing to do is to connect it to ethernet.
	* If that doesn't work, you can connect to WiFi. [These directions may be helpful.](https://dev.to/joeneville_/configure-ubuntu-wifi-with-netplan-4je0)
4. Run these commands:
	* `sudo apt install git`
	* `git clone https://github.com/JHSRobo/ROVMIND`
	* `sudo bash ~/ROVMIND/rov_bringup.sh`
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
