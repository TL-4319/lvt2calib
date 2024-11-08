# Information for running this tool set with LAGER setup


## Data collection
Save stuff as raw files and csv and convert to bag later

## Running LVT2Calib
Need osrf/ros:noetic-desktop-full

### Terminal 1
In terminal 1, start roscore
```
sudo docker run -it --network=host --privileged --rm  /
    -v ${PWD}:/home/catkin_ws/src/lvt2calib   /
    -v /tmp/.X11-unix:/tmp/.X11-unix   /
    -v /dev:/dev  /
    -v $HOME/.ssh:$HOME/.ssh   /
    -e DISPLAY=$DISPLAY  /
    -e QT_X11_NO_MITSHM=1  /
    osrf/ros:noetic-desktop-full
```

Within the container
```
roscore
```

### Terminal 2
In terminal 2, the recorded data can be playback as rosbag

```
sudo docker run -it --network=host --privileged --rm  /
    -v ${PWD}:/home/catkin_ws/src/lvt2calib   /
    -v /tmp/.X11-unix:/tmp/.X11-unix   /
    -v /dev:/dev  /
    -v $HOME/.ssh:$HOME/.ssh   /
    -e DISPLAY=$DISPLAY  /
    -e QT_X11_NO_MITSHM=1  /
    osrf/ros:noetic-desktop-full
```

Within the container
```
rosbag play -l <data>.bag
```

### Terminal 3
In terminal 3, we run the needed code for LVT2Calib

From ```lvt2calib/docker``` directory, run

```
sudo bash priv_run.sh
```

Follow the original documentation for calibration