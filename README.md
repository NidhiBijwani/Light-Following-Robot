Light Following Robot
An autonomous robot that detects and tracks a light source in real time using LDR sensors and motor control logic built on Arduino.

Overview
This project is a light-following robot that uses two Light Dependent Resistors (LDRs) to compare light intensity on the left and right sides. Based on the difference, it steers the motors toward the brighter side — making the robot autonomously follow any light source.

How It Works
Two LDR sensors are placed on the left and right sides of the robot.
The Arduino reads analog values from both sensors.
If the left LDR detects more light → robot turns left.
If the right LDR detects more light → robot turns right.
If both sensors are equal → robot moves forward.
A threshold value prevents jittery movement in low-contrast lighting.
