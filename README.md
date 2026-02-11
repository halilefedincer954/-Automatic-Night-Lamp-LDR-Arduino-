
# 🌙 Automatic Night Lamp (LDR + Arduino)

This project creates an automatic night lamp using an LDR (photoresistor) and Arduino.

When the environment gets dark, the LED turns ON.
When it becomes bright, the LED turns OFF.

## 🔧 Components Used

- Arduino Uno
- LDR (Photoresistor)
- 10kΩ resistor
- LED
- 220Ω resistor (for LED)
- Breadboard
- Jumper wires

- ## 📷 Circuit Image

![Circuit Image] Circuit Image.png

## ⚡ Circuit Connection

Voltage Divider Setup:

5V ---- LDR ---- A0 ---- 10kΩ ---- GND

LED Connection:

Digital Pin 2 ---- 220Ω ---- LED ---- GND

## 💻 Arduino Code

```cpp
#define LED 2
#define LDR A0

void setup() {
  Serial.begin(9600);
  pinMode(LED, OUTPUT);
}

void loop() {
  int value = analogRead(LDR);
  Serial.println(value);

  if (value < 50) {   // Adjust threshold if needed
    digitalWrite(LED, HIGH);  // Dark -> LED ON
  } else {
    digitalWrite(LED, LOW);   // Bright -> LED OFF
  }

  delay(200);
}
