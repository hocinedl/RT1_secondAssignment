RT1_Assignment #2
=================
<br>This repository contains my solution for the second assignment of RT1 in which we were asked to create ROS nodes to perform specific tasks as follows:</br> 
<br>1- An action client node that allows the user to specify a target location or cancel it,I name it (node_a_action).</br>
<br>2- A node that publishes the robot's position and velocity as a custom message using values from the topic /odom, I name it (node_a_pub).</br>
<br>3- A service node that, when activated, prints the number of goals that have been reached and cancelled.I name it (node_b_service).</br>
<br>4- A node that subscribes to the robot's position and velocity using the custom message and prints the distance of the robot from the target and the robot's average speed. A parameter will be used to set the frequency of publishing the information. (node_c_sub).</br>
<br>5- And to start the entire simulation, I created the launch file.</br>

# Nodes:
The nodes were created in the /script folder of a new package named Assignment2. And it was coded using Python. 
#### Action Client node:
The action client node is responsible for allowing the user to set a target or cancel it. I implemeted it using the action client syntax 
The script does the following:
<br>This node imports various modules, including rospy for ROS functionality, actionlib for creating the action client. </br>
<br> Defines the action_client function, which creates an action client that connects to an action server at the /reaching_goal topic. The function then enters a loop that waits for keyboard input from the user. If the user enters c, the goal is cancelled. Otherwise, the user is prompted to enter the target position, which is then converted to a goal message and sent to the action server. If the user enter any letter different that 'c', it exit. </br>
#### The Publisher node:
<br> It is a node that publishes the robot's current position and velocity as a custom message using the /odom topic.</br>
it defines the 'publisher' function, which is a callback for the odometry subscriber. This function takes in an odometry message, extracts the position and velocity data, and uses it to create a custom message of type Posxy_velxy. This custom message is then published.
#### The service node:
This code is a Python script that uses the ROS (Robot Operating System) framework to create a service that keeps track of how many goals have been reached and how many goals have been cancelled by the robot. The script creates a service that listens to the /reaching_goal/result topic and counts the number of goals that have been cancelled and reached and it publish it.
#### The Subscriber node:
