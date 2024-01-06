# Zephyr OS with STM32F4-Discovery Board

This repository documents my efforts to learn how to develop programs for an STM32 microcontroller using the Zephyr RTOS.

The STM32F4DISCOVERY is an evaluation board for STM32F407VGT6 MCU which includes everything required for beginners and experienced users to get started quickly. It includes an ST-LINK/V2-A embedded debug tool, two ST MEMS, digital accelerometer and digital microphone, one audio DAC with integrated class D speaker driver, LEDs and push buttons and an USB OTG micro-AB connector.

## Features

- STM32F407VGT6 microcontroller featuring 32-bit Arm® Cortex®-M4 with FPU core, 1-Mbyte Flash memory and 192-Kbyte RAM in an LQFP100 package
- USB OTG FS
- ST MEMS 3-axis accelerometer (LIS302DL)
- ST-MEMS audio sensor omni-directional digital microphone (MP45DT02)
- Audio DAC with integrated class D speaker driver (CS43L22)
- User and reset push-buttons
- Eight LEDs:
  - LD1 (red/green) for USB communication
  - LD2 (red) for 3.3 V power on 
  - Four user LEDs, LD3 (orange), LD4 (green), LD5 (red) and LD6 (blue)
  - Two USB OTG LEDs, LD7 (green) VBUS and LD8 (red) over-current
- Board connectors:
  - USB with Micro-AB
  - Stereo headphone output jack
  - 2.54 mm pitch extension header for all LQFP100 I/Os for quick connection to prototyping board and easy probing
- Flexible power-supply options: ST-LINK, USB VBUS, or external sources
- External application power supply: 3 V and 5 V
- Comprehensive free software including a variety of examples, part of STM32CubeF4 MCU Package, or STSW-STM32068 for using legacy standard libraries
- On-board ST-LINK/V2-A debugger/programmer with USB re-enumeration capability: mass storage, Virtual COM port, and debug port
- Support of a wide choice of Integrated Development Environments (IDEs) including IAR Embedded Workbench®, MDK-ARM, and STM32CubeIDE

![dm00039084-discovery-kit-with-stm32f407vg-mcu-stmicroelectronics2](https://github.com/m3y54m/stm32f4-discovery-zephyr/assets/1549028/ba54764c-32a9-4404-aa91-65588bfeb8db)

## Hardware

STM32F4DISCOVERY Discovery kit provides the following hardware components:

- STM32F407VGT6 in LQFP100 package
- ARM 32-bit Cortex-M4 CPU with FPU
- 168 MHz max CPU frequency
- VDD from 1.8 V to 3.6 V
- 1 MB Flash
- 192+4 KB SRAM including 64-Kbyte of core coupled memory
- GPIO with external interrupt capability
- 3x12-bit ADC with 24 channels
- 2x12-bit D/A converters
- RTC
- Advanced-control Timer
- General Purpose Timers (17)
- Watchdog Timers (2)
- USART/UART (6)
- I2C (3)
- SPI (3)
- SDIO
- 2xCAN
- USB 2.0 OTG FS with on-chip PHY
- USB 2.0 OTG HS/FS with dedicated DMA, on-chip full-speed PHY and ULPI
- 10/100 Ethernet MAC with dedicated DMA
- 8- to 14-bit parallel camera
- CRC calculation unit
- True random number generator
- DMA Controller

## Pinout

![image](https://github.com/m3y54m/stm32f4-discovery-zephyr/assets/1549028/db83825e-bc4f-4850-be38-ce8d5cd27a1c)

## Supported Features in Zephyr OS

The Zephyr `stm32f4_disco` board configuration supports the following hardware features:

| Interface | Controller | Driver/Component |
|-|-|-|
| NVIC | on-chip | nested vector interrupt controller |
| UART | on-chip | serial port-polling; serial port-interrupt |
| PINMUX | on-chip | pinmux |  
| GPIO | on-chip | gpio |
| PWM | on-chip | pwm |
| USB | on-chip | usb |
| CAN | on-chip | CAN controller |

The default configuration can be found in the defconfig file:

`boards/arm/stm32f4_disco/stm32f4_disco_defconfig`

Default Zephyr Peripheral Mapping:

- UART_1_TX : PB6
- UART_1_RX : PB7
- UART_2_TX : PA2
- UART_2_RX : PA3
- USER_PB : PA0
- LD3 : PD13
- LD4 : PD12
- LD5 : PD14
- LD6 : PD15
- USB DM : PA11
- USB DP : PA12
- CAN1_RX : PB8
- CAN1_TX : PB9
- CAN2_RX : PB5
- CAN2_TX : PB13

**STM32F4DISCOVERY Discovery kit has up to 6 UARTs. The Zephyr console output is assigned to UART2. Default settings are 115200 8N1.**

## Resources

- [Discovery kit with STM32F407VG MCU * New order code STM32F407G-DISC1 (replaces STM32F4DISCOVERY)](https://www.st.com/en/evaluation-tools/stm32f4discovery.html)
- [Discovery kit with STM32F407VG MCU - User manual](https://www.st.com/resource/en/user_manual/um1472-discovery-kit-with-stm32f407vg-mcu-stmicroelectronics.pdf)
- [STM32F4DISCOVERY - F407VGT6 - B02 Schematic](https://www.st.com/content/ccc/resource/technical/layouts_and_diagrams/schematic_pack/group1/0f/91/8b/39/b3/78/4d/c4/MB997-F407VGT6-B02_Schematic/files/MB997-F407VGT6-B02_Schematic.pdf/jcr:content/translations/en.MB997-F407VGT6-B02_Schematic.pdf)
- [ST STM32F4 Discovery - Zephyr Project Documentation](https://docs.zephyrproject.org/latest/boards/arm/stm32f4_disco/doc/index.html)
- [West (Zephyr’s meta-tool)](https://docs.zephyrproject.org/latest/develop/west/index.html)
- [Zephyr: Tutorial for Beginners](https://maksimdrachov.github.io/zephyr-rtos-tutorial/)
