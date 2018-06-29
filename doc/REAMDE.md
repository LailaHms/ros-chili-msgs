## Instructions for different usage scenarios

### Publish ROS messages from a QML application
 - Build and install the `chili-msgs` ROS package. Follow instructions [here](https://github.com/chili-epfl/ros-chili-msgs)
 - Build and install the `qml-ros-publisher` QML plugin. Follow instructions [here](https://github.com/chili-epfl/qml-ros-publisher)
 - Include the plugin in your application (`import ch.epfl.chili.ros.publisher`). Create an item of type RosPublisher. Set the ROS master IP and start the node. Now you can start publishing messages to topics. For more information about the interface, consult the plugin's header file.

### Subscribe to ROS messages from a QML application
 - Build and install the `chili-msgs` ROS package. Follow instructions [here](https://github.com/chili-epfl/ros-chili-msgs)
 - Build and install the `qml-ros-subscriber` QML plugin. Follow instructions [here](https://github.com/chili-epfl/qml-ros-subscriber)
 - Include the plugin in your application (`import ch.epfl.chili.ros.subscriber`). Create an item of type RosSubscriber. Set the ROS master IP and start the node. Now you can start publishing messages to topics. For more information about the interface, consult the plugin's header file.

### Record selected topics to a ROS bag from a QML application
 - Build and install the `rosbag_recorder` ROS package. Follow instructions [here](https://github.com/chili-epfl/rosbag-recorder)
 - Build and install the `qml-ros-recorder` QML plugin. Follow instructions [here](https://github.com/chili-epfl/qml-ros-recorder)
 - Include the plugin in your application (`import ch.epfl.chili.ros.recorder`). Create an Item of type RosRecorder. Set the ROS master IP and start the node. Now you can start publishing messages to topics. For more information about the interface, consult the plugin's header file.
 
 ### Annotate a ROS bag
 - Build and install the `chili-msgs` ROS package. Follow instructions [here](https://github.com/chili-epfl/ros-chili-msgs)
 - Build and install the `qml-rosbag-annotator` QML plugin. Follow instructions [here](https://github.com/chili-epfl/qml-rosbag-annotator)
 - Build and execute the interface qml application, which is included in the `qml-rosbag-annotator` repository. Follow instructions [here](https://github.com/chili-epfl/qml-rosbag-annotator/interface)
 - For annotation, a topic of type `sensor_msgs/CompressedImage` needs to exists inside the bag.

 ### Extensions with more ROS message types
 - For publishing, add a method for the message type to the `qml-ros-publisher` plugin's implementation (ca. 6 lines of code)
 - For subscribing, add the message type and a callback to the `qml-ros-subscriber` plugin's implementation (ca. 12 lines of code)
 - For use during annotation, add the message type to `RosBagAnnotator::extractMessage` in the `qml-rosbag-annotator` plugin's implementation (ca. 10 ines of code). If it doesn't fit into the existing message type templates, create two new hashmap for stored and current messages of that type in the header file, and add cases for them everywhere they are used (as for other messages types). This might take some effort (ca. 40-50 lines of code).

 ### Other tips
  - Use an up-to-date version of Qt (min. 5.11). Make sure to use the correct `qmake` binary.
  - Create a ROS launch file to start all nodes you require in one go.
  - Make sure the ROS libraries and the include directory are correctly setup system-wide.
 