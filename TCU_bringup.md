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

8. Make github folder

   * Enter folder

9. type the command: `git clone releasepage repo`

   * Enter releasepage folder

   * Run tcu_build.sh

10. Idk where his goes, but type:

   * `Cd /etc/udev/rules.d`

   * `Sudo touch joystick.rules`

   * `Sudo nano joystick.rules`

      * Type in opened file: `“KERNAL==“HyACMO” MODE==“06666””`

11. type: `sudo nano /etc/hosts`

   * Insert

      * `192.168.1.100 master`

      * `192.168.1.111 bottomside`

12. type: `cd ~`

   * `sudo nano .bashrc`

      * `Export ROS_MASTER_URI=http://master:11311`

      * `Export ROS_HOSTNAME=master`

      * `Export ROS_IP=192.168.1.100`

   * Type `sudo crontab -e`

      * At the  bottom of the  document, type `@reboot bash /home/jhsrobo/Github/streamer/startup.sh`

## ROV:
### Raspberry Pi 3B+ : Ubuntu MATE 32-bit and ROS Build

This is a brief outline of the 4 steps you will be taking to build a full working ROV image.

   1) Install Ubuntu MATE 32 bit image on flash  (PC)
   2) Complete Ubuntu MATE configuration (Raspberry Pi 3B+/Screen/Keyboard)
   3) Install ROS Kinetic (Raspberry Pi 3B+/Screen/Keyboard)
   4) Verify image on ROV

   1. Download the following image for the core OS build process: Ubuntu Mate 18.04.02 for Raspberry Pi

https://releases.ubuntu-mate.org/archived/bionic/armhf/ubuntu-18.04.2-beta2-desktop-armhf+raspi-ext4.img.xz

|NOTE on 32 bit image|
|-----------------------------------------------------------------------------------------------------------------------------|
|armhf = hardware floating point instructions + 32-bit instruction set. 64-bit ARM supports hardware floating point and NEON |


All archived images can be found at the following location
https://releases.ubuntu-mate.org/archived/bionic/armhf/

![First_archive_library](pictures/First_archive_library.PNG)
