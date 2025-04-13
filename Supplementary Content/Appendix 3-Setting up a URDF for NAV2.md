### Appendix 3: Setting Up a URDF for the Nav2 Example SamBot and MockTurtleBot with Create1 Base.

First, Configure a **remote** repository in your github.com to hold your code  

Name: **Repository Name**

Configure upper level root workspace 

Configure **description** and **bringup** packages  

1.        Load this repository into your local machine 
2.        Configure 3 additional packages mtc1,  mtc1_descrption, mtc1_bringup
3.        Build the code into each of these packages, step by step, testing each until no errors, proceeding to the next.  
  
A suggested way to get started with configuring a robot project **URDF** is to follow the **OPEN NAVIGATION NAV 2** *“Getting Started”* Tutorial. On a x86-64 Ubuntu Desktop Workstation, when the installation is complete, the procedure will run a Gazebo Simulation of a Turtlebot3 to demonstrate how Nav2 works with an active robot model

Then it goes on to a “**First-Time Robot Setup Guide**” to cover the essential elements of  robot navigation, Transformations, URDF, Odometry, Sensors Robot’s Footprint. It uses a Robot Model called “**Sambot**”that is a typical 2-Wheel "Diff-Drive", that can be migrated to commonly used rectangular or circular shaped Robot Models..

To follow are the specific steps we followed to configure a **MockBotC1** with a Create 1 Base.  


**Helpful Toolchain Apps**

**Urdf_launch**
A ROS 2 package that contains launch files and configurations for common URDF operations. It can be Installed from Binary into a ROS2 Humble Desktop Development Workstation,  

$ **sudo apt install ros–humble-urdf-launch** can be used as a stand-alone launch file on a command line to display on a RViz Window a selected URDF or Xacro Robot Model, that is part of a  existing developed “description” package. It provides responsive feedback to edits made to the URDF or Xacro files.


For example: After sourcing a Robot Model description package, check that the desired package is is installed your ROS 2 system: rub:  
$ ros2 pkg list|grep description.

This should list, turtlebot3_description.

Then execute ros2 launch urdf_launch display.launch.py urdf_package:=turtlebot3_description urdf_package_path:=urdf/turtlebot3_burger.urdf

RViz should open displaying the Robot Model that can be manipulated to examine the components.

**VSCode**, described previously with the ROS Extension, can facilitate code development and a handy URDF: Preview that enables you to immediately see the results of any editing the Xacro or URDF code files. Of course , useful only if you are already using VS Code to edit ROS in an active workspace.

 **Freecad** with the recently released “freecad.cross” add-on  https://github.com/galou/freecad.cross github
**CROSS** is a FreeCAD workbench that appears as an additional menu item to generate robot description packages (xacro or URDF) for the Robot Operating System,

**RTAB-Map**
http://introlab.github.io/rtabmap/
