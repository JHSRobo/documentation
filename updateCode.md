# Committing to GitHub and Updating Release Page

### Creating a new package:
 
1. `cd ~Github/ROVMIND/ros_workspace/src`
 
2. Create a package using `catkin_create_pkg <pkg name> <dependency> <dependency>`
 
3. Move the code you wrote into the package

4. Compile the package using `catkin_make` in ros_workspace

5. Open up a browser and go to the Rovotics Github Page

6. Create a new repository, naming it with snake_case and creating a readme.

7. Clone the new repository to your local machine

8. Move the .git and readme files from the cloned repository to the package you created in Github/ROVMIND/ros_workspace/src

  - The .git is a hidden file, so in order to see it you must use: `ls -a`.

9. Push the package you created in Github/ROVMIND/ros_workspace/src to the new Github Repository.

10. `git commit -am “<message goes here>”`

11. `git push`

- **If you are not already logged in on this machine, it will give you the commands to run in order to login to your Github.**

12. Use a personal access token in place of your password

## Adding the repository to Launch Files

1. Open up the GitHub website and navigate to the ROVMIND repository

2. `cd ros_workspace/src/launch_files/launch`

3. If this program will be running on topside, edit topside.launch

4. If this program will be running on bottomside, edit bottomside.launch

5. Copy an existing node and replace the names with appropriate titles for your new code.

- .type= is the name of the file you want to launch

## Updating Release Page:

- *If this is not your first time pushing the code, see step 12 to push the code to Github.*

### Create a new release for the code you pushed the repository to.

1. Navigate to the `Code` page in the repository you edited and click the `Releases` link on the right side.

2. Add a title and a tag of the format: `V#.#`

- Name the new release the next number after the previous release.

#### Update the release page for the new release

- Navigate to the [`releasepage`](https://github.com/jhsrobo/releasepage) repository

- Change the version of the repository in either [`tcu_build.sh`](https://github.com/JHSRobo/releasepage/blob/master/tcu_build.sh) or [`rov_build.sh`](https://github.com/JHSRobo/releasepage/blob/master/rov_build.sh) depending on whether you want the code to be on the TCU or the ROV to the new version you created.

- **If this is the first time with this repository, you will need to create a new line. Copy an existing git clone and replace the URL with the URL of the new repository. Make sure to use correct version**
   
# Updating the new code on the TCU / ROV

1. Open a new terminal and navigate to `~/Github/releasepage`

2. `git pull` the latest code after you updated the release page

3. `bash rov_buld.sh` or `bash tcu_build.sh` depending on whether you are on the TCU or the ROV

- Ensure that it completes successfully, if it doesn't you have to fix a bug. The test benches may take a while.

4. You can then refer to the [roslaunch steps](https://github.com/JHSRobo/documentation/blob/main/ros_startup.md) to launch ros properly
