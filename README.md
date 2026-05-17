Light Following Robot
An autonomous robot that detects and tracks a light source in real time using LDR sensors and motor control logic built on Arduino.

Overview
This project is a light-following robot that uses two Light Dependent Resistors (LDRs) to compare light intensity on the left and right sides. Based on the difference, it steers the motors toward the brighter side — making the robot autonomously follow any light source.

How It Works
Two LDR sensors are placed on the left and right sides of the robot.
The Arduino reads analog values from both sensors.
If the left LDR detects more light → robot turns right.
If the right LDR detects more light → robot turns left.
If both sensors are equal → robot moves forward.
A threshold value prevents jittery movement in low-contrast lighting.

Code
#define LeftLDR 8
#define RightLDR 9
#define IN1 10
#define IN2 11
#define IN3 12
#define IN4 13
void setup() {
  pinMode(LeftLDR, INPUT);
  pinMode(RightLDR, INPUT);
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
}
void loop() {
  // Both detect light → move forward
  if (!digitalRead(LeftLDR) && !digitalRead(RightLDR)) {
    digitalWrite(IN1, HIGH);
    digitalWrite(IN2, LOW);
    digitalWrite(IN3, HIGH);
    digitalWrite(IN4, LOW);
  }
  // Left dark → turn left
  else if (!digitalRead(LeftLDR)) {
    digitalWrite(IN1, LOW);
    digitalWrite(IN2, LOW);
    digitalWrite(IN3, HIGH);
    digitalWrite(IN4, LOW);
  }
  // Right dark → turn right
  else if (!digitalRead(RightLDR)) {
    digitalWrite(IN1, HIGH);
    digitalWrite(IN2, LOW);
    digitalWrite(IN3, LOW);
    digitalWrite(IN4, LOW);
  }
  // Both dark → stop
  else {
    digitalWrite(IN1, LOW);
    digitalWrite(IN2, LOW);
    digitalWrite(IN3, LOW);
    digitalWrite(IN4, LOW);
  }
}
