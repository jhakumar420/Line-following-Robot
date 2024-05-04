# Line-following-Robot
// Define pins for motor driver
const int motorA1 = 2;  
const int motorA2 = 3; 
const int motorB1 = 4;  
const int motorB2 = 5;  

// Define pins for IR sensors
const int leftIR = A0;   
const int rightIR = A1; 

// Define threshold values for detecting black line
const int threshold = 250;

void setup() {
  pinMode(motorA1, OUTPUT);
  pinMode(motorA2, OUTPUT);
  pinMode(motorB1, OUTPUT);
  pinMode(motorB2, OUTPUT);
  
  pinMode(leftIR, INPUT);
  pinMode(rightIR, INPUT);
}

void loop() {
  int leftValue = analogRead(leftIR);
  int rightValue = analogRead(rightIR);
  
  // If both sensors detect black, move forward
  if (leftValue < threshold && rightValue < threshold) {
    moveForward();
  }
  // If left sensor detects black, turn right
  else if (leftValue < threshold) {
    turnRight();
  }
  // If right sensor detects black, turn left
  else if (rightValue < threshold) {
    turnLeft();
  }
  // If both sensors detect white, stop
  else {
    stopMoving();
  }
}

// Function to move forward
void moveForward() {
  digitalWrite(motorA1, HIGH);
  digitalWrite(motorA2, LOW);
  digitalWrite(motorB1, HIGH);
  digitalWrite(motorB2, LOW);
}

// Function to turn  left
void turnLeft() {
  digitalWrite(motorA1, LOW);
  digitalWrite(motorA2, HIGH);
  digitalWrite(motorB1, HIGH);
  digitalWrite(motorB2, LOW);
}

// Function to turn  right
void turnRight() {
  digitalWrite(motorA1, HIGH);
  digitalWrite(motorA2, LOW);
  digitalWrite(motorB1, LOW);
  digitalWrite(motorB2, HIGH);
}

// Function to stop the robot
void stopMoving() {
  digitalWrite(motorA1, LOW);
  digitalWrite(motorA2, LOW);
  digitalWrite(motorB1, LOW);
  digitalWrite(motorB2, LOW);
}

  line-following robot built using 2 IR sensors and an Arduino Uno powered by an L298N motor driver! 🤖🔍 With this setup, the robot is programmed to effortlessly track a black line, showcasing the perfect blend of hardware and software in action.
