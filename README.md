# Arduino Digital Analog Control System Button Potentiometer

This project demonstrates the design and implementation of both digital and analog input systems using an Arduino. A push button is used as a digital input to toggle an LED, while a potentiometer acts as an analog sensor to control the brightness of another LED. The system is built on a breadboard and programmed using Arduino IDE, making it suitable for beginners learning embedded systems and basic electronics.

## Project Overview
The project consists of two main parts:

### Digital System:
A push button controls an LED using toggle logic (press once to turn ON, press again to turn OFF).

### Analog System:
A potentiometer adjusts the brightness of another LED using PWM.

## Components Used
- Arduino Uno
- Breadboard
- Push Button (Digital Input)
- Potentiometer (Analog Sensor)
- 2 × LEDs
- 2 × 220Ω Resistors (for LEDs)
- 10kΩ Resistor (for button - pull-down)
- Jumper Wires

## Circuit Configuration

### Digital Circuit (Button):
- Button connected to Pin 2
- 10kΩ resistor connected as pull-down
- LED connected to Pin 8 with 220Ω resistor

### Analog Circuit (Potentiometer):
- Middle pin connected to A0
- Side pins connected to 5V & GND
- LED connected to Pin 9 (PWM) with 220Ω resistor

## Wiring Summary

### Digital:
5V → Button → Pin 2  
Pin 2 → 10kΩ → GND  

Pin 8 → 220Ω → LED → GND  

### Analog:
Potentiometer:  
5V → one side  
GND → other side  
Middle → A0  

Pin 9 → 220Ω → LED → GND  

## Arduino Code

```cpp
int buttonPin = 2;
int ledPin = 8;
int ledState = 0;     
int lastButtonState = 0;

int potPin = A0;
int ledPins = 9;

void setup() {
  pinMode(buttonPin, INPUT);
  pinMode(ledPin, OUTPUT);
  pinMode(ledPins, OUTPUT);
}

void loop() {
  int buttonState = digitalRead(buttonPin);

  if (buttonState == 1 && lastButtonState == 0) {
    ledState = !ledState;  
    delay(200); 
  }

  digitalWrite(ledPin, ledState);
  lastButtonState = buttonState;

  int value = analogRead(potPin);   
  int brightness = map(value, 0, 1023, 0, 255);
  analogWrite(ledPins, brightness); 
}
```

## Circuit Diagram
![Planetary Gear Assembly](imeges/Projest-Digram.png)
