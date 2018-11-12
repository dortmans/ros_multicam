# ros_multicam

## Installation

Install this repository:
```
cd ~/catkin_ws/src
git clone https://github.com/dortmans/ros_multicam.git
cd ..
catkin_make
```

Install dependencies:
```
sudo apt install ros-kinetic-usb-cam
```
or
```
sudo apt install ros-kinetic-cv-camera
```

## Usage

Start the camera nodes:
```
roslaunch ros_multicam usb_multicam.launch
```
or
```
roslaunch ros_multicam cv_multicam.launch
```

## misc

Quick check of available cameras: ls /dev | grep video

Quick check of the support video modes of a camera: v4l2-ctl --list-formats-ext -d /dev/video0

Camera viewer with extensive camera configuration: guvcview or guvcview -d /dev/video0

View udev attributes to create different udev rules: udevadm info -a -n /dev/video0
