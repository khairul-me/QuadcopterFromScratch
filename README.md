# 🚁 DIY Quadcopter Build Guide: From Theory to Flight

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Issues](https://img.shields.io/github/issues/khairul-me/QuadcopterFromScratch)](https://github.com/khairul-me/QuadcopterFromScratch/issues)
[![GitHub Stars](https://img.shields.io/github/stars/khairul-me/QuadcopterFromScratch)](https://github.com/khairul-me/QuadcopterFromScratch/stargazers)

A comprehensive guide to building a professional-grade quadcopter drone, with detailed explanations of physics, engineering principles, and step-by-step instructions.

## 📚 Table of Contents

1. [Understanding Drones](#understanding-drones)
2. [Drone Components](#drone-components)
3. [Build Process](#build-process)
4. [Configuration Guide](#configuration-guide)
5. [Pre-Flight Checklist](#pre-flight-checklist)
6. [Flight Guide](#flight-guide)
7. [Troubleshooting Guide](#troubleshooting-guide)
8. [Support & Community](#support--community)
9. [Contributing](#contributing)
10. [License](#license)

## Technical Specifications

| Specification | Value |
|--------------|-------|
| Frame Size | 450mm |
| Flight Time | 15-20 minutes |
| Max Speed | 60 km/h |
| Control Range | 1-2 km |
| Maximum Payload | 500g |
| Total Weight | ~1200g |

## Understanding Drones

### Basic Quadcopter Layout
```
    Motor 1    Motor 2
       \         /
        \       /
         [===]
        /       \
       /         \
    Motor 3    Motor 4
```

### Flight Principles

1. **Thrust Generation**
```
T = CT × ρ × n² × D⁴

Where:
T = Thrust (N)
CT = Thrust coefficient
ρ = Air density (kg/m³)
n = Propeller rotational speed (rev/s)
D = Propeller diameter (m)
```

2. **Power Requirements**
```
P = CP × ρ × n³ × D⁵

Where:
P = Power (W)
CP = Power coefficient
```

3. **Flight Dynamics**
- Throttle: Vertical movement
- Roll: Left/right tilt
- Pitch: Forward/backward tilt
- Yaw: Rotation

## Drone Components

### Essential Parts List

#### Frame & Structure
- Carbon fiber frame (450mm)
- 4× arms
- Landing gear
- Vibration dampeners
- Mounting hardware

#### Propulsion System
```
Motors (4×):
- Type: Brushless DC
- KV Rating: 920KV
- Size: 2212-2312

ESCs (4×):
- Current: 30A
- Protocol: DShot600
- Firmware: BLHeli_32

Propellers:
- Size: 10×4.5
- Type: 2× CW, 2× CCW
- Material: Carbon fiber
```

#### Electronics
```
Flight Controller:
- Processor: F7
- IMU: MPU6000
- Built-in OSD

Power System:
- PDB (Power Distribution Board)
- 4S LiPo battery (3000mAh, 50C)
- Battery monitor
- XT60 connectors

Communication:
- RC Receiver
- GPS Module
- Telemetry (optional)
```

### Required Tools

#### Essential
- Soldering iron (40W minimum)
- Hex driver set (M2-M5)
- LiPo battery charger
- Multimeter
- Wire strippers/cutters
- Heat shrink tubing
- Helping hands for soldering

#### Optional
- Oscilloscope
- Battery voltage tester
- Prop balancer
- Heat gun

## Build Process

### 1. Preparation
```
Workspace Setup:
□ Clean work area
□ Organize components
□ Verify all parts present
□ Read manuals
□ Gather tools
```

### 2. Frame Assembly
```
Step-by-Step:
1. Mount center plate
2. Attach arms
   - Check orientation
   - Secure all screws
3. Install landing gear
4. Mount PDB
5. Quality check
```

### 3. Electronics Installation
```
Wiring Sequence:
1. Solder XT60 to PDB
2. Mount ESCs on arms
3. Connect motor wires
4. Install flight controller
5. Connect receiver
6. Mount GPS module
```

### 4. Configuration

#### Flight Controller Settings
```yaml
# Basic PID Configuration
pid_roll:
  P: 42
  I: 40
  D: 20

pid_pitch:
  P: 42
  I: 40
  D: 20

pid_yaw:
  P: 85
  I: 45
  D: 0
```

#### Radio Setup
```
Channel Mapping:
1. Throttle
2. Aileron (Roll)
3. Elevator (Pitch)
4. Rudder (Yaw)
5. Flight Mode
6. Arm Switch
```

## Pre-Flight Calculations

### Thrust-to-Weight Ratio (TWR)
```python
def calculate_twr(motor_thrust, components_weight, battery_weight):
    total_thrust = motor_thrust * 4  # Four motors
    total_weight = components_weight + battery_weight
    return total_thrust / total_weight

# Example
motor_thrust = 800  # grams
components_weight = 800  # grams
battery_weight = 400  # grams

twr = calculate_twr(motor_thrust, components_weight, battery_weight)
# Target TWR > 2.0 for good performance
```

### Flight Time Estimation
```python
def calculate_flight_time(battery_capacity, avg_current_draw):
    """
    battery_capacity in mAh
    avg_current_draw in A
    returns flight time in minutes
    """
    return (battery_capacity / 1000 * 0.8) / avg_current_draw * 60

# Example
battery_capacity = 3000  # mAh
avg_current_draw = 20  # A
flight_time = calculate_flight_time(battery_capacity, avg_current_draw)
```

## Pre-Flight Checklist

### Physical Inspection
```
□ Frame integrity
□ Propeller condition
□ Battery secure
□ All screws tight
□ No loose wires
```

### Electronics Check
```
□ Battery voltage
□ Motor response
□ Radio link
□ GPS lock
□ Failsafe test
```

### Environment Assessment
```
□ Weather conditions
□ Flying area clear
□ Legal requirements met
□ Spotter available
```

## Troubleshooting Guide

### Common Issues

| Problem | Cause | Solution |
|---------|-------|----------|
| Won't arm | FC not level | Calibrate accelerometer |
| Unstable flight | Bad PID tune | Adjust PID values |
| Motor not spinning | ESC issue | Check connections |
| Poor GPS hold | Interference | Relocate GPS module |
| Short flight time | High current draw | Check power system |

### Motor Direction Check
```
Front Left: CCW
Front Right: CW
Back Left: CW
Back Right: CCW
```

## Flight Guide

### First Flight Steps
1. Choose open area
2. Start in stabilized mode
3. Take off slowly
4. Hover test
5. Basic movements
6. Landing practice

### Advanced Maneuvers
- Figure 8 patterns
- Precision hovering
- Emergency procedures
- Return to home testing

## Safety Guidelines

### General Safety
1. Never fly over people
2. Maintain visual line of sight
3. Check local regulations
4. Monitor battery voltage
5. Have emergency procedures ready

### Battery Safety
- Never over-discharge
- Store at 3.8V per cell
- Check for swelling
- Use LiPo safe bag
- Proper charging procedures

## Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## Support & Community

- [Discord Server](https://discord.gg/dronecommunity)
- [Wiki](https://github.com/khairul-me/QuadcopterFromScratch/wiki)
- [Issue Tracker](https://github.com/khairul-me/QuadcopterFromScratch/issues)
- [Updates](https://github.com/khairul-me/QuadcopterFromScratch/releases)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Created with ❤️ by [Khairul Islam](https://github.com/khairul-me)**

[Back to Top](#-diy-quadcopter-build-guide-from-theory-to-flight)

</div>
