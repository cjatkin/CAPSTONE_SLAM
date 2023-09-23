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

`sudo apt-get update`
`sudo apt-get install get`
`sudo apt-get instal gitk git-gui`

### Clone the ArduPilot repository

Clone the ArduPilot code form the main repository
`https://github.com/ArduPilot/ardupilot.git` Link to the github

In the command line:
`git clone –recurse-submodules https://github.com/ArduPilot/ardupilot.git`
`cd ardupilot`

For debian based systems there is a script that will install all of the required packages
`Tools/environment_install/install-prereqs-ubuntu.sh -y`

Reload the path (log-out and log-in to make permanent):
`. ~/.profile`


## Install AirSim on WSL

## Install ArduPilot on WSL

## Install MavLink on WSL

## Install ArduPilot Copter SITL

## Install MavProxy on WSL

## Setup RC Controller

## Get Maps that are built in Unreal Engine 4

## Install MavROS 

## Install ROS (Melodica?)

## Catkin Workspace

## rviz

## RPLidar Node

## Hector SLAM

