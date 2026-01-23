# Obstacle Avoiding Robot 

An autonomous Arduino-based robot car that uses ultrasonic sensors and a servo-mounted scanner to detect and navigate around obstacles in real-time.

## Features

- **Autonomous Navigation**: Moves forward and automatically detects obstacles
- **Smart Scanning**: Servo-mounted ultrasonic sensor scans left and right to find the best path
- **Obstacle Avoidance**: Makes intelligent decisions to turn or reverse when blocked
- **Audio Feedback**: Buzzer alerts when obstacles are detected
- **Sensor Validation**: Multi-reading validation system to filter out false sensor data

## Hardware Requirements

### Components

- Arduino board (Uno/Nano recommended)
- L298N Motor Driver Module
- 4x DC Motors with wheels
- HC-SR04 Ultrasonic Sensor
- SG90 Servo Motor
- Active Buzzer
- Chassis and wheels
- Battery pack (7-12V recommended)
- Jumper wires

### Pin Configuration

| Component | Arduino Pin |
|-----------|-------------|
| Motor Driver ENA | 5 (PWM) |
| Motor Driver IN1 | 6 |
| Motor Driver IN2 | 7 |
| Motor Driver IN3 | 8 |
| Motor Driver IN4 | 9 |
| Motor Driver ENB | 3 (PWM) |
| Ultrasonic TRIG | 2 |
| Ultrasonic ECHO | 4 |
| Servo Signal | 11 (PWM) |
| Buzzer | A2 |

## Wiring Diagram

```
Arduino          L298N Motor Driver
  5   ---------> ENA (Enable A - PWM)
  6   ---------> IN1 (Motor A Direction)
  7   ---------> IN2 (Motor A Direction)
  8   ---------> IN3 (Motor B Direction)
  9   ---------> IN4 (Motor B Direction)
  3   ---------> ENB (Enable B - PWM)

Arduino          HC-SR04 Sensor
  2   ---------> TRIG
  4   ---------> ECHO
 5V   ---------> VCC
 GND  ---------> GND

Arduino          Servo Motor
  11  ---------> Signal (Orange/Yellow)
 5V   ---------> VCC (Red)
 GND  ---------> GND (Brown/Black)

Arduino          Buzzer
  A2  ---------> Positive (+)
 GND  ---------> Negative (-)
```

## Installation

1. **Install Arduino IDE**: Download from [arduino.cc](https://www.arduino.cc/en/software)

2. **Install Required Library**:
   - Open Arduino IDE
   - Go to `Sketch` → `Include Library` → `Manage Libraries`
   - Search for "Servo" and install the official Servo library

3. **Upload Code**:
   - Connect your Arduino to your computer via USB
   - Open the `.ino` file in Arduino IDE
   - Select your board: `Tools` → `Board` → `Arduino Uno` (or your board)
   - Select the port: `Tools` → `Port` → (select your Arduino port)
   - Click the Upload button (→)

## How It Works

1. **Forward Movement**: The robot moves forward at maximum speed when the path is clear
2. **Obstacle Detection**: When an obstacle is detected within 30cm, the robot stops
3. **Scanning**: The servo rotates the sensor to scan left (160°) and right (20°)
4. **Decision Making**:
   - If the left path is clearer and safe (>40cm), turn left
   - If the right path is clearer and safe (>40cm), turn right
   - If both paths are blocked, reverse and turn right
5. **Validation**: Multiple sensor readings are averaged to prevent false detections

## Configuration

You can adjust these parameters in the code to customize behavior:

```cpp
#define SAFE_DISTANCE 40   // Minimum clearance needed to turn (cm)
#define STOP_DISTANCE 30   // Distance to trigger obstacle detection (cm)
#define MAX_SPEED 100      // Forward/turning speed (0-255)
#define REVERSE_SPEED 80   // Reverse speed (0-255)
```

## Serial Monitor Output

Open the Serial Monitor (115200 baud) to see real-time debugging information:

```
--- OBSTACLE AVOIDING ROBOT ---
System Ready!
Distance: 85 cm
Distance: 72 cm
⚠️ Obstacle detected! Scanning...
Left: 65 cm
Right: 25 cm
→ Turning LEFT
```

## Troubleshooting

### Robot doesn't move
- Check motor driver connections and power supply
- Verify battery voltage is sufficient (7-12V)
- Test motors directly with the motor driver

### Erratic sensor readings
- Ensure sensor is mounted firmly
- Check for loose connections on TRIG and ECHO pins
- Avoid metallic or sound-absorbing obstacles during testing

### Robot gets stuck in loops
- Adjust `SAFE_DISTANCE` and `STOP_DISTANCE` values
- Increase turn delays for sharper turns
- Check that servo is centered properly at 90°

### Servo jitters
- Use external power supply for servo if needed
- Add a small capacitor (100µF) across servo power lines

## Future Enhancements

- [ ] Add line-following capability
- [ ] Implement PID control for smoother movement
- [ ] Add Bluetooth control via smartphone app
- [ ] Include speed sensors for odometry
- [ ] Multi-sensor array for better obstacle detection

## License

This project is open-source and available under the MIT License.

## Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new features
- Submit pull requests

## Acknowledgments


**For the robotics club, Nithin Sankar K**
