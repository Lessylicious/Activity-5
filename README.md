/*Activity:5
Create a distance measuring device that:
1. turn RED LED light and Buzzer ON if distance is below 10cm;
2. turn Yellow LED light if distance is below 11cm-20cm
3. turn Green LED light if distance is more than 20cm*/
//Lester Calub BSIT 2B

//Pins
int trigPin= 12;
int echoPin= 11;
const int red=10;
const int yellow=9;
int green=8;
#define buzzer 7

long duration;
float cm;
float inches;


void setup(){
  
Serial.begin (9600);
pinMode (trigPin, OUTPUT);
pinMode (echoPin, INPUT);
pinMode(buzzer, OUTPUT);
}



void loop(){
digitalWrite(trigPin, LOW);
delayMicroseconds(5);
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
             
duration= pulseIn (echoPin,HIGH);          
             
cm = (duration/2) / 29.1;
inches = (duration/2) / 74;
             

Serial.print(inches);
Serial.print("in, ");           
Serial.print(cm);
Serial.print("cm");
Serial.println();
  
  //Red LED
   if(cm<10){
    digitalWrite(red,HIGH);
    digitalWrite(green,LOW);
    digitalWrite(yellow,LOW);
    digitalWrite(buzzer,HIGH);
     digitalWrite(buzzer,LOW);
  }
  //Yellow LED
   if (cm>11 && cm<20){
    digitalWrite(red,LOW);
    digitalWrite(green,LOW);
    digitalWrite(yellow,HIGH); 
     digitalWrite(buzzer,LOW);
  }
  //Green LED
  if (cm > 20){
    digitalWrite(red,LOW);
    digitalWrite(green,HIGH);
    digitalWrite(yellow,LOW);
    digitalWrite(buzzer,LOW);
 
  
  
  }
}

