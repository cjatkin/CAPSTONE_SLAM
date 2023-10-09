# SLAM Simulator Setup

These steps are for setting up a drone simulator that creates a map using 3D LIDAR. This map is created using a Simultaneous Localization and Mapping (SLAM) algorithm. 

Installing on Windows 10, specifically version ...

## Install Windows Subsystem for Linux 1 (WSL 1)

Enable WSL by opening “Control Panel”, “Programs”, “Turn Windows features on or off”, selecting “Windows Subsystem for Linux”, and press OK.
![Enable WSL](https://github.com/cjatkin/CAPSTONE_SLAM/assets/66192589/fd11082f-0f32-41d9-93cc-234f2617bf52)


Open the Microsoft Store, and download the Ubuntu 22.04.2 LTS. 
![Download Ubuntu 1](https://github.com/cjatkin/CAPSTONE_SLAM/assets/66192589/7d303c06-b731-4cd9-9474-00e1f2f93ec3)

![Download Ubuntu 2](https://github.com/cjatkin/CAPSTONE_SLAM/assets/66192589/e6f7202a-812e-4870-abbb-5a3708526d03)

Open the Ubuntu installation from the app store. Enter a username and password for your installation. 
![Open Ubuntu](https://github.com/cjatkin/CAPSTONE_SLAM/assets/66192589/48897019-44b9-4cf8-84fa-ca3e6e9b38be)


[WSL 1 instructions](https://learn.microsoft.com/en-us/windows/wsl/install)

## Setting up the Build Environment

### Git

The first step here is to set up Git so that the ArduPilot code repositry can be retrieved then built.

`sudo apt-get update`\
`sudo apt-get install git`\
`sudo apt-get install gitk git-gui`

### Clone the ArduPilot repository

Next step is to clone the ArduPilot code form the main repository. If a custom version of ArduPilot is being ran, the link to that repositry can be used instead.\
`https://github.com/ArduPilot/ardupilot.git` Link to the github

In the command line clone the repositry to your local machine using:\
`git clone --recurse-submodules https://github.com/ArduPilot/ardupilot.git`\
`cd ardupilot`

For debian based systems there is an included script that will install all of the required packages.\
`Tools/environment_install/install-prereqs-ubuntu.sh -y`

Reload the path (log-out and log-in to make it permanent):\
`. ~/.profile`

## Install XWindow application

Xwindow applications allow for windows with UI elements to be created when running linux from the command line.\

Install VcXserver with default settings
https://sourceforge.net/projects/vcxsrv/\


`# Export Display for XWindows`\
`# For WLS1`\
`export DISPLAY=0:0`\

Run `~/.bashrc\` to put the chagnes into effect.


##Setting up SITL

`cd arudpilot/ArduCopter`\
`sim_vehicle.py -w`

##Run Mavproxy

`cd ~/ardupilot/ArduCopter`\
`../Tools/autotest/sim_vehicle.py --map --console`




In the terminal enter\
`Mode guided`\
`Arm throttle`\
`Takeoff 40`

## MavProxy + AirSim

In WSL\
`sim_vehicle.py -v ArduCopter -f airsim-copter --console --map`\

`Param set ARMING_CHECK 0`\
`Mode guided`\
`Arm throttle`\
`Takeoff 40`



## Setup RC Controller

## Get Maps that are built in Unreal Engine 4

## Install MavROS 

## Install ROS (Melodica?)

## Catkin Workspace

## rviz

## RPLidar Node

## Hector SLAM

