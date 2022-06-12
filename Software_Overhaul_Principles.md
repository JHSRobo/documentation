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
* ## Make Topics Easy
  * Fewer topics, more data. For example: Instead of creating multiple topics for tool toggling, create one topic and custom message, and send each tool's status as a boolean in that custom message.
  * New topics should only be created when it is necessary to publish at a different rate. For example, a separate topic would be used for tools and thruster data.
* ## Make Environments Easy
  * Environments should always be as up to date as possible. This means Ubuntu 22, Python3, ROS 2, etc. 
  * WHenever possible, avoid configuring environments. Leave them as the default. This will make developing remotely and documentation much easier.
* ## Make Readability Easy
  * You don't have to write comments for every line of your code, but you should generally provide one or two lines at the beginning of each function.
  * At the beginning of each program, write a brief paragraph about how it works. This goes a long way.
