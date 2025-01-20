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

## Steps to Use

1. **Connect the IR sensor to the Arduino**:
   - **VCC** → 5V  
   - **GND** → GND  
   - **OUT** → Digital Pin 8 (or your chosen pin)  
2. Open the **Serial Monitor** in the Arduino IDE.  
3. Press buttons on your remote and note down the hex codes displayed in the Serial Monitor.  
4. Replace the placeholder codes in the car’s main program with these hex codes.

---

## Predefined Remote Codes

| **Button**      | **Hex Code** | **Car Action**     |
|------------------|-------------|--------------------|
| **Up (↑)**       | `0xFFA25D`  | Move Forward       |
| **Down (↓)**     | `0xFFE21D`  | Move Backward      |
| **Left (←)**     | `0xFF22DD`  | Turn Left          |
| **Right (→)**    | `0xFFC23D`  | Turn Right         |
| **Stop (⏹️)**      | `0xFF02FD`  | Stop Car           |

---

## Circuit Diagram

### **Connections**
- **IR Sensor**:
  - **VCC** → 5V  
  - **GND** → GND  
  - **OUT** → Arduino pin defined in the code (8 by default).  
- **L298N Motor Driver**:
  - **ENA/ENB** → PWM pins for speed control  
  - **IN1, IN2, IN3, IN4** → Digital pins for motor direction  
  - **Motors** → OUT1/OUT2 and OUT3/OUT4 terminals  
- **Arduino Uno**:
  - Connect power and ground to the appropriate pins.  
  - Upload the program using USB.  

---

## Installation

1. Clone this repository:  
   ```bash
   git clone https://github.com/inayatrahimdev/Arduino-Remote-Controlled-Car.git

## Installation

1. Install the **IRremote** library in the Arduino IDE.  
2. Open the `.ino` file in the Arduino IDE.  
3. Upload the code to your Arduino Uno.  
4. Assemble the circuit as per the diagram.

---

## How It Works

1. **Remote Signal Decoding**: The IR sensor decodes signals from the remote into hex codes.  
2. **Hex Code Matching**: The program compares received codes with predefined values.  
3. **Motor Control**: Based on the matched code, the L298N motor driver activates the motors to execute the desired action.

---

## Future Enhancements

- Add obstacle detection using ultrasonic sensors.  
- Implement Bluetooth or Wi-Fi control.  
- Introduce a speed control mechanism using PWM.

---

## Contributing

Contributions are welcome! Feel free to fork the repository, create a pull request, or submit issues.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Author

👤 **Inayat Rahim**  
📧 [inayatrahim006@gmail.com](mailto:inayatrahim006@gmail.com)  
🔗 [GitHub Profile](https://github.com/inayatrahimdev)
