# Water Linked DVL A50 - ROS 2 Package

A ROS 2 package for the Water Linked DVL A50. 
<!-- Along with a subscribing client for easy visualization of the communication through ROS. -->

Water Linked A50 is, by far, the world's smallest commercially available Doppler Velocity Log. With the record-breaking 5 cm min altitude measurability, the A50 is extremely useful for working with tools close to the seabed.

![Image of Water Linked A50](img/DSC04478_1600_web.jpg?raw=true "Water Linked DVL A50")

### Prerequisites
The package has been tested with ROS 2 Humble.
<!-- , and should work with most distros of ROS 2. Although using it with distros older than Hydro may require some tweeking.  -->
The package is coded in Python 3 for easier readability, as such you would need to have Python 3 installed. Preferably Python 3.10.

## Installation
Assuming you created your ROS 2 workspace at the default location ('/ros2_ws/'), and have git installed, the below steps should work:

1. install the [Water Linked python library](https://github.com/waterlinked/dvl-python/tree/master/serial). In a directory of your choice:
```bash
git clone git@github.com:waterlinked/dvl-python.git
cd dvl-python/serial/
pip3 install -e .
```

2. clone and build the custom messages and driver software
```bash
cd ~/ros2_ws/src
git clone -b ros2_humble git@github.com:RozaGkliva/dvl-a50-ros-driver.git
cd ~/ros2_ws
colcon build --packages-select waterlinked_a50_interfaces waterlinked_a50_ros_driver
```

### Usage
The following applies to serial connection.

Find the DVLs serial port (e.g., '/dev/ttyUSB0'). Once that's done, the package and it's components can be run by following these steps:

**To run the publisher that listens to the TCP port and sends the data to ROS**
```bash
ros2 run waterlinked_a50_ros_driver dvl_serial_publisher serial_port:='/dev/ttyUSB0'
```

where the serial port should be replaced by the port of the DVL. <!--You can also display the raw DVL data in the terminal by specifying the argument "do_log_data": -->

<!-- **To run the publisher that listens to the TCP port, displays the raw data in the DVL and sends the data to ROS**
```bash
rosrun waterlinked_a50_ros_driver publisher.py _ip:=192.168.2.95 _do_log_raw_data:=true
```

**To run a subscriber node that listens to the DVL topic. Helpful for debugging or checking if everything is running as it should be. Choose between "subscriber_gui.py" and "subscriber.py". The GUI makes reading data visually much easier. While the non-GUI version makes it easier to read through the code to see how you can implement code yourself.**
```bash
rosrun waterlinked_a50_ros_driver subscriber_gui.py
``` -->
<!-- ![GUI Subscriber](img/a50_gui.png?raw=true "Interface as seen when running the GUI version of the subscriber")

## Documentation
The node publishes data to the topics: "*dvl/json_data*" and "*dvl/data*".
* *dvl/json_data*: uses a simple String formated topic that publishes the raw json data coming from the DVL.
* *dvl/data*: Uses a custom message type that structures the parsed data following our protocol. Read more about the protocol here: [DVL Protocol](https://waterlinked.github.io/docs/dvl/dvl-protocol/)

![rqt_graph of the package in action](img/a50_graph.png?raw=true "Graph of the package's node-to-node structure")

*The graph illustrates the topics and nodes created when the package is run.* -->
