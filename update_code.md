Committing to GitHub Directions

First Time Setup:
Write the code
cd into Github/ROVMIND/ros_workspace/src
Create a package using catkin_create_pkg <pkg name> <dependency> <dependency>
Move the code into the package
Make the package using catkin_make in ros_workspace
Open up a browser and go to the Rovotics Github Page
Create a new repository, naming it with snake_case and creating a readme.
Clone the new repository to your local machine
Move the .git and readme files from the cloned repository to the package you created in Github/ROVMIND/ros_workspace/src
The .git is a hidden file, so in order to see it you must use: ls -a.
Push the package you created in Github/ROVMIND/ros_workspace/src to the new Github Repository.
git commit -am “<message goes here>”
git push
If you are not already logged in on this machine, it will give you the commands to run in order to login to your Github.
Use a personal access token in place of your password
Open up the GitHub website and navigate to the ROVMIND repository
Go to ros_workspace/src/launch_files/launch
If this program will be running on topside, edit topside.launch
If this program will be running on bottomside, edit bottomside.launch
Copy an existing node and replace the names with appropriate titles for your new code.
type= is the name of the file you want to launch

Every Time Setup:
If this is not your first time pushing the code, see step 7 to push the code to Github.
Create a new release for the code you pushed the repository to.
Navigate to the Code page in the repository and click the Releases link on the right side.
Add a title and a tag of the format: V#.#
Repeat Step 10 for the ROVMIND repository
Name the new release the next number after the previous release.
Navigate to the releasepage repository
Change the version listed in tcu_build.sh for ROVMIND
Change the version in either tcu_build or rov_build for the repository where you pushed your code.
If this is the first time with this repository, you will need to create a new line. Copy an existing git clone and replace the URL with the URL of the new repository. Make sure to use correct version
Choose between tcu_build or rov_build based on where the code is going to run.
  
  
