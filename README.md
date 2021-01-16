# Dogbot
<h3>Sample code</h3>
<p>#include "LedControl.h"<br>
#include "binary.h" <br>
LedControl lc=LedControl(7,6,5,4);   <br>
// happy face   <br>
byte hf[8]= {B00111100,B01000010,B10100101,B10000001,B10100101,B10011001,B01000010,B00111100};    <br>
// neutral face   <br>
byte nf[8]={B00111100, B01000010,B10100101,B10000001,B10111101,B10000001,B01000010,B00111100};    <br>
// sad face    <br>
byte sf[8]= {B00111100,B01000010,B10100101,B10000001,B10011001,B10100101,B01000010,B00111100};  <br>
// defines pins numbers   <br>
int l,r;                                   // initializing two variables l & r for storing inputs from Light sensors.  <br>
void setup()  <br>
{   <br>
  pinMode(10,OUTPUT);                     //10,11 for left motor  <br>
  pinMode(11,OUTPUT);  <br>
  pinMode(12,OUTPUT);                     //12,13 for right motor  <br>
  pinMode(13,OUTPUT);   <br>
  pinMode(2,OUTPUT);  <br>
  pinMode(5,OUTPUT);  <br>
  pinMode(4,INPUT);                       // At pin no:4 we will connect the right light sensor which will act as an input device  <br>
  pinMode(3,INPUT);                       // At pin no:3 we will connect the left light sensor which will act as input device.   <br>
  digitalWrite(2,HIGH);   <br>
  digitalWrite(5,LOW);    <br>  
}   <br>
void loop()   <br>
{   <br>
  r=digitalRead(4);                       // Reading the input of right sensor and storing the value in pin no:4 of Arduino  <br>
  l=digitalRead(3);                       // Reading the input of left sensor and storing the value in pin no:3 of Arduino   <br>
 lc.setRow(0,0,hf[0]);  <br>
  lc.setRow(0,1,hf[1]);  <br>
  lc.setRow(0,2,hf[2]);   <br>
  lc.setRow(0,3,hf[3]);  <br>
  lc.setRow(0,4,hf[4]);  <br>
  lc.setRow(0,5,hf[5]);  <br>
  lc.setRow(0,6,hf[6]);   <br>
  lc.setRow(0,7,hf[7]);  <br>
delay(1000);    <br>

  if(r==HIGH && l==HIGH)                  // If both left & right sensor are on white surface  <br>
  {                                       // the left & right motor will go forward  <br>
    digitalWrite(10,HIGH);   <br>
    digitalWrite(11,LOW);  <br>
    digitalWrite(12,HIGH);  <br>
    digitalWrite(13,LOW);  <br>
  }  <br>
  else if(l==HIGH && r==LOW)             // If left sensor is on white and right sensor is on black surface  <br>
  {                                      // the left motor will go forward & right motor will go backward  <br>
    digitalWrite(10,HIGH);                 <br>
    digitalWrite(11,LOW);  <br>
    digitalWrite(12,LOW);  <br>
    digitalWrite(13,LOW);   <br>
  }  <br>
  else if(l==LOW && r==HIGH)            // If left sensor is on white and right sensor is on black surface  <br>
  {                                     // the left motor will go backward & right motor will go forward.  <br>
    digitalWrite(10,LOW);  <br>
    digitalWrite(11,LOW);  <br>
    digitalWrite(12,HIGH);  <br>
    digitalWrite(13,LOW);   <br>
   }  <br>
    else                           // the last condition is, if both left & right light sensor are on black surface  <br>
  {                                // the left & right will stop. <br>
    digitalWrite(10,HIGH);  <br>
    digitalWrite(11,HIGH);  <br>
    digitalWrite(12,HIGH);  <br>
    digitalWrite(13,HIGH);  <br>
   }  <br>
}  <br>
    
</p>
