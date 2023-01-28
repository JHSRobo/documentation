# ROS Structure
ROS is the Robot Operating System, but it's not an OS like Linux. It's a framework that lets us run multiple programs (called **nodes**) in sync with each other. This file outlines a few key concepts for using our ROS implementation.
The difficult part about ROS is not the code that you will be writing, it is managing dependencies and integrating your code and other things along those lines.

### Nodes and Topics
**Nodes** are what ROS calls the programs that we write, and they communicate through **topics**. You can think of a topic like a chalkboard. Any node can write something on the chalkboard, and any other node can see what has been written. When a node sends something out on a topic, it is broadcasting it to the other nodes in the system.
### Publishers and Subscribers
The way that a ROS Node "writes to the topic chalkboard" is with a **publisher**. This is an object that you create in your nodes, and you can call a method to publish a value of a set data type to an indicated topic. The things that you publish are called **messages**.
To listen to a topic, you will use a **subscriber**. This is another object that you create in your code. Whenever there is a new message published to a topic, any subscribers attuned to that specific topic will run a **callback function**. This contains code you want to run every time you get a new message from a topic.
### Messages
As previously stated, messages are the things sent to topics. Each topic accepts a specific data type as a message. They're objects, and the data contained is a property of said object.
>The most common data types are a part of the ROS library `std_msgs` (http://docs.ros.org/en/api/std_msgs/html/index-msg.html). You can also create custom messages easily for sending more complex data.
