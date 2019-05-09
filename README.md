# Santorini Grand Challenge

## Overview

This repo contains launch files for the 2019 Cognitive Robotics Santorini Grand Challenge.

#### Dependencies

- [Robot Operating System (ROS)](http://wiki.ros.org) (middleware for robotics),
- [Mission Controller](https://github.com/16412-cogrob-2019/mission_controller)

		git clone git@github.com:16412-cogrob-2019/mission_controller.git
- [MAAS](https://github.com/16412-cogrob-2019/MAAS)

		git clone git@github.com:16412-cogrob-2019/MAAS.git

- [EEPP](https://github.com/16412-cogrob-2019/EEPP)

		git clone git@github.com:16412-cogrob-2019/EEPP.git

- [MCTS](https://github.com/16412-cogrob-2019/mcts)

		git clone git@github.com:16412-cogrob-2019/mctss.git

- [ROS map_server](http://wiki.ros.org/map_server)

		sudo apt-get install ros-kinetic-map-server

- [Optional] If you want to use the `use_gazebo` flag to simulate the turtlebots in gazebo, you will need follow the installation steps at these links to install the `turtlebot3_navigation` and `turtlebot3_gazebo` ros packages:

[Turtlebot3 Setup + Navigation Stack](http://emanual.robotis.com/docs/en/platform/turtlebot3/pc_setup/)

[Turtlebot3 Gazebo](http://emanual.robotis.com/docs/en/platform/turtlebot3/simulation/#simulation)



## Usage
### To run without Gazebo Sim
1. Run the main launch file

		roslaunch santorini santorini.launch use_gazebo="false" use_map_server:="true"

2. To trigger the MAAS node to publish the first set of points, open another terminal and run

		rostopic pub -r 1 /activity/done mission_controller/ActivityDone -f ~/catkin_ws/src/santorini/test/test_done.yaml

### To run with Gazebo Sim
1. If you want to launch the santorini stack with a gazebo simulation use

		roslaunch santorini santorini.launch use_gazebo:="true" use_map_server:="false"

	(Note that the included `turtlebot3_navigation` starts its own map_server, so we don't need to start another one.)

2. Open rviz, click the `2D Pose Estimate` button at the top of the screen, then click on the map to give the robot a good estimate of its initial pose.

3. To trigger the MAAS node to publish the first set of points, open another terminal and run

		rostopic pub -r 1 /activity/done mission_controller/ActivityDone -f ~/catkin_ws/src/santorini/test/test_done.yaml
