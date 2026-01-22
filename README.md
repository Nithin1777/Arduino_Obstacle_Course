Obstacle Avoiding Robot (Arduino)

A self-navigating robotic car built with an Arduino, an L298N Motor Driver, and an HC-SR04 Ultrasonic Sensor mounted on a servo motor. The robot autonomously detects obstacles, scans its surroundings, and chooses the clearest path to continue moving.
🚀 Features

    Intelligent Scanning: When an obstacle is detected within 30cm, the robot stops and rotates the sensor left and right to compare distances.

    Glitched Reading Protection: Includes logic to filter out ultrasonic noise and "stuck" sensor readings.

    Automatic Backtracking: If both sides are blocked, the robot reverses and performs a wide turn to escape corners.

    Speed Control: Uses PWM (Pulse Width Modulation) to manage motor speeds for smoother movements.

🛠️ Hardware Requirements

    Microcontroller: Arduino Uno (or compatible)

    Motor Driver: L298N Dual H-Bridge

    Motors: 2x DC Gear Motors

    Sensor: HC-SR04 Ultrasonic Sensor

    Actuator: SG90 Micro Servo

    Power: 7.4V - 12V Li-ion battery pack or AA battery holder

    Misc: Piezo Buzzer, Jumper Wires, Robot Chassis
### 🔌 Pin Mapping Table

| Component | Function | Arduino Pin | Driver Pin |
| :--- | :--- | :---: | :---: |
| **Left Motor** | Speed (PWM) | 5 | ENA |
| **Left Motor** | Direction | 6 | IN1 |
| **Left Motor** | Direction | 7 | IN2 |
| **Right Motor** | Direction | 8 | IN3 |
| **Right Motor** | Direction | 9 | IN4 |
| **Right Motor** | Speed (PWM) | 3 | ENB |
| **Ultrasonic** | Trigger | 2 | TRIG |
| **Ultrasonic** | Echo | 4 | ECHO |
| **Servo** | Rotation | 11 | Signal |
| **Buzzer** | Alert | A2 | (+) |


    Forward Drive: The robot moves forward while constantly checking the distance in front.

    Detection: If an object is detected within STOP_DISTANCE (30cm), the stopCar() function is called.

    Scanning: The executeScan() function triggers the servo to move to 160° (Left) and 20° (Right).

    Decision: * If Left distance > Right distance and above 40cm: Turn Left.

        If Right distance > Left distance and above 40cm: Turn Right.

        If Both are blocked: Reverse, then turn 180 degrees.

💻 Installation

    Ensure you have the Servo library installed in your Arduino IDE (pre-installed by default).

    Connect your hardware according to the Pin Mapping table.

    Open Obstacle_Avoiding_Robot.ino in the Arduino IDE.

    Select your Board and Port.

    Click Upload.
