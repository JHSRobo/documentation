# Rovotics Naming Conventions Guide

The following is a set of guidelines for how to name things in your code. It covers **variables**, **functions**, **publishers**, **subscribers**, **topics**, **nodes**,
**packages**, **files**, and **repositories**. It also lays out guidelines for **syntax**, and what to include in your **readme**.

## The Basics
* camelCase, camelCase, camelCase. You know the drill, lowercase first letter, capital letter at the start of every consecutive word.
* Avoid one-line if statements and functions for the sake of legibility. We aren't writing in Java.
* Use 2 spaces, not tabs. Some IDEs will allow you to replace your tabs with a certain number of spaces. If you like, set this to 2.
* You don't need to excessively comment, but you should include one line descriptions for each function you write.
* Each program should have some sort of a flowchart. Include it in the readme for that package.

## Software Practices
* Each package should have a logfile. 
  * Log each major step in your program to this log file. This doesn't have to be anything complex.
  * Log whenever a button is pressed or something is activated as well.
* Avoid creating new topics wherever possible. Instead, use existing topics and custom message types to send more data.
* Use more dictionaries! We do not want to see repetitive variables.

## Naming Things
* **Variables:** Keep variable names short, but don't ever settle for one letter. It should always be clear what the variable represents. 
* **Functions:** Function names should generally be verbs or action phrases, so as to avoid confusion with variables. Keep them short as well.
* **Publishers:** Name each publisher the name of the topic it publishes to, and affix `Pub` to the end.
* **Subscribers:** Name each subscriber the name of the topic it subscribes to, and affix `Sub` to the end.
* **Topics:** Each topic should take its designated name in the Software Architecture Diagram. If you need to create a new topic, consult the
team and settle on something clear that describes its purpose.
* **Nodes:** Nodes should be the name of their program, with `Node` affixed to the end.
* **Packages:** Packages should detail what they're about, but should be named something different than the program contained within.
* **Files:** For anything created by ROS, leave it as the default unless explicitly directed to change it. This will avoid confusion.
* **Repositories:** Each repository should be named after the package it contains.

## Readme Stuff
* Each package should have a readme.
* List your readme in the .gitignore file in each package
* Each readme should contain a flowchart of the package's program, as well as a paragraph about what the program does/is for.
