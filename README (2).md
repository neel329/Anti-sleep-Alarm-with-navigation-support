# Anti-Sleep Alarm for Drivers using Arduino Nano and Relay Module

## Overview

This project demonstrates how to create an anti-sleep alarm system for drivers using an Arduino Nano and a Relay Module. The system detects signs of drowsiness or fatigue in the driver and triggers an alarm to alert the driver to stay awake and attentive.

## Hardware Requirements

- Arduino Nano
- Relay Module
- IR (Infrared) Sensor Module
- Buzzer or Piezo Speaker
- Power Supply (Battery or 5V USB)
- Connecting Wires
- Optional: Enclosure for the hardware

## Installation and Setup

1. **Install the Arduino IDE**: If you haven't already, download and install the Arduino IDE from the [official Arduino website](https://www.arduino.cc/en/software).

2. **Connect Hardware**:

    - Connect the IR Sensor Module to the Arduino Nano as follows:
        - VCC to 5V
        - GND to GND
        - OUT to a digital pin (e.g., D2)

    - Connect the Relay Module to the Arduino Nano:
        - VCC to 5V
        - GND to GND
        - IN to a digital pin (e.g., D3)

    - Connect the Buzzer to the Relay Module:
        - Connect one end of the buzzer to NO (Normally Open) and the other end to COM (Common) on the Relay Module.

3. **Upload the Code**:

    - Open the Arduino IDE and create a new sketch.
    - Copy and paste the Arduino code (provided below) into the sketch.
    - Select the appropriate board (Arduino Nano) and port from the Tools menu.
    - Click the "Upload" button to upload the code to the Arduino Nano.

4. **Power Supply**:

    - Power the Arduino Nano using a 5V power supply (e.g., a USB connection or a battery).

5. **Test the System**:

    - Place the IR sensor in a location where it can monitor the driver's eye movements (e.g., near the driver's eye level).
    - When the driver starts to get drowsy and closes their eyes for an extended period, the IR sensor will trigger the relay, which activates the buzzer, alerting the driver.

## Arduino Code

Here is the Arduino code to implement the anti-sleep alarm system:

```arduino
const int irSensorPin = 2; // Connect the IR sensor to digital pin 2
const int relayPin = 3;    // Connect the relay to digital pin 3
const int buzzerPin = 4;   // Connect the buzzer to digital pin 4

void setup() {
  pinMode(irSensorPin, INPUT);
  pinMode(relayPin, OUTPUT);
  pinMode(buzzerPin, OUTPUT);
}

void loop() {
  int irValue = digitalRead(irSensorPin);
  
  if (irValue == LOW) {
    // IR sensor detects an obstacle (driver's eyes closed)
    digitalWrite(relayPin, HIGH); // Activate the relay
    digitalWrite(buzzerPin, HIGH); // Turn on the buzzer
    delay(1000); // Buzz for 1 second (adjust as needed)
    digitalWrite(relayPin, LOW);  // Deactivate the relay
    digitalWrite(buzzerPin, LOW); // Turn off the buzzer
  }
}
```

## Customization

You can customize this project by:

- Adjusting the sensitivity of the IR sensor or changing its placement to better suit your needs.
- Modifying the alarm duration and sound pattern by altering the delay and buzzer control in the code.
- Adding additional features, such as data logging or integrating with a mobile app for remote monitoring.


## Acknowledgments

- [Arduino Official Website](https://www.arduino.cc/)
- [IR Sensor Module Datasheet](https://components101.com/ir-sensor-module-working-pinout-datasheet)
- [Relay Module Tutorial](https://lastminuteengineers.com/arduino-relay-control-tutorial/)
