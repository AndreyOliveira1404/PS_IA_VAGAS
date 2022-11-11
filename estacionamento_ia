#include <Adafruit_LiquidCrystal.h>

int dist = 0;

int dist2 = 0;

int vagas = 0;

int vagasO = 0;

long readUltrasonicDistance(int triggerPin, int echoPin)
{
  pinMode(triggerPin, OUTPUT);  // Clear the trigger
  digitalWrite(triggerPin, LOW);
  delayMicroseconds(2);
  // Sets the trigger pin to HIGH state for 10 microseconds
  digitalWrite(triggerPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(triggerPin, LOW);
  pinMode(echoPin, INPUT);
  // Reads the echo pin, and returns the sound wave travel time in microseconds
  return pulseIn(echoPin, HIGH);
}

Adafruit_LiquidCrystal lcd_1(0,1,10,11,12,13);

void setup()
{
  pinMode(6, OUTPUT);
  pinMode(7, OUTPUT);
  pinMode(8, OUTPUT);
  pinMode(9, OUTPUT);
  lcd_1.begin(16, 2);
}

void loop()
{
  vagas = 2;
  vagasO = 0;
  dist2 = 0.01723 * readUltrasonicDistance(3, 2);
  dist = 0.01723 * readUltrasonicDistance(5, 4);
  if (dist < 200) {
    digitalWrite(6, HIGH);
    digitalWrite(7, LOW);
    vagas = (vagas - 1);
    vagasO = (vagasO + 1);
  } else {
    digitalWrite(7, HIGH);
    digitalWrite(6, LOW);
  }
  if (dist2 < 200) {
    digitalWrite(8, HIGH);
    digitalWrite(9, LOW);
    vagas = (vagas - 1);
    vagasO = (vagasO + 1);
  } else {
    digitalWrite(8, LOW);
    digitalWrite(9, HIGH);
  }
  
  if (vagas == 2) {
    lcd_1.setCursor(0, 0);
    lcd_1.print("Vagas Livres: ");
    lcd_1.setCursor(15, 0);
    lcd_1.print(vagas);
    
    lcd_1.setCursor(0, 1);
    lcd_1.print("Vagas Ocupadas: ");
    lcd_1.setCursor(15, 1);
    lcd_1.print(vagasO);
  } else if (vagas == 1) {
    lcd_1.setCursor(0, 0);
    lcd_1.print("Vagas Livres: ");
    lcd_1.setCursor(15, 0);
    lcd_1.print(vagas);
    
    lcd_1.setCursor(0, 1);
    lcd_1.print("Vagas Ocupadas: ");
    lcd_1.setCursor(15, 1);
    lcd_1.print(vagasO);
  } else {
  	lcd_1.setCursor(0, 0);
    lcd_1.print("Vagas Livres: ");
    lcd_1.setCursor(15, 0);
    lcd_1.print(vagas);
    
    lcd_1.setCursor(0, 1);
    lcd_1.print("Vagas Ocupadas: ");
    lcd_1.setCursor(15, 1);
    lcd_1.print(vagasO);
  }
  delay(10); // Delay a little bit to improve simulation performance
}
