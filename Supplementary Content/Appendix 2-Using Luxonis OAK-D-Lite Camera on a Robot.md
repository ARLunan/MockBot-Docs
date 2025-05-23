### Appendix 2: Using Luxonis Oak-D Camera on a Robot
 
OAK-D is a ultimate camera for robotic vision that perceives the world like a human by combining stereo depth camera and high-resolution color camera with an on-device Neural Network inferencing and Computer Vision capabilities. It uses USB-C for both power and USB-C connectivity.
 
Of many available models, for the purposes of this book, the **Oak-C-Lite** and **Oak-D-Pro** (same camera as Oak-D-Lite + an IMU) applications will be described. A variety of applications and ROS 2 packages are available and software installed from the repositories. 
 
Be sure to connect the camera to the Raspberry Pi USB-C Socket with a good quality USB-3 (inside colored blue) to LSB-C, or better yet, use Luxonis optional Power Splitter
 
**Installation of DepthAI Support**  
Non-Ros Python only
[Getting Started](https://docs.luxonis.com/software/depthai/getting-started/)
 
Depending on your machine configuration, you may need to follow instructions to install on a Linux machine in a virtual environment. You may want to follow the "Test Installation" procedure and run the DepthAI Viewer [Manual DepthAI installation](https://docs.luxonis.com/software/depthai/manual-install#supported-platforms)  
\$ sudo wget -qO- https://docs.luxonis.com/install_depthai.sh | bash
 
**On ROS 2** 
Install from Binary using \$ sudo ros-jazzy-depthai-ros
For reference Github: https://github.com/luxonis/depthai-ros

To check connection, run \$ lsusb, and look for a “Movidius” device.
 
This repository includes a set of example Launch and rviz files that publish topics to display a variety of RGB, Stereo BW, depth and pointcloud2 . The launch files are written that enable command line parameters to manage the camera type, open rviz or not, resolution and many more, such as resolution and frame rate, filters.
 
The 3 different rviz files must be matched to a particular Launch file, per the Example Launch Files below. 
 
Refer to this documenation for further information
https://docs-beta.luxonis.com/software/ros/depthai-ros/intro/
https://github.com/luxonis/depthai-ros/tree/humble/depthai_examples
 
**Desktop**

The ROS 2 package **rqt** or **rqt_image_view** is used to display available ros2 image topics published by the launched file from the **Robot**. 

Run \$ ros2 topic list to see the published image topics  

\$ rqt > select Visualization > Image view > Color/Image or whatever topic shows or is desired  
\$ ros2 rqt_image_view rqt_image_view /color/image 
Select Image Topic or whatever topic shows or is desired

To visualize the image topics on rviz, run  
\$ ros2 run rviz2 rviz** and open the designated "name.rviz" file.  
 
**Robot (Optionally with attached Monitor)**
 
Example Launch Files that must be run from the **Robot**, some run the rviz2 package locally, that should only be enabled when there is an attached onitor. Otherwise set rviz:=false  
\$ ros2 launch depthai_examples *.launch.py camera\_model:=OAK_D_LITE enableRviz:=True|False (True is default)
 
#### ros2 launch depthai_examples  
 
\$ ros2 launch mobile\_publisher.launch.py camera_model:=OAK-D-LITE  
(filename.rviz)
 
\$ ros2 launch depthai\_examples  
rgb_stereo_node.launch.py camera\_model:=OAK-D-LITE enableRviz:=True, or  
ros2 launch depthai\_examples  
rgb\_stereo\_node.launch.py camera\_model:=OAK-D-LITE enableRviz:=False  
 
\$ ros2 launch depthai\_examples stereo.launch.py  
camera_model:=OAK-D-LITE enableRviz:=True   
(pointClous.rviz)  
Revise Rviz Pointcloud Display Channel = Intensity  

\$ ros2 launch depthai\_examples stereo_inertial_node.launch.py camera\_model:=OAK-D-LITE enableRviz:=True  
(stereoInertialDepthAlignROS2.rviz (aligned) or stereoInertial.rviz (rectify))  
This also launches the IMU.

Launch to publish only image and imu topics, NOT "description" and no rviz.  
\$ ros2 launch depthai\_ros\_driver camera\_as\_part\_of\_a\_robot.launch.py camera\_model:=OAK-D-LITE
