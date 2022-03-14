# Robot Arm Project
That's what I named when I was in high school senior, July.
This is a code for Arduino Robot Arm.
It can move every way in the area of hemisphere.
Also you can pick something up with your tongs connected to the servo3 motor.
I refered to the Youtube video of the part of linking three servo motors.




#include <Servo.h>

Servo servo1;
Servo servo2;

int joyX =0;
int joyY =1;
int joyVal;

#define LEFT 10
#define RIGHT 11

int ServoPin = 2;
Servo servo3;
int ange = 90;
int angleStep = 10;


void setup()
{
 servo1.attach(3);
 servo2.attach(5);
 servo3.attach(2);
 pinMode(LEFT, INPUT_PULLUP);
 pinMode(RIGHT, INPUT_PULLUP);
 servo3.write(angle);

}

void loop()
{
 joyVal = analogRead(joyX);
 joyVal = map (joyVal, 0, 1023, 0 170);
 servo1.write(joyVal);
 delay(10);
 
 while(digitalRead(RIGHT) == LOW){
 
  if(angle > 0 && angle <= 180){
   angle = angle - angleStep;
   if(angle < 0) {
    angle = 0;
   }else{
   servo3.write(angle);
   }
  }
 delay(100);
 }
 
 while(digitalRead(LEFT) == LOW) {
  
  if(angle >= 0 && angle <= 180){
   angle = angel + angleStep;
   if(angle > 180){
    angle = 180;
   }
  }
  delay(100);
 }
 
}


 
 
 
