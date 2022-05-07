# Committing to GitHub and Updating Release Page

## First Time Setup:

1. Write the code
 
2. `cd into Github/ROVMIND/ros_workspace/src`
 
3. Create a package using `catkin_create_pkg <pkg name> <dependency> <dependency>`
 
4. Move the code into the package

5. Make the package using `catkin_make` in ros_workspace

6. Open up a browser and go to the Rovotics Github Page

7. Create a new repository, naming it with snake_case and creating a readme.

8. Clone the new repository to your local machine

9. Move the .git and readme files from the cloned repository to the package you created in Github/ROVMIND/ros_workspace/src

10. The .git is a hidden file, so in order to see it you must use: `ls -a`.

11. Push the package you created in Github/ROVMIND/ros_workspace/src to the new Github Repository.

12. `git commit -am “<message goes here>”`

13. `git push`

- **If you are not already logged in on this machine, it will give you the commands to run in order to login to your Github.**

14. Use a personal access token in place of your password

15. Open up the GitHub website and navigate to the ROVMIND repository

16. `cd ros_workspace/src/launch_files/launch`

17. If this program will be running on topside, edit topside.launch

18. If this program will be running on bottomside, edit bottomside.launch

19. Copy an existing node and replace the names with appropriate titles for your new code.

20. type= is the name of the file you want to launch

## Updating Release Page:

- If this is not your first time pushing the code, see step 12 to push the code to Github.

1. Create a new release for the code you pushed the repository to.

2. Navigate to the Code page in the repository and click the Releases link on the right side.

3. Add a title and a tag of the format: V#.#

4. Repeat Step 10 for the ROVMIND repository

5. Name the new release the next number after the previous release.

6. Navigate to the releasepage repository

7. Change the version listed in tcu_build.sh for ROVMIND

8. Change the version in either tcu_build or rov_build for the repository where you pushed your code.

- **If this is the first time with this repository, you will need to create a new line. Copy an existing git clone and replace the URL with the URL of the new repository. Make sure to use correct version**

9. Choose between tcu_build or rov_build based on where the code is going to run.
  
  
