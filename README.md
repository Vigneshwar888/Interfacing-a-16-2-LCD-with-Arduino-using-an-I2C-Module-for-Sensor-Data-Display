# EXP — INTERFACING A 16×2 LCD WITH ARDUINO USING AN I2C MODULE FOR SENSOR DATA DISPLAY

## Aim

To interface a **16×2 LCD display with Arduino using an I2C module** and display sensor data on the LCD.

## Objectives

- To understand the operation of a 16×2 LCD.
- To interface the LCD with Arduino using an I2C module.
- To reduce the number of GPIO pins required for LCD communication.
- To read sensor data using Arduino.
- To display the sensor readings on the LCD.

## Hardware / Software Tools Required

### Hardware

- Arduino UNO
- 16×2 LCD Display
- I2C LCD Module (PCF8574-based)
- DHT11 Temperature and Humidity Sensor
- Breadboard
- Jumper wires
- USB cable

### Software

- Arduino IDE
- Arduino C/C++ programming language
- LiquidCrystal_I2C library
- DHT sensor library

## Components

### 16×2 LCD
### I2C Module
### Circuit Connections
### I2C Communication
### Working Principle

1. The DHT11 sensor measures temperature and humidity.
2. Arduino reads the sensor values through the digital data pin.
3. The Arduino processes the received sensor data.
4. The processed values are sent to the LCD through the I2C interface.
5. The LCD displays the temperature on one line.
6. The humidity is displayed on the second line.
7. The readings are periodically updated.

## Arduino Program
```
#include <Adafruit_LiquidCrystal.h>

Adafruit_LiquidCrystal lcd(0);

int trig = 8;
int echo = 11;

float distance;
long duration;

void setup()
{
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);

  lcd.begin(16, 2);

  lcd.setCursor(0, 0);
  lcd.print("Distance =");
}

void loop()
{
  digitalWrite(trig, LOW);
  delayMicroseconds(2);

  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);

  duration = pulseIn(echo, HIGH);

  distance = duration * 0.0343 / 2;

  lcd.setCursor(0, 1);
  lcd.print("                ");  // clear only old value
  lcd.setCursor(0, 1);
  lcd.print(distance, 1);
  lcd.print(" cm");

  delay(5000);
}
```
## Observation

<img width="899" height="1599" alt="WhatsApp Image 2026-09-25 at 10 42 26 AM" src="https://github.com/user-attachments/assets/a7be6858-fb59-4a20-8bc5-87a02b0a1662" />

## Result

Thus, the **16×2 LCD was successfully interfaced with Arduino UNO using an I2C module**, and the temperature and humidity values obtained from the DHT11 sensor were successfully displayed on the LCD. The experiment demonstrates the use of **I2C communication for efficient sensor-data display** in embedded and IoT applications.
