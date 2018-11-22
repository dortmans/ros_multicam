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

If you want to record images in a bag file open a new terminal window and enter:
```
roslaunch ros_multicam record.launch
```

The recorded bagfile will be saved in the $ROS_HOME directory (default: ~/.ros).

To play a recorded bagfile (with or without looping):
```
roslaunch ros_multicam play.launch loop:=<true/false> <name_of_bagfile> 
```

## Misc

Quick check for video devices: `ls /dev/video*`

More ifo on available camera devices: `v4l2-ctl --list-devices`
Overview of camera controls: `v4l2-ctl -d /dev/video1 -l`
To turn off autofocus: `v4l2-ctl -d /dev/video1 -c focus_auto=0`

You can also use the uvcdynctrl utility:
Get autofocus status: `uvcdynctrl -v -d /dev/video1 --get='Focus, Auto'`
To turn off autofocus: `uvcdynctrl -d /dev/video1 -s 'Focus, Auto' 0`

Camera viewer with extensive camera configuration: `guvcview -d /dev/video1`

View udev attributes to create different udev rules: `udevadm info -a -n /dev/video1`

OpenCV VideoCaptureProperties: `cv::CAP_PROP_AUTOFOCUS = 39`
