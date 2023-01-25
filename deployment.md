# Deployment
This file contains directions for setting up new TCU or ROV software environments.
Please read architecture.md and using_software.md first.
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
	* Disable Wifi (Important)
	* Enable the locale settings
2. Install the SD card into an RPi. Finish installation if prompted.
3. Enable Internet on the Raspberry Pi
	* Directions will vary from network to network. The easiest thing to do is to connect it to ethernet.
	* If you choose to connect to wifi, run `ip link set wlan0 up`
		* Edit `/etc/netplan/50-cloud-init.yaml` to match your network preferences. You can see an example [here](https://github.com/JHSRobo/documentation/blob/main/example_netplan)
			* You will need to change the network name, password, and default gateway.
		* Run `sudo netplan apply`. (It might hang, in that case just reboot.)
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
3. Once you are inside Ubuntu, make the following changes:
	* Navigate to Network settings, edit your network connection, and set your IP address to be manually assigned to 192.168.1.100
	* Mount the VBoxGuestAdditions iso file that came in the directory where you installed virtualbox inside your Ubuntu environment.
		* This will enable clipboard sharing and window resizing.
### Cameras
1. Flash a micro-SD card using the [Raspberry Pi Imager](https://www.raspberrypi.com/software/) with **Raspbian Bullseye Lite** (32-bit).
	* Click the settings icon and adjust the settings
	* Create a user with username jhsrobo and password JHSRobo
	* Enable SSH with Password Authentication
	* Enable WiFi and configure with appropriate settings
	* Enable the locale settings
2. Install the SD card into an RPi 3B+ or 4. Finish installation if prompted.
	* We use 3B+ and 4 for setup because RPi Zeros (the RPi in the cameras) does not have WiFi access.
3. Enable WiFi on the Raspberry Pi
	* You will need to enable it using the menu by running `sudo raspi-config`.
		* If you still can't connect, run`sudo nmtui` and connect to wifi.
			* If this gives you an error related to network manager, run `sudo systemctl start NetworkManager`
    * You may need to change your default gateway. Do this with `ip route add default via gateway dev wlan0 onlink`, where `gateway` is replaced with your network's default gateway.
	    * Please note that this command is temporary and only changes your IP for around 10 minutes, but this is plenty of time for the steps that come.
4. Run the following commands:
	* `sudo apt install git`
	* `git clone https://github.com/JHSrobo/camera_stream`
	* `sudo bash ~/camera_stream/stream.sh`
You will be disconnected from the RPi, and you will get a video feed when you run topside.
