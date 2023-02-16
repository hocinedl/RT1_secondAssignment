RT1_Assignment #2
=================
<br>This repository contains my solution for the second assignment of RT1 in which we were asked to create ROS nodes to perform specific tasks as follows (all the nodes were coded in python):</br> 
<br>1- The first ROS node allows a user to input a target position for a robot to navigate to and he can also cancel the operation and stop the robot an reassign new target distination, it was implemented using an action client </br>
<br>2- A node that publishes the robot's position and velocity as a custom message using values from the topic ``` python /odom ``` </br>
<br>3- A service node that, when activated, prints the number of goals that have been reached and cancelled.I name it (node_b_service).</br>
<br>4- A node that subscribes to the robot's position and velocity using the custom message and prints the distance of the robot from the target and the robot's average speed. A parameter will be used to set the frequency of publishing the information. (node_c_sub).</br>
<br>5- And to start the entire simulation, I created the launch file that launches multiple ROS nodes and set their parameters.</br>

# Nodes:

First of all I created the WorkSpace and in the /src file of the workspace I cloned the package Assignment_2_2022 and I created a new package which contains /scripts file.
##### These are some useful commands for running nodes and setting up the workspace.
<br> To build the workspace, we use the comand ``` catkin_make```.</br>
<br> To run a node, we use the comand ``` rosrun <package_name> <node_name(executable)>```.</br>
<br> To launch a file , we use the comand ``` rolaunch <package_name> <launch_file>```.</br>

I created the python scripts for my nodes inside /assignmentpackage/scripts:

#### Action Client node:
The action client node is responsible for allowing the user to set a target or cancel it. I implemeted it using the action client syntax.
The script does the following:
<br>This node imports various modules, including rospy for ROS functionality, actionlib for creating the action client. </br>
<br>Defines the action_client function, which creates an action client that connects to an action server at the /reaching_goal topic. The function then enters a loop that waits for keyboard input from the user. If the user enters c, the goal is cancelled. Otherwise, the user is prompted to enter the target position, which is then converted to a goal message and sent to the action server. If the user enter any letter different that 'c', it exit. </br>
The PseudoCode of the this node can be the following :

``` Define main function:
    Initialize a client to send a goal to the '/reaching_goal' action server
    Wait for the server to start
    While True:
        Ask the user to enter a position to navigate to
        If the user types 'c', cancel the current goal and continue with the loop
        Else if the user types 'q', break out of the loop
        Otherwise, split the user input into a list of coordinates and convert to float
        Create a new goal object
        Set the position of the goal to the user input coordinates
        Send the goal to the action server
    
If the script is being executed directly (i.e., not being imported as a module):
    Initializing a new ROS node and naming it
    Call the main function to start the program
``` 






#### The Publisher node:
<br> This node actually is a part of the 1st node, It is a node that publishes the robot's current position and velocity as a custom message by subscribing to the /odom and /cmd_vel topics.</br>
it defines the 'publisher' function, which is a callback for the odometry subscriber. This function takes in an odometry message, extracts the position and velocity data, and uses it to create a custom message of type Posxy_velxy. This custom message is then published.
#### The service node:
This code is a Python script that uses the ROS (Robot Operating System) framework to create a service that keeps track of how many goals have been reached and how many goals have been cancelled by the robot. The script creates a service that listens to the /reaching_goal/result topic and counts the number of goals that have been cancelled and reached and it publish it.
#### The Subscriber node:
