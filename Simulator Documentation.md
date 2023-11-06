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
`export DISPLAY=0:0`

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

`param set ARMING_CHECK 0`\
`mode guided`\
`arm throttle`\
`Takeoff 40`



## Setup RC Controller

## Get Maps that are built in Unreal Engine 4

## Install MavROS 

## Install ROS (Noetic)

Setup your sources.list\
`sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`

Set up your keys
`sudo apt install curl`\
`curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -`

Installation\
`sudo apt update`\
Desktop-Full Install: `sudo apt install ros-noetic-desktop-full`

Enviroment setup
`source /opt/ros/noetic/setup.bash`

Bash setup (add comments to do this manually)\
`echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc`\
`source ~/.bashrc`

Dependencies for building packages\
`sudo apt install python3-rosdep python3-rosinstall python3-rosinstall-generator python3-wstool build-essential`

Initialize rosdep\
`sudo apt install python3-rosdep`\
`sudo rosdep init`\
`rosdep update`

## ROS airsim wrapper

The ROS airsim wrapper requires GCC version 8 or above. You can check this using `gcc -version` \
If the GCC version is below 8, run:\
`sudo aput-get install gcc-8 g++-8`\
Verify the installation with `gcc-8 --version`\

Instal tf2 sensor and mavros packages: `sudo apt-get install ros-melodic-tf2-sensor-msgs ros-melodic-tf2-geometry-msgs ros-melodic-mavros*`

### Catkin Workspace

Install catkin_tools for Ubuntu 20.04 using: `pip install "git+https://github.com/catkin/catkin_tools.git#egg=catkin_tools"`

###Build

Build AirSim \
`git clone https://github.com/Microsoft/AirSim.git`\
`cd AirSim`\
`./setup.sh`\
`./build.sh`\

Setup the enviroment variables for ROS: \
`echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc`\
`source ~/.bashrc`\

Build ROS Package:\
`cd ros`\
`catkin build`

###Running
Two different terminals are required to be open simultaneously. On the first terminal run:
`source devel/setup.bash`\
`roslaunch airsim_ros_pkgs airsim_node.launch`\

In the second terminal run:\
`roslaunch airsim_ros_pkgs rviz.launch`


