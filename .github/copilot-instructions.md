# STM32F030R8 Firmware Rules

Target MCU:
STM32F030R8 (Cortex-M0)

Constraints:
- 8 KB RAM / 64 KB Flash
- No malloc/free allowed
- No recursion
- Keep ISR code minimal
- Prefer static/global buffers only where needed

Architecture:
- Bare-metal superloop
- State machine-based design
- Interrupt-driven peripherals (no polling loops where possible)

Coding rules:
- C99 standard
- Use fixed-width types (uint8_t, uint16_t, uint32_t)
- Always check HAL return values
- Mark ISR-shared variables as volatile
- Avoid floating point unless absolutely necessary

Peripherals:
- USART (interrupt or DMA preferred)
- SPI
- I2C
- ADC
- TIM
- DMA

Performance rules:
- Minimize stack usage
- Avoid large local arrays in functions
- Avoid unnecessary memcpy
- Prefer ring buffers for UART