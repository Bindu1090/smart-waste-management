#include <SoftwareSerial.h> 
SoftwareSerial blue(2,3); //rx2 tx 3//
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);
//LiquidCrystal_I2C lcd(0x3F, 1sensor3, 2);
int time = 0;
int buzzer=8;
int sensor1=4;
int sensor2=5;
int sensor3=6;
int sensor4=7;

void setup() 
{
  Serial.begin(115200);
  blue.begin(9600); 
  lcd.init();
  lcd.backlight();  
  lcd.setCursor(0, 0);
  lcd.print("Dustbin Managment");
  delay(1500);

  lcd.clear();
  pinMode(sensor4, INPUT);
  pinMode(sensor3, INPUT);
  pinMode(sensor2, INPUT);
  pinMode(sensor1, INPUT);
  pinMode(buzzer,OUTPUT);
} 

void loop() 
{
 
  lcd.setCursor(0, 0);
  sensor();
  delay(500);
  
}

void sensor()
{                                                                                                                                                                                                                                                                                                                                                                                                                                                           


if(digitalRead(sensor1)==LOW)   

{
    lcd.setCursor(0,0);
    lcd.print("1 FULL ");  
    delay(100);
    digitalWrite(buzzer,HIGH);
    delay(200);
    digitalWrite(buzzer,LOW);
    blue.print("DUSTBIN 1:- FULL");
    blue.println("\n");
    
  }

else
{
lcd.setCursor(0,0);
lcd.print("1 EMPTY");  
    
}

if(digitalRead(sensor2)==LOW)   

{
    lcd.setCursor(9,0);
    lcd.print("2 FULL ");  
    delay(100);
    digitalWrite(buzzer,HIGH);
    delay(200);
    digitalWrite(buzzer,LOW);
    blue.print("DUSTBIN 2:- FULL");
    blue.println("\n");
    
  }

else
{
lcd.setCursor(9,0);
    lcd.print("2 EMPTY");     
   
}

if(digitalRead(sensor3)==LOW)   

{
    lcd.setCursor(0,1);
    lcd.print("3 FULL ");  
    delay(100);
    digitalWrite(buzzer,HIGH);
    delay(200);
    digitalWrite(buzzer,LOW);
     blue.print("DUSTBIN 3:- FULL");
    blue.println("\n");
  }

else
{
lcd.setCursor(0,1);
    lcd.print("3 EMPTY");      
}

if(digitalRead(sensor4)==LOW)   

{
    lcd.setCursor(9,1);
    lcd.print("4 FULL  ");  
    delay(100);
    digitalWrite(buzzer,HIGH);
    delay(200);
    digitalWrite(buzzer,LOW);
    blue.print("DUSTBIN 4 :- FULL");
    blue.println("\n");
    
  }

else
{
lcd.setCursor(9,1);
lcd.print("4 EMPTY");  
  
}
    
}
  
