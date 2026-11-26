# Roller Coaster Automation

An STM32F4 firmware prototype exploring the control and instrumentation around a roller-coaster braking system. The project combines an operator setup flow with peripheral configuration, ADC sampling, PWM output, I²C communication, and a small state machine.

> **Safety notice:** This repository is an educational prototype, not a validated braking controller or safety system. Do not connect it to or use it to control a real ride or other safety-critical equipment.

## Hardware and firmware

- Target configured in the project: STM32F407VGTx (STM32F4, LQFP100).
- Firmware uses the STM32 HAL and an STM32CubeIDE project configuration.
- USART6 serial interface is configured for 115200 baud.
- ADC1 channel 1 on PA1 is configured for 12-bit conversion and samples in interrupt-driven continuous mode.
- TIM9 channel 1 on PE5 is configured for PWM output.
- I²C1 is configured for 400 kHz, 7-bit addressing.
- Four status GPIO outputs use PD12–PD15.

At startup, the serial setup flow requests weight, speed, brake force, brake time, and pulse distance. The state table contains `INITIAL`, `MANUAL`, `AUTOMATIC`, and `SAFE` states. In the current implementation, the manual path averages ADC samples and updates the PWM output; the automatic path currently sequences status indicators rather than implementing a closed-loop braking controller. The entered parameters are not all used to calculate a physical stopping profile.

## Build and use

The repository contains an STM32CubeIDE configuration (`.ioc`), linker scripts, HAL-based source, and a debug launch configuration. Open the project with a compatible STM32CubeIDE toolchain and inspect its board, peripheral, and pin configuration before building or flashing. Hardware-specific setup and a connected debugger/programmer are required.

Do not treat the state names, serial input, PWM output, or SAFE state as evidence of a verified fail-safe design. The code and hardware have not been documented here as validated for real-world braking use.

## Related links

- [Portfolio project details](https://kasurancodes.github.io/stm.html)
- [Max McGill's portfolio](https://kasurancodes.github.io/)
