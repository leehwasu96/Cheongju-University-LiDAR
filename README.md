# Cheongju University LiDAR Lecture Notes<br>
  Author : Hwasu Lee<br><br>
  Affiliation : UNICON LAB (Incheon National University, South Korea)<br><br>
  Position : M.A. student<br><br>
  E-mail : leehwasu96@naver.com (or leehwasu9696@inu.ac.kr)<br><br>

#  Course Duration
  Date : 24.07.02 ~ 24.07.04<br><br>

# LiDAR Lecture Note Description
  "LiDAR Lecture Notes (1).pdf is the LiDAR lecture notes."<br><br>
  "LiDAR Lecture Notes (2).pdf is the LiDAR lecture notes."<br><br>
  "LiDAR Lecture Homework.pdf is the LiDAR lecture homeworks."<br><br>

# SLAM(Simultaneous Localization<br>And Mapping) practice command

Please note that this practice was conducted in an<br><br> 
Ubuntu 20.04 LTS and ROS(Robot Operating System) 1 Noetic environment.<br><br>

To set up the project, follow these steps:<br><br>

1. Create catkin workspace and src folder:
  ```shell
  mkdir -p ~/catkin_ws/src
  ```
<br><br>

2. Change directory to the src folder within the catkin workspace:
  ```shell
  cd ~/catkin_ws/src
  ```
<br><br>

3. Initialize and set up the build environment for the catkin workspace:
  ```shell
  catkin_init_workspace
  ```
<br><br>

4. Build the catkin workspace:
  ```shell
  cd ~/catkin_ws && catkin_make
  ```
<br><br>

5. Add the ROS package path to the environment variables:
  ```shell
  source devel/setup.bash
  ```
<br><br>

6. Change directory to the src folder within the catkin workspace:
  ```shell
  cd ~/catkin_ws/src
  ```
<br><br>

7. Install the Turtlebot3-related packages:
  ```shell
  git clone –b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3.git
  ```
  ```shell
  git clone –b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
  ```
<br><br>

8. Install the Turtlebot3-related packages and then build the catkin workspace:
  ```shell
  cd ~/catkin_ws && catkin_make
  ```
<br><br>

9. Define the Turtlebot3 model before running the Gazebo simulation:
  ```shell
  export TURTLEBOT3_MODEL=burger
  ```
<br><br>

10. Run the Turtlebot3 environment based on the Gazebo simulation:
  ```shell
  roslaunch turtlebot3_gazebo turtlebot3_world.launch
  ```
  or
  ```shell
  roslaunch turtlebot3_gazebo turtlebot3_house.launch
  ```
<br><br>

11. Run the code to control the Turtlebot3 model in a terminal different from the one where the Turtlebot3 world is running:
  ```shell
  export TURTLEBOT3_MODEL=burger
  ```
  ```shell
  roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
  ```
<br><br>

12. Run the code to perform SLAM(Gmapping) in a terminal different from the ones running the Turtlebot3 world and Turtlebot3 teleop_key:
  ```shell
  export TURTLEBOT3_MODEL=burger
  ```
  ```shell
  roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
  ```
<br><br>

13. Save the Occupancy Grid Map created based on SLAM(Gmapping) using the map_server:
  ```shell
  rosrun map_server map_saver -f ~/map
  ```
<br><br>

13-1. If the map_server package is not available, install it using the following command:
  ```shell
  sudo apt update
  ```
  ```shell
  sudo apt install ros-noetic-map-server
  ```
<br><br>

# ROS Navigation Stack practice command

Please note that this practice was conducted in an<br><br> 
Ubuntu 20.04 LTS and ROS(Robot Operating System) 1 Noetic environment.<br><br>

To set up the project, follow these steps:<br><br>

1. Define the Turtlebot3 model before running the Gazebo simulation:
  ```shell
  export TURTLEBOT3_MODEL=burger
  ```
<br><br>

2. Run the Turtlebot3 environment based on the Gazebo simulation in the same terminal:
  ```shell
  roslaunch turtlebot3_gazebo turtlebot3_world.launch
  ```
  or
  ```shell
  roslaunch turtlebot3_gazebo turtlebot3_house.launch
  ```
<br><br>

3. In a different terminal, run the following code to practice the Navigation Stack for the Turtlebot3 model:
  ```shell
  export TURTLEBOT3_MODEL=burger
  ```
  ```shell
  roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=/home/unicon3/map.yaml
  ```
  In the above command, modify that path to the path where your map.yaml file is located.<br>
  /home/unicon3/map.yaml --> /home/{your map.yaml path}
<br><br>

4. In Rviz (ROS Visualization), set the initial position of the Turtlebot3 Burger model using the "2D Pose Estimate" button, then click "2D Nav Goal" to set the target position for the Turtlebot3 Burger model.
<br><br>

# Homework : <br>Control the Turtlebot3 in the ROS Gazebo simulation environment

Please note that this practice was conducted in an<br><br> 
Ubuntu 20.04 LTS and ROS(Robot Operating System) 1 Noetic environment.<br><br>

To set up the project, follow these steps:<br><br>

1. Create the turtlebot3_control package and the scripts folder:
  ```shell
  cd ~/catkin_ws/src
  ```
  ```shell
  catkin_create_pkg turtlebot3_control rospy std_msgs sensor_msgs geometry_msgs
  ```
  ```shell
  cd ~/catkin_ws/src/turtlebot3_control
  ```
  ```shell
  mkdir scripts
  ```
<br><br>
