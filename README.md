RT1_Assignment #2
=================

This repository contains my solution for the second assignment of RT1 in which we were asked to create ROS nodes to perform specific tasks as follows: 
1- An action client node that allows the user to specify a target location or cancel it,I name it (node_a_action).
2- A node that publishes the robot's position and velocity as a custom message using values from the topic /odom, I name it (node_a_pub).
3- A service node that, when activated, prints the number of goals that have been reached and cancelled.I name it (node_b_service).
4- A node that subscribes to the robot's position and velocity using the custom message and prints the distance of the robot from the target and the robot's average speed. A parameter will be used to set the frequency of publishing the information. (node_c_sub).
5- And to start the entire simulation, I created the launch file.
