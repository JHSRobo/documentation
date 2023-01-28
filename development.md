﻿
# Development
### Important ROVOTICS Software Practices
* Avoid writing while loops. Almost any time you need something to run on repeat, you can tie it in to a topic callback.
* Don't use the `sleep()` method in code that interfaces with ROS. It causes issues. Instead, use the built in ROS function.
* Don't forget to create nodes with `rospy.init_node()`. You should do this in every program that runs on your machine.
* Spaces, not tabs. Ideally, configure your IDE to automatically replace tabs with 2 spaces. 
* When you write a new function, leave a brief one line comment detailing what it does. If you see code that doesn't have this comment, add it.
* Each program should check to see if it's being run by main. This looks like:
	* `if  __name__  ==  '__main__':`
		* Treat this as you would a main() function in another language like C.
	* This guarantees that the file is not run if it is imported by another program.
* Don't use camelCase. Instead, use **snake_case**. This is what ROS uses, so it is good to stay consistent.
### Writing Code
* Code should primarily be written during the week, and then tested on Saturdays, because testing time is usually the bottleneck for our software production.
	* This ensures that we don't squander our testing time typing away in VSCode.
* Use Virtual Machines for development. It makes simulating the TCU a piece of cake. See deployment.md for instructions setting up virtual machines.
	* It is possible to connect a TCU virtual machine to a testbench simulating the ROV. This is what our current 2023 software engineers do all the time.
### Integrating Code
* When you are implementing a new feature in an existing package, create a new branch.
	* When complete, get somebody other than yourself to facilitate the merge. This will make sure that your code is intelligible and you haven't prioritized your project over someone else's.
	* Delete the branch you were developing on when you are done.
	* Do not merge into the main branch until your code has been tested.
* When you have created a new program to be integrated into ROS, make a flowchart in diagrams.net, put it in the repository, and link to it in the **README**.
	* In the same **README**, provide a paragraph summary of what your program is and how it works. Also, include your name and year of graduation at the bottom so that you can get credit for your work.
* You will need to create these files if making a new package, or update them if integrating into a currently existing package.
	* `package.xml`: This lists all of the packages your program will need. If you import something, list it in here. Directions for how to do that can be found inside the file itself. To know what to list for your package, check out the `python.yaml` and `base.yaml` files on the rosdistro repository on ROS's Github. It contains lists of packages that rosdep (see using_software.md) will install when it is called. This is like a `requirements.txt` but on the package level. 
	* `CMakeLists.txt`: Here, you will need to list the names of any custom message files that you generate, or .cfg files that you use, or services you want to create. This file is checked by `catkin_make`, and everything listed is compiled.
	* **launch_files**: This is one of our repositories, and it contains the **launchfiles** that we use to initiate topside and bottomside. When you are implementing a new package, you will need to list your program in either **topside.launch** or **bottomside.launch** in this repository. 

