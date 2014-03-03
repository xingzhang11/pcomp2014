/*Mar3 reading temperature data from color*/
// 1 Blue LED * 3 Red LEDS stand for cold and hot seperately
// March 3, 2014 by Xing Zhang 

const int sensorPin = A0;
const float baselineTemp = 160; 

void setup(){
  Serial.begin(9600);	
  for(int pinNumber=2;pinNumber<6;pinNumber++){ //define my leds
    pinMode(pinNumber,OUTPUT);
    digitalWrite(pinNumber,LOW);
  }	
}

void loop(){
  int sensorVal	=analogRead(sensorPin); 
  Serial.print("Sensor Value:");
  Serial.print(sensorVal); //check the temperature

//if it is colder than the default temp, blue lights up
  if(sensorVal<baselineTemp){ 
    digitalWrite(2,HIGH);
    digitalWrite(3,LOW);
    digitalWrite(4,LOW);
    digitalWrite(5,LOW);
  }	
  //the degree of the hotness
  else	if(sensorVal>=baselineTemp && sensorVal<baselineTemp+2){
    digitalWrite(2,LOW);
    digitalWrite(3,HIGH);
    digitalWrite(4,LOW);
    digitalWrite(5,LOW);
  }	
  else	if(sensorVal>=baselineTemp+2 && sensorVal<baselineTemp+4){
    digitalWrite(2,LOW);
    digitalWrite(3,HIGH);
    digitalWrite(4,HIGH);
    digitalWrite(5,LOW);
  }	
  else	if(sensorVal>=baselineTemp+4){
    digitalWrite(2,LOW);
    digitalWrite(3,HIGH);
    digitalWrite(4,HIGH);
    digitalWrite(5,HIGH);
  }
  delay(100);
}






