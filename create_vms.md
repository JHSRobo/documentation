### The following is a set of instructions for setting up 2 VMs to emulate Topside and Bottomside.
#### Recommended Specs: Quad core CPU, 8GB Ram (preferably more)
___
Created by James Randall
1. Determine Network Information
    1. Run ipconfig on Windows or ifconfig on MacOS or Linux in your command line.
        1. You will use this information for the next steps
    2. Determine your computer’s IP:
        1. This will probably be 192.168.X.Y
        2. The third number, X, is important.
        3. **Topside IP** = 192.168.X.111
        4. **Bottomside IP** = 192.168.X.100
        5. Whenever you see **Topside IP** or **Bottomside IP** in this doc, replace it with the actual IP.
    3. Determine your router's IP:
        1. This will usually be 192.168.1.1 or 192.168.0.1.
        2. From this point forward, this will be referred to as **Default Gateway**.
    4. Determine your netmask:
        1. This can be determined by your router page.
        2. This will usually be 255.255.255.0
        3. From this point forward, this will be referred to as **Netmask**

2. Download the AMD64 version of both operating systems and VirtualBox
    1. Topside: [Ubuntu Bionic Beaver 18.04.6](https://releases.ubuntu.com/18.04/ubuntu-18.04.6-desktop-amd64.iso)
    2. Bottomside: [Ubuntu Mate Xenial Xerus 16.04.6 ](https://cdimage.ubuntu.com/ubuntu-mate/releases/16.04/release/ubuntu-mate-16.04.6-desktop-amd64.iso)
    3. VirtualBox [Application](https://www.virtualbox.org/wiki/Downloads)
        1. Run the installer to completion and open VirtualBox

3. Create a virtual machine (VM) for Topside, and a VM for bottomside using the steps below.
    1. In the top left of the right pane, press New.
    2. Name the VM either Topside or Bottomside
    3. Machine folder is fine as the default location
    4. Type -> Linux
    5. Version -> Debian (64-bit)
    6. Allocate minimum 2 GB RAM for Bottomside, and 4 GB RAM for Topside. Allocate more if your specs will allow.
    7. Choose “Create a virtual hard disk now”
        1. Select .vdi when prompted.
        2. Select Fixed Size when prompted
        3. Give both VMs at least 16gb of storage.
        4. Default directory is fine for .vdi
    8. Repeat for both Topside and Bottomside

4. Install the OS on each VM using the steps below.
    1. Some of these steps may vary in order between Topside and Bottomside
    2. Select either Topside or Bottomside and press Start in the top left of the right pane
    3. Select the correct OS for the VM from the dropdown menu
        1. ubuntu-18.04.6-desktop-amd64.iso for Topside
        2. ubuntu-mate-16.04.6-desktop-amd64.iso for Bottomside
    4. Select to install the OS rather than try when prompted
    5. Fill out information regarding Language
    6. If prompted, leave Download Updates checked.
    7. If prompted, connect to the internet.
    8. Fill out information regarding keyboard layout.
    9. Select Minimal Installation when prompted.
    10. Select Erase disk and install OS
        1. This will wipe your .vdi, not your computer, don’t worry.
        2. Click continue if prompted
    11. Fill out information regarding location.
    12. Customize name and password however you like. Recommended settings below.
        1. Your name: JHSRobo
        2. Your computer’s name: JHSTopside / JHSBottomside
        3. Username: jhsrobo
        4. Password: JHSRobo
    13. Once installation is complete, restart the VM. Ignore what it says about removing the installation medium.
    14. Select Don’t Upgrade if prompted to upgrade Ubuntu Version
    15. If prompted, accept the software updates
    16. Shut down the VM
    17.Repeat for both Topside and Bottomside

5. In VirtualBox, for both Topside and Bottomside:
    1. Select the VM and navigate to Settings in the top left of the right pane
    2. Navigate to General > Advanced and set both Shared Clipboard and Drag’n’Drop to Bidirectional
        1. This means you will be able to drag files and use the clipboard in between your host OS and VM. It won’t start working until a later step.
    3. Navigate to system -> Motherboard and tick the Network box.
    4. Navigate to system -> Processor and allocate 2 CPUs to the VM.
    5. Navigate to Display -> Screen and turn up Video Memory.
        1. If you have a discrete GPU, I recommend maximizing at 128MB.
    6. Navigate to Network -> Adapter 1
        1. Select Bridged Adapter from dropdown
    7. Unless stated otherwise, repeat for both Topside and Bottomside

6. Install appropriate software on each VM using steps below.
    1. Launch the VM
    2. Open a terminal window
        1. `sudo apt update`
        2. `sudo apt upgrade`
        3. `sudo apt install gcc make perl`
    3. In the VirtualBox menu (top left of your window), navigate to Devices > Insert Guest Additions CD Image.
        1. If prompted, press OK, and then Run
    4. Reboot
        1. Copy/paste sharing should work now
    5. Install ROS:
        1. On Topside, install [ROS Melodic](http://wiki.ros.org/melodic/Installation/Ubuntu)
            1. Install Desktop-Full version
        2. On Bottomside, install [ROS Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu)
            1. Install ROS-Base version
    6. Install packages
        1. `sudo add-apt-repository -y ppa:jblgf0/python`
        2. `sudo apt update`
        3. `sudo apt install python3.6`
        4. `sudo apt install python-pip`
        5. `python -m pip install pyxhook`
        6. `python -m pip install smbus`
        8. `sudo apt install ssh`
        9. `sudo /etc/init.d/ssh start`
        10. `sudo apt install net-tools`
    7. Clone the Rovotics Github Repository
        1. In the root directory, make a folder called Github and cd into it.
        2. `git clone https://github.com/JHSRobo/releasepage`
        3. `cd releasepage`
        4. On Topside, install these packages:
            1. `sudo apt install ros-melodic-joy`
            2. `sudo apt install ros-melodic-rocon-std-msgs`
            3. `sudo apt install ros-melodic-rosserial`
        5. On Bottomside, install these packages:
            1. `sudo apt install ros-kinetic-joy`
            2. `sudo apt install ros-kinetic-rocon-std-msgs`
            3. `sudo apt install ros-kinetic-rosserial`
        6. On Topside: `bash tcu_build.sh`
        7. On Bottomside: `bash rov_build.sh`
        
        **DO NOT SUDO BASH. JUST NORMAL BASH.**
    8. Repeat for both Topside and Bottomside

7. Configure the settings for Topside and Bottomside:
    1. On Topside, add the Joystick Settings
        1. `cd /etc/udev/rules.d`
        2. `sudo touch joystick.rules`
        3. `sudo nano joystick.rules`
            1. Type in the opened file: KERNAL==“HyACMO” MODE==“06666”
        4. `cd ~`
    2. Adjust your IP
        1. On Bottomside:
            1. `sudo nano /etc/network/interfaces`
            2. Delete everything in the file and add the following lines:
                ```
                auto enp0s3
                iface enp0s3 inet static
                address [Bottomside IP]
                netmask [Netmask] 
                gateway [Default Gateway]
                dns-nameservers 1.1.1.1 1.0.0.1
                ```
        2. On Topside:
            1. Click on network in the top left of the desktop
            2. Navigate to Wired Connected -> Wired Settings -> The gear icon next to the toggle that says on -> IPv4
            3. Select Manual for IPV4 Method
            4. Fill in the following details:
                1. Address: **Topside IP**
                2. Netmask: **Netmask**
                3. Gateway: **Default Gateway**
            5. Click apply in the top right of the window
    3. ```sudo nano ~/.bashrc```
        1. Add the following terminal commands to the very bottom:
            ```
            cd ~/Github/ROVMIND/ros_workspace/devel
            source setup.bash
            cd ~
            export ROS_MASTER_URI=http://master:11311
            ```
        2. On Topside, add:
            ```
            export ROS_HOSTNAME=master
            export ROS_IP=[Topside IP]
            alias Topside="roslaunch launch_files topside.launch"
            ```
        3. On Bottomside, add:
            ```
            export ROS_HOSTNAME=bottomside
            export ROS_IP=[Bottomside IP]
            alias Bottomside="roslaunch launch_files bottomside.launch"
            ```
    4. sudo nano /etc/hosts
        1. Add the following lines to the top:
   
            **Topside IP** master
            
            **Bottomside IP** bottomside
            
    5. Compile everything
        1. `cd ~/Github/ROVMIND/ros_workspace`
        2. `catkin_make`
    6. Unless stated otherwise, complete all steps on Topside and Bottomside

8. Launch ROS
    * You will probably get a bunch of errors related to joysticks and hardware_interface.
    * Whenever you push to Github from these VMs, create a branch in the repository.
    * **If there is code tested only on these VMs running on the TCU or ROV I will make you drink cement**
    * Happy VMing 
