# Smart Home Automation System

## Project Overview
This project focuses on building a **Smart Home Automation System** that enhances convenience, safety, and energy efficiency. It integrates sensors and automation technology to optimize the use of electricity, reduce manual effort, and improve the overall user experience. 
![WhatsApp Image 2025-01-03 at 13 38 34_37a7b6d2](https://github.com/user-attachments/assets/8fb27b32-abcf-4fd6-ab9c-9a27865603d8)

## Key Features

### 1. **Automatic Day-Night Light Control**
- **Description**: Outdoor lights are automatically controlled based on natural light levels using an **LDR (Light Dependent Resistor)** sensor. Lights turn off during the day and on at night without manual intervention.
- **Benefits**: 
  - Reduces electricity consumption.
  - Ensures outdoor areas are always well-lit during the night for safety.

### 2. **Indoor Light and Fan Automation**
- **Description**: Indoor lights and fans are automated using an **Ultrasonic Sonar Sensor HC-SR04**, which detects human presence.
- **Functionality**: Lights and fans automatically turn on when a person is detected and turn off when no one is present.
- **Benefits**:
  - Saves energy by operating appliances only when needed.
  - Provides a hands-free, convenient user experience.

### 3. **Keyless Access**
- **Description**: Secure, keyless entry is implemented to replace traditional locks. Advanced authentication methods ensure only authorized individuals can access the home.
- **Benefits**:
  - Enhances security by eliminating risks associated with lost or stolen keys.
  - Saves time and offers convenience.

## Advantages
- **Energy Efficiency**: Optimizes electricity usage, reducing costs.
- **Safety**: Prevents accidents like electrical hazards and ensures secure access.
- **User Convenience**: Reduces manual tasks and offers a seamless living experience.

## System Components
1. **LDR Sensor**: For detecting ambient light levels to control outdoor lighting.
2. **Ultrasonic Sonar Sensor HC-SR04**: For detecting human presence to automate indoor appliances.
3. **Microcontroller (e.g., Arduino/ESP8266)**: The central unit for processing sensor data and controlling devices.
4. **Relay Modules**: To control high-voltage appliances like lights and fans.
5. **Keyless Access System**: Could include RFID, biometric, or password-based access systems.
6. **Power Supply Unit**: Provides necessary power to all components.

## Project Workflow
1. **Design**:
   - Plan sensor placements and wiring.
   - Identify the appliances to be automated.
2. **Development**:
   - Program the microcontroller to process sensor data.
   - Develop the logic for day-night detection, presence-based automation, and keyless access.
3. **Integration**:
   - Connect sensors, relays, and appliances.
   - Test individual components to ensure functionality.
4. **Testing**:
   - Test the complete system under various scenarios (e.g., day, night, occupied, unoccupied).
5. **Deployment**:
   - Install the system in the intended location.
   - Provide user instructions for operating the system.

## Future Improvements
- **Integrating Voice Assistants**: Add compatibility with Alexa or Google Assistant for voice control.
- **Remote Control Capabilities**: Develop mobile apps for system control.
- **Machine Learning Integration**: Implement algorithms to predict user habits for optimized automation.

## How to Use
1. **Automatic Day-Night Light Control**: The outdoor lights will function autonomously; no action is required.
2. **Indoor Automation**: Lights and fans will activate automatically based on your presence.
3. **Keyless Access**: Follow the authentication method configured during installation (e.g., use your RFID card, biometric scan, or password).

## Conclusion
This **Smart Home Automation System** provides a modern, energy-efficient, and user-friendly solution for home management. By automating key aspects of daily life, it reduces electricity costs, enhances safety, and offers unparalleled convenience.


---

## Example Code
### Arduino Code for Light Control Using LDR Sensor
```cpp
int LDR_PIN = A0; // LDR connected to analog pin
int LIGHT_PIN = 7; // Light connected to digital pin

void setup() {
  pinMode(LIGHT_PIN, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int ldrValue = analogRead(LDR_PIN);
  Serial.println(ldrValue);

  if (ldrValue < 500) { // Adjust threshold as needed
    digitalWrite(LIGHT_PIN, HIGH); // Turn on the light
  } else {
    digitalWrite(LIGHT_PIN, LOW); // Turn off the light
  }
  delay(100);
}
```

### Arduino Code for Indoor Automation Using Ultrasonic Sensor
```cpp
#define TRIG_PIN 9
#define ECHO_PIN 10
#define FAN_LIGHT_PIN 8

void setup() {
  pinMode(TRIG_PIN, OUTPUT);
  pinMode(ECHO_PIN, INPUT);
  pinMode(FAN_LIGHT_PIN, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  long duration;
  int distance;

  digitalWrite(TRIG_PIN, LOW);
  delayMicroseconds(2);

  digitalWrite(TRIG_PIN, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIG_PIN, LOW);

  duration = pulseIn(ECHO_PIN, HIGH);
  distance = duration * 0.034 / 2; // Calculate distance in cm

  if (distance < 100) { // Adjust range as needed
    digitalWrite(FAN_LIGHT_PIN, HIGH); // Turn on fan and light
  } else {
    digitalWrite(FAN_LIGHT_PIN, LOW); // Turn off fan and light
  }
  delay(500);
}
```
![WhatsApp Image 2025-01-03 at 13 38 34_f3c6198c](https://github.com/user-attachments/assets/c3a37ae9-2eb4-49d2-9bb9-2b9ec89a4dc9)

