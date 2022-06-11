# TCU NUC build

1. Ubuntu 16.04.7- (desktop image- 64bit version)

2. Power up NUC

    * F2 to visual bio setup  

    * Make  sure default is booting to flash drive  

3. Install Ubuntu

    *  English  

    * Don’t download updates  

    * Install 3rd party software

    * Erase disk and install

    * Use LVM

  * Stay with UEFI

    * LA time zone

    * Username: jhsrobo

    * Pword: JHSRobo

    * Login automatically

4. Wait for install to finnish

5. Remove boot flash drive and boot

6. Wait for software  update popup

  * Click “update” 

  * restart after update

7. search “Ubuntu install of ROS Melodic”

  * First link

  * Follow instructions

    * Install desktop full version

Make github folder

Enter folder

Git clone releasepage repo

Enter releasepage folder

Run tcu_build.sh

Idk where his goes, but type:

Cd /etc/udev/rules.d

Sudo touch joystick.rules

Sudo nano joystick.rules

Type in opened file: “KERNAL==“HyACMO” MODE==“06666””

Sudo nano /etc/hosts

Insert

192.168.1.100 master

192.168.1.111 bottomside

Cd ~

Sudo nano .bashrc

Export ROS_MASTER_URI=http://master:11311

Export ROS_HOSTNAME=master

Export ROS_IP=192.168.1.100

Type “sudo crontab -e”

At the  bottom of the  document, type “@reboot bash /home/jhsrobo/Github/streamer/startup.sh
