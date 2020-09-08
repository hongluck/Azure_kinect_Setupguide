# Setupguide

#### this is a setup guide for my own project.
#### Hope it can help in  your projects as well
#### This repository will be mainly about setting up RGBD cameras, in Jetson nano and xavier.
#### Also, installing PCL Open3d will be updated in the ear future.



#### 1. Install ROS melodic

#### 2. Install Azure kinect sdk
#### https://github.com/microsoft/Azure-Kinect-Sensor-SDK 
#### ARM64 for Nivida jetson nano
```curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -```
#### Insert password: of your nano
```
sudo apt-add-repository https://packages.microsoft.com/ubuntu/18.04/multiarch/prod

sudo apt-get update


sudo apt-get install k4a-tools
sudo apt search k4a
```
#### check what file is missing not installed my case -dev file was not installed
```sudo apt-get install libk4a1.4-dev```
```
cd /etc/udev/rules.d/

sudo nano 99-k4a.rules
```
#### 3. go to page with rules -- https://github.com/microsoft/Azure-Kinect-Sensor-SDK/blob/develop/scripts/99-k4a.rules
#### copy and paste all 

#### 4.  run k4aviewer to check sdk installation
```k4aviewer```
#### 5.  Go to ROS driver website -- https://github.com/microsoft/Azure_Kinect_ROS_Driver
```cd catkin_ws/src ```
```git clone https://github.com/microsoft/Azure_Kinect_ROS_Driver.git```
```cd ../```
```catkin_make --force-cmake```

#### 6. For jetson nano users this will not work due to opencv and cv_bridge issue. This is because the Jetpack installs opencv4 and does not create a opencv folder in the usr repository. Follow the below instructions the issue is described in this git --https://github.com/ros-perception/vision_opencv/issues/329
#### 7.  Install opencv from source 3.x --https://ultrakid.tistory.com/10
```
sudo ln -s /usr/include/opencv4/ /usr/include/opencv
catkin_make --force-cmake
```

#### 8. Check if the driver works(plug in Azure kinect)
```
roslaunch azure_kinect_ros_driver driver.launch
source devel/setup.bash
```
