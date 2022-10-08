# Software Overhaul Principles
* ## Make Rollbacks Easy
  * Always maintain a branch of each repository with working code.
  * Create new releases whenever major changes are made.
* ## Make Debugging Easy
  * Log steps in your code to log files.
  * When buttons are pressed or things are activated, log to rosout.
* ## Make Remote Development Easy
  * Each package should have its own repository.
  * Everything should be synced to Github, including libraries and config files.
  * Push **everything** to Github, even code that is in development. Just make sure to push to an in development branch.
* ## Make Names Easy
  * Packages, Programs, Topics, Nodes, Variables, etc should follow clearly outlined naming conventions. This will minimize stupid mistakes when different people work on the same code.
* ## Make ROS Easy
  * Fewer topics, more data. Whenever possible, keep things within one topic, and use a custom message type to send multiple pieces of information.
  * New topics should only be created when it is necessary to publish at a different rate. For example, a separate topic would be used for sensors and thruster data.
  * Transition towards the use of services more than topics. It is probably better to use services for things like button presses in order to reduce topic clutter and have more straightforward code.
* ## Make Environments Easy
  * Environments should always be as standardized and up to date as possible. This means Ubuntu 20, Python3, ROS Noetic +, etc. 
  * WHenever possible, avoid configuring environments. Leave them as the default. This will make developing remotely and documentation much easier.
* ## Make Readability Easy
  * You don't have to write comments for every line of your code, but you should generally provide one or two lines at the beginning of each function.
  * At the beginning of each program, write a brief paragraph about how it works. This goes a long way.
* ## Make Projects Easy
  * When you aren't doing anything, check the Software Overhaul project. There will always be stuff for you to do.
  * When you have a new idea, add it to the planning section of the project. If something's status has changed, move it. You, specficially, reading this, can move it.
* ## Make Documentation Easy
  * From now on, consolidate all documentation in this repository on Github.
  * It is better to minimize the amount of documentation required than to have great documentation. If you can make a process simpler, do it.
  * The things that need documentation are going to be things like environment configuration. Remember all weird libraries installed and all weird settings changed.
* ## Make Training Easy
  * The difficult part about training new kids is not teaching them to read your code, it is teaching them how our software architecture works and where all our nebulous config files and libraries are. Keep this as straightforward as possible to avoid the situation we have found ourselves in.
  * Every time code is updated or written, make a flowchart, add it to the repo, and list it in the .gitignore file.

______________
### Alex Bertran, Nathan Peterson, James Randall, Adon Sharp, 2022
