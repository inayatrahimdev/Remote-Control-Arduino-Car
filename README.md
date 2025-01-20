# **Arduino Remote-Controlled Car**

Welcome to the **Arduino Remote-Controlled Car** project repository! 🚗 This project demonstrates the design and implementation of a fully functional remote-controlled car using an Arduino microcontroller, IR sensors, and an IR remote. The car’s movement—forward, backward, left, right, and stop—is controlled using decoded IR signals from a remote.

---

## **Features**
- **Remote-Controlled Navigation**: Seamless control via an IR remote for various car movements.
- **Customizable Codes**: Use any IR remote by identifying and integrating its unique codes.
- **Efficient Motor Control**: Smooth and responsive handling with optimized motor operations.
- **Expandable Design**: Add more features like obstacle detection or advanced navigation.
- **User-Friendly Setup**: Easy-to-follow instructions and straightforward assembly.

---

## **Technologies Used**
- **Arduino Uno**: Core microcontroller for signal decoding and motor control.
- **IR Sensors (TSOP1738)**: Decode IR remote signals and transmit commands to the Arduino.
- **IR Remote**: Send signals to control the car's movement.
- **L298N Motor Driver**: Manage power delivery to motors for precise movements.
- **DC Motors**: Drive the wheels for forward, backward, and turning motions.
- **Battery Power**: Reliable energy source for uninterrupted operation.

---

## **Hardware Requirements**
1. **Arduino Uno** microcontroller
2. **IR Sensors (TSOP1738)** for decoding remote signals
3. **IR Remote Control**
4. **L298N Motor Driver**
5. 2 **DC Motors** with compatible wheels
6. Power supply (battery)
7. Connecting wires and a breadboard

---

## **Software Requirements**
1. **Arduino IDE** (latest version)
2. **IRremote Library**:
   - Install via Arduino IDE: **Sketch > Include Library > Manage Libraries > Search "IRremote" > Install**
3. **Serial Monitor** for debugging and identifying remote codes (optional)

---

## **Finding Special IR Codes**
Before programming the car, identify the hex codes for your IR remote buttons. These codes will be assigned to specific actions (forward, backward, left, right, and stop).

### **IR Code Finder Code**
Upload the following code to your Arduino to print the hex codes of your IR remote buttons to the Serial Monitor:

```cpp
#include <IRremote.h>
const int RemotePin = 8;  // Pin connected to IR sensor
IRrecv irrecv(RemotePin);
decode_results results;

void setup() {
  Serial.begin(9600);
  irrecv.enableIRIn();  // Start the IR receiver
}

void loop() {
  if (irrecv.decode(&results)) {
    Serial.println(results.value, HEX);  // Print the hex code
    delay(200);
    irrecv.resume();  // Prepare for the next code
  }
}
