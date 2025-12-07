# Chapter 4: Building a Simple Humanoid Prototype

## Hardware Selection
Building a full-scale humanoid is a massive undertaking, but creating a small-scale prototype is an achievable and highly educational project. Here's a breakdown of the key hardware components you'll need:

- **Servos:** For a small prototype, servo motors are the best choice for joints. They are affordable, easy to control, and come in a wide range of sizes and torques. Hobby servos (like the MG996R or DS3218) are a good starting point. For higher performance, you can look at more advanced "robot" servos.

- **Frames:** The frame is the skeleton of your robot. You can build a frame from a variety of materials, including aluminum brackets, carbon fiber tubes, or 3D-printed parts. Many online communities share open-source designs for robot frames.

- **Microcontrollers:** The microcontroller is the brain of your robot. It reads sensor data and sends control signals to the servos.
  - **ESP32/Arduino:** These are excellent choices for a first prototype. The Arduino is very beginner-friendly, while the ESP32 offers more processing power, built-in Wi-Fi, and Bluetooth, which are useful for more advanced projects.

## ESP32/Arduino Basics
- **Arduino:** The Arduino platform is famous for its simplicity. The Arduino IDE uses a simplified version of C++, and there are thousands of libraries and tutorials available. An Arduino Mega has enough I/O pins to control a large number of servos.

- **ESP32:** The ESP32 is a powerful dual-core microcontroller that can be programmed using the Arduino IDE or MicroPython. Its wireless capabilities allow you to control your robot remotely or connect it to the internet to fetch data or receive commands.

## 3D Printing Overview
3D printing is a game-changer for hobby robotics. It allows you to design and create custom parts, such as brackets, sensor mounts, and even entire limbs, with a relatively low-cost desktop 3D printer.

- **FDM (Fused Deposition Modeling):** This is the most common type of 3D printing, where a plastic filament (like PLA or PETG) is melted and extruded layer by layer to build an object.
- **CAD Software:** To design your own parts, you will need to learn some basic CAD (Computer-Aided Design). Free tools like Tinkercad (very easy) and Fusion 360 (more advanced) are great places to start.

## Servo Control Example (Pseudocode)
Controlling a servo is straightforward. Servos are controlled by a PWM (Pulse Width Modulation) signal. You don't need to generate this signal yourself, as most microcontroller libraries handle it for you.

Here is a simple pseudocode example of how to control a servo using an Arduino-like library:

```cpp
// Include the servo library
#include <Servo.h>

// Create a servo object
Servo myServo;

void setup() {
  // Attach the servo to a pin (e.g., pin 9)
  myServo.attach(9);
}

void loop() {
  // Move the servo to 0 degrees
  myServo.write(0);
  delay(1000); // Wait for 1 second

  // Move the servo to 90 degrees
  myServo.write(90);
  delay(1000); // Wait for 1 second

  // Move the servo to 180 degrees
  myServo.write(180);
  delay(1000); // Wait for 1 second
}
```

## AI Integration Roadmap
Once you have a working hardware prototype that you can control, you can start integrating AI.

1.  **Start with Simple Sensors:** Add simple sensors like an ultrasonic distance sensor or an IMU to your microcontroller. Write code that uses this sensor data to make basic decisions (e.g., stop if an obstacle is detected).

2.  **Offload AI to a PC:** Your microcontroller is not powerful enough to run complex AI models. A common approach is to have the robot stream sensor data (like a camera feed) to a more powerful computer (like a laptop or a Raspberry Pi).

3.  **Use ROS2:** Install ROS2 on both your PC and your robot's microcontroller (using a package like `micro-ros`). This will allow you to send sensor data and commands seamlessly between the two.

4.  **Run AI Models on the PC:** On the PC, you can run AI models for object detection or SLAM. The output of these models can be used to generate high-level commands (e.g., "move forward," "turn left").

5.  **Send Commands to the Robot:** The PC sends these commands back to the microcontroller, which then translates them into low-level servo movements.

This "hybrid" architecture, where a powerful computer handles the "brains" and a simple microcontroller handles the "muscle," is a powerful and scalable way to build increasingly intelligent robots.
