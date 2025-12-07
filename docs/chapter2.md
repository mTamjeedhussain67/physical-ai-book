# Chapter 2: Humanoid Robotics Fundamentals

## Anatomy of Humanoids
A humanoid robot's anatomy is a complex integration of hardware designed to mimic the human form and function. The key components include:

- **Sensors:** These are the robot's senses, providing the data needed to perceive the world and its own state. Common sensors include:
  - **Cameras:** Provide visual input for navigation and object recognition.
  - **LiDAR (Light Detection and Ranging):** Creates 3D maps of the environment.
  - **IMUs (Inertial Measurement Units):** Measure orientation, velocity, and gravitational forces to maintain balance.
  - **Force/Torque Sensors:** Placed in joints and end-effectors to measure forces and provide feedback for manipulation.
  - **Tactile Sensors:** Give the robot a sense of touch.

- **Actuators:** These are the "muscles" of the robot, responsible for creating motion. Most humanoid robots use electric motors, though some research platforms explore hydraulic or pneumatic systems for greater power.

- **Motors:** The most common type of actuator is the electric motor, often paired with a gearbox to increase torque. Brushless DC motors and servo motors are widely used in robotics for their precision and reliability.

## Balance & Bipedal Locomotion
Bipedal locomotion—walking on two legs—is one of the greatest challenges in humanoid robotics. Unlike wheeled robots, humanoids are dynamically unstable, meaning they must constantly adjust to stay upright.

Key concepts in bipedal locomotion include:

- **Center of Mass (CoM):** The robot's control system must constantly manage its CoM to keep it within the "support polygon"—the area defined by its feet on the ground.
- **Zero Moment Point (ZMP):** A key metric used in balance control. The ZMP is the point on the ground where the net moment of inertial and gravitational forces is zero. To remain stable, the robot must keep the ZMP within the support polygon.
- **Gait Generation:** This involves creating the sequence of leg movements for walking, running, or climbing stairs. Gaits can be pre-programmed or generated in real-time based on sensor feedback.

## ROS2 Fundamentals
The Robot Operating System (ROS) is a flexible framework for writing robot software. ROS2 is the second generation of ROS, offering improved performance, security, and support for multi-robot systems.

Key ROS2 concepts include:

- **Nodes:** A node is a process that performs a computation (e.g., controlling a motor, processing sensor data). A ROS2 system is comprised of many nodes.
- **Topics:** Nodes communicate by publishing and subscribing to "topics." A topic is a named bus over which messages are sent. For example, a camera node might publish images to a `/camera/image` topic.
- **Services:** For request/response communication, nodes can use "services." One node offers a service, and another node can call it and receive a response.
- **Actions:** Actions are used for long-running tasks, like navigating to a goal. They provide feedback during execution and can be preempted.

## Power, Battery, and Joint Structure
- **Power Systems:** Humanoid robots are power-hungry. Their power system must be able to deliver high currents to the motors while also providing stable, clean power to the onboard computers and sensors.

- **Battery:** Most modern humanoids are untethered and rely on high-capacity lithium-ion battery packs. Battery management is critical, as it involves monitoring the state of charge, temperature, and current draw to ensure safe and efficient operation.

- **Joint Structure:** Humanoid joints are designed to provide a specific range of motion, or "degrees of freedom" (DOF). A typical humanoid has over 20 DOF, with multiple joints in the legs, arms, and torso. The design of these joints involves a trade-off between range of motion, torque, speed, and cost. High-performance gearboxes, such as harmonic or cycloidal drives, are often used to achieve high torque in a compact form factor.
