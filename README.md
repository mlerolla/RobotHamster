RobotHamster
============

#include <Servo.h> 
Servo servoLeft;
Servo servoRight;
// set the output of the sensor to a pin A4 of the arduino
//int sensorPin = 4;
int positionPin = 2;
// the sum of 4 values of the sensor read by the arduino
int val;
// set the pin 9 to control a motor
int motor1Pin = 9;
// set the pin 11 to control the other motor
int motor2Pin = 11;
int ledPin = 13;
//initialize the arduino
void setup(){
 //set the rate to read or write to the Serial port
  Serial.begin(9600);
  //set the mode of the pins
 servoLeft.attach(motor1Pin);
 servoRight.attach(motor2Pin);
  pinMode(ledPin,OUTPUT);
  //clear the Serial port
  Serial.flush();
 }
 // the principal program
 void loop(){
   Serial.println(analogRead(positionPin));
   if(analogRead(positionPin) <1000){
   // set the valeur of the motor1Pin and motor2Pin to control the 2 motors
   //to let it advance
servoLeft.write(30);
servoRight.write(150);
  int i = 0;
   val = 0;
   collect the values of the sensor 4 times and calculate the average
  for(i=0;i <=3;i++){
     val  = val + analogRead(sensorPin);
   }
   if the sensor detect an obstacle in front
   if(val/4 > 300){
         analogWrite(motor1Pin,220);
      analogWrite(motor2Pin,90);
          int i =0;
     for(i=0;i<=5;i++){
     digitalWrite(ledPin,HIGH);
      delay(100);
      digitalWrite(ledPin,LOW);
      delay(50);
    }
     //advance in an opposite direction for 1 second

     delay(1000);
     //turning for 1.5 seconds
    bbanalogWrite(motor1Pin,0);
      analogWrite(motor2Pin,90);

     delay(1500);
  }
    delay(500);
   }
      else{
        servoLeft.write(150);
servoRight.write(30);

         int i =0;
      for(i=0;i<=5;i++){
      digitalWrite(ledPin,HIGH);
      delay(100);
      digitalWrite(ledPin,LOW);
      delay(50);}
      
      delay(1000);
     //turning for 1.5 seconds
             servoLeft.write(0);
servoRight.write(150);
      analogWrite(motor1Pin,0);
      analogWrite(motor2Pin,90);

      delay(1500);
      }
     
   
    //present the average value in the serial port
   Serial.println(val/4);
   
 }
