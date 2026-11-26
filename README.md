# Roller Coaster Automation

This project uses an STM microcontroller to monitor and control a roller coaster braking system, with a focus on predictable operation and safety.

## Configuration and control

At startup, an operator enters the system's physical parameters through a serial terminal:

- Weight
- Speed
- Brake force
- Brake time
- Pulse distance

The system stores these values for use while managing the braking behaviour.

## Operating modes

A state machine organizes operation into four defined modes:

- Initial setup
- Manual control
- Automatic operation
- Safe mode



