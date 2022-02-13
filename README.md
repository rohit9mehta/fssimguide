# FSSIM - A Better Guide!
All credits to the OG creators of FSSIM

# Installing Ubuntu (written from a Mac perspective but probably fairly applicable to Windows)
1. Install the 32 or 64 bit Desktop version of Ubuntu 16.04 from here: http://releases.ubuntu.com/16.04/
2. Install VirtualBox
3. In VirtualBox, click "New" and initialize your Ubuntu 16.04 OS. Select 10GB Memory during setup
4. Select 10GB Memory during setup, and go with the default settings for everything else 

# How to Run It in your Workspace
1. Run `sudo apt install ros-kinetic-desktop-full` and `sudo apt install python-catkin-tools`
2. Git clone from https://github.com/AMZ-Driverless/fssim, cd into this new workspace
3. Run `catkin init`
5. Run `cd src/fssim` from the workspace.
6. Run `./update_dependencies.sh`, you will need to approve multiple packages to be installed.
7. Run `echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc`
8. Run `source ~/.bashrc`
9. Run `source /opt/ros/kinetic/setup.bash`
10. Run `catkin_make`. If any errors, install what it directs to install
11. After successful building, run the simulator with `roslaunch fssim auto_fssim.launch`. RVIZ window will start. NOTE: You might need to untick and tick `FSSIM Track` and `RobotModel` in RVIZ in order to load the STL files. NOTE: This ` [Wrn] [ModelDatabase.cc:339] Getting models from[http://gazebosim.org/models/]. This may take a few seconds.` might take up to a minute when starting for the first time.
13. The terminal will inform you what is happening. The loading time takes around 20 seconds. When `Sending RES GO` will show up in the terminal, you can start controlling the vehicle with `/fssim/cmd` topic.

At this point, you have launched the simulator! In my experience, the simulator lagged so much once it launched that it was impossible to use. It did launch though!

# Combine it with simple FSD skeleton Framework and drive a lap
0. Install `sudo apt install ros-kinetic-desktop-full` and `sudo apt install python-catkin-tools` if not already done.
1. [Clone the AMZ skeleton workspace](https://github.com/AMZ-Driverless/fsd_skeleton#setting-up-the-workspace).
2. Run `./update_dependencies.sh -f` from `fsd_skeleton`, you will need to approve multiple packages to be installed
3. Compile with `catkin_make`
4. Source the workspace `source fsd_environment.sh`
5. Run `roslaunch fssim_interface fssim.launch`
6. Run `roslaunch control_meta trackdrive.launch`

or

5. Run automated test. Execute `FSD_ATS` (this command is loaded when sourcing `fsd_environment.sh`). If you will want to see the visualization, run RViZ: `roslaunch fssim_interface rviz.launch`. NOTE: The car will keep driving until the simulation will time-out since no lap counter is implemented.

In my experience, I was able to launch the fssim interface but experienced extreme lagging issues. Additionally, upon running FSD_ATS, I received a CMake error that neither me nor my advisor were able to resolve. Nevertheless, this guide should be added on to if I or anyone else ever discovers how to get around this error!
