# USRC Welcome Week Challenge - Pixel Chaser

## Getting started

TinkerCAD link: https://www.tinkercad.com/

You're going to need to have the following things ready before you can build this project

- A TinkerCAD account (a google login should work)

Once your account is set up, you can get started.

## Bringing Up The Circuit Builder

1. Go the **Circuit** tab on the left hand side and click *Create a new circuit*

On your right hand side will be your components that will be available to bring into the builder. Simply drag and drop a component to bring it into the enviornment

2. Bring the following components into the environment

- Arduino Uno R3
- Breadboard
- Servo
- Ultrasonic Sensor HC-SR04

## Setting up the Circuit

1. Attach your GND line on your bread board your GND on your Arduino. 
2. Attach your Power line on your breadboard to 5V on your Arduino
3. On your ultrasonic sensor, connect VCC to your power line and GND to ground.
4. Then connect TRIG to pin 5 on your Arduino
5. Connect ECHO to pin 4 on your Arduino
6. Connect your power and ground pins on your servo to your power and ground lines respectively
7. Connect your Signal pin to pin 3 on your Arduino

## Writing the Code
For the sake of time, you're just going to copy the code into your Arduino.

```
//Sketch created by Akshay Joseph
#include<Servo.h>
#define echoPin 4
#define trigPin 5
Servo Myservo;
int pos;
int long duration;
int distance;



void setup(){ 
  Myservo.attach(3);
  pinMode(echoPin,INPUT);
  pinMode(trigPin,OUTPUT);

}
  
void loop(){
  digitalWrite(trigPin,LOW);
  delayMicroseconds(2); 
  digitalWrite(trigPin,HIGH);
  delayMicroseconds(10); 
  digitalWrite(trigPin,LOW);
  duration=pulseIn(echoPin,HIGH);
  distance=(duration*0.034/2);

  if(distance<=80){
      for(pos=180;pos>=0;pos--){
        Myservo.write(pos);
        delay(111.1);
      }
  }


  else{
      Myservo.write(180);
  }
  delay(200);
  
}
```



