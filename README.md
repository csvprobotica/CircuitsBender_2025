## Circuits Benders WRO 2025

_The Circuits Benders team is integrated by Maria Adames, Roberto Monterey  and Fabian Arrocha, who represent Colegio San Vicente de Paúl, Santiago in this Future Engineers competition._ 

Engineering materials
====

This repository contains engineering materials of a self-driven vehicle's model participating in the WRO Future Engineers competition in the season 2025.

Materials to build our robot:
* 1 Lego Inventor Large Hub 88016
* 1 Large Angular Motor 88017
* 1 Medium Angular Motor 88018
* 3 Technic Distance Sensor 45604
* 1 Rechargeable battery 7.4V 2100mAh
* Integrated gyroscope
* 3D modeling designs for assembly

Building Instructions
====
* Robot Structure:
  - The main idea of the design was developed by us and two sources were used as a guideline.[`M.V.P`](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://www.lego.com/cdn/product-assets/product.bi.additional.main.pdf/51515_MVP.pdf&ved=2ahUKEwiw8bretaWHAxV0mbAFHf3RBCYQFnoECBMQAQ&usg=AOvVaw04D5riAZvc2TIGsk0whvge) and [`Antons Mindstorms Hot Rod`](https://www.antonsmindstorms.com/product/hot-rod-with-spike-prime-pdf-building-instructions/)
* Components Assembly:
  - The Studio 2.0 application was used for the creation and 3D modeling of all parts in the [`models`]() directory.
* Operating Diagram:
  - The directory  [`schemes`](https://github.com/csvprobotica/Circuitsbenders/tree/main/schemes)contains a connection diagram where all the ports used are distributed, a process diagram which details all the actions to be performed and a list of electronic components in which each of the elements used are described.
* Programming Code: (Block and Python)
  - The directory [`scr`](https://github.com/csvprobotica/Circuitsbenders/tree/main/src) contains the main source code realized in a block system using the Lego Inventor Mindstorms program and Python Code.

All the programming has been done by ourselves.



## Content

* [`models`](https://github.com/csvprobotica/Circuitsbenders/tree/main/models) in this directory you will find the 3D modeled files for the assembly of the robot and its components.
* [`other`](https://github.com/csvprobotica/Circuitsbenders/tree/main/other) in this directory you will find additional files of the robot operation, process diagram and execution.
* [`schemes`](https://github.com/csvprobotica/Circuitsbenders/tree/main/schemes) contains a schematic diagram in PNG format of the electromechanical components illustrating all the elements (electronic components and motors) used in the vehicle and how they are connected to each other.
* [`src`](https://github.com/csvprobotica/Circuitsbenders/tree/main/src) contains code of control software for all components which were programmed to participate in the competition.
* [`t-photos`](https://github.com/csvprobotica/Circuitsbenders/tree/main/t-photos) contains 2 photos of the team (an official one and one funny photo with all team members).
* [`v-photos`](https://github.com/csvprobotica/Circuitsbenders/tree/main/v-photos) contains 6 photos of the vehicle (from every side, from top and bottom).
* [`video`](https://github.com/csvprobotica/Circuitsbenders/tree/main/video) contains the video.mp4 file with the robot driving demonstration.

## Mobility

This robot is designed to avoid side obstacles, complete three full rotations, and stop at its starting position, using a rear motor for forward movement and a front motor for turning.

This mobility system allows the robot to navigate autonomously in environments with obstacles, perform evasive maneuvers, and maintain precise orientation using the gyroscope.

_Below are the key aspects of its mobility:_

1.Continuous Forward Movement:

-The rear motor, connected to port B, drives the robot forward at a constant speed.
-The robot moves continuously while monitoring the distances to obstacles on both sides.

2.Side Obstacle Detection and Avoidance:

-Three ultrasonic sensors are connected to ports D (right), E (left), and F (front).
-These sensors detect obstacles on the sides of the robot.
-If the right sensor detects a wall closer than 10 cm, the robot stops the rear motor and uses the front motor to turn 90 degrees to the left.
-If the left sensor detects a wall closer than 10 cm, the robot stops the rear motor and uses the front motor to turn 90 degrees to the right.
-After avoiding an obstacle, the rear motor resumes forward movement.

3.Turning and Navigation:

-The front motor, connected to port A, is used exclusively for precise turns.
-To turn 90 degrees left, the front motor runs in reverse for a specific duration.
-To turn 90 degrees right, the front motor runs forward for a specific duration.
-These turns are calibrated to ensure the robot stays on course and navigates effectively around obstacles.

4.Gyroscope Usage:

-The gyroscope integrated into the LEGO Mindstorms hub is used to track the robot’s orientation.
-At the start, the gyroscope is reset to establish a zero-degree reference point.
-While the robot moves forward and avoids obstacles, the gyroscope measures the accumulated turning angle.
-The robot is programmed to complete three full rotations, totaling 1080 degrees.
-Each time the gyroscope detects a 360-degree rotation, the turn counter increases and the gyroscope angle resets.

5.Stopping at the Starting Position:

-After completing the three rotations, the robot stops the rear motor and remains in its starting position, indicating that the task is complete.


## Strategy
The code for the LEGO Mindstorms Inventor robot describes a method for achieving autonomous movement, obstacle avoidance, and controlled rotations.

This approach allows the LEGO Mindstorms Inventor robot to move independently through its surroundings, steer clear of obstacles, and execute precise turns. By using the rear motor for driving forward, the front motor for steering, and the gyroscope for orientation monitoring, the robot can carry out complex navigation tasks with accuracy. This strategy ensures reliable performance in changing environments while fulfilling its objectives.

_Below is an alternative detailed breakdown of the implemented strategy:_

1.Setup and Initialization:

-The program begins by configuring the hub, motors, and ultrasonic sensors.
-The rear motor (connected to port B) is assigned for propulsion
-The front motor (connected to port A) is dedicated to handling turns.
-Three ultrasonic sensors (connected to ports D, E, and F) monitor the left and right sides for obstacles.

Steady Forward Motion:

-The robot advances forward at a steady speed using the rear motor.
-This continuous movement allows it to explore its environment smoothly.

3.Detecting and Avoiding Obstacles:

-While traveling forward, the robot constantly checks distances on both sides using its ultrasonic sensors.
-If the right-side sensor identifies an obstacle within 10 cm:

    -The rear motor halts to stop forward travel.
    -The front motor rotates the robot 90 degrees to the left.
    -The program waits briefly to complete the turn.
    -Forward movement resumes.

-If the left-side sensor spots an obstacle within 10 cm:

    -The rear motor stops.
    -The front motor turns the robot 90 degrees to the right.
    -It pauses to finish the turn.
    -Forward travel resumes afterward.
    -This behavior enables the robot to maneuver around obstacles and continue navigating.

4.Orientation Monitoring with the Gyroscope:

-The built-in gyroscope is used to track the robot’s heading.
-At startup, the gyroscope is reset to establish a baseline of 0 degrees.
-Throughout operation, it measures rotation angles to monitor turning progress.

5.Completing Three Full Turns:

-The robot’s task is to achieve three complete rotations, totaling 1080 degrees.
-Every time a full 360-degree rotation is detected, a counter increases, and the gyroscope resets to zero.
-The combination of obstacle avoidance and continuous movement allows these rotations to be completed reliably.

6.Finishing and Halting:

-Once the three full rotations are complete, the rear motor stops completely.
-The robot remains stationary in its final position, signaling the end of its mission.

## Challenges
_This challenge will encourage us to design and build a functional robot prototype that solves a real-world problem. It will help us apply our knowledge of robotics, sensors, and programming, while enhancing our creativity, teamwork, and engineering skills through practical application._



