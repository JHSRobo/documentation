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
  * Environments should always be as standardized and up to date as possible. This means Ubuntu 22, Python3, ROS 2, etc. 
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

# Why Are We Doing This?
* ## The Approach of EOL Status
  * ROS1 Melodic (Our current version) hits End of Life status in May of next year, right before competition. 
  * Ubuntu 18 is nearing End of Life, and ROS1 Melodic is not supported on newer versions.
  * Python2 has been End of Life for a long time
* ## Forwards Sustainability
  * We want new members to be able to read our code easily, which means not forcing them to learn C++ to understand old code.
  * We should actually walk the walk in regards to standardization, and not have our code be a mess fragmented between 2 different languages.
* ## Better Understanding
  * There is a lot of old esoteric code that we don't understand. By writing it ourselves, we will be familiar with it.
  * Hopefully, this will allow future team members to understand more easily as well.
* ## Cleanup
  * We have 10 years of old code in our ROS1 architecture. We have like 3 different iterations of depth hold, and a bunch of empty topics that no longer see any use, but are still depended on by the rest of the architecture.
  * Our code is a mess. Different generations of coders have all named variables, topics, nodes, etc in their own styles, and cleaning this up while keeping the current architecture would be a massive undertaking on its own while only delaying the inevitable switch to ROS2.
* ## Cooler Code
  * We wanna use Python3! We want access to cool libraries like CirtcuitPython so we can interface easily with the new cool HAT! We wanna be able to use new libraries that aren't supported on Python2 without having to make jenky workarounds!
______________
### Alex Bertran, Nathan Peterson, James Randall, Adon Sharp, 2022
