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

Tools like v4l2-ctl can be handy for controlling your cameras.
- More info on available camera devices: `v4l2-ctl --list-devices`
- Overview of camera controls: `v4l2-ctl -d /dev/video1 --list-ctrls`
- Get autofocus status: `v4l2-ctl -d /dev/video0 --get-ctrl=focus_auto`
- Turn off autofocus: `v4l2-ctl -d /dev/video1 --set-ctrl=focus_auto=0`

Using the uvcdynctrl utility:
- List available devices: `uvcdynctrl --list`
- Overview of camera controls: `uvcdynctrl -d /dev/video1 --clist --verbose`
- Get autofocus status: `uvcdynctrl -d /dev/video1 --get='Focus, Auto'`
- Turn off autofocus: `uvcdynctrl -d /dev/video1 --set='Focus, Auto' 0`

Camera viewer with extensive camera configuration: `guvcview -d /dev/video1`

View udev attributes to create different udev rules: `udevadm info -a -n /dev/video1`

Autofocus property in OpenCV VideoCaptureProperties: `cv::CAP_PROP_AUTOFOCUS = 39`
