# FPGA-Projects
These are some of my FPGA Projects  done with target board ZYNQ 7000 SoC

Project 1- SPI Project in FPGA- Ambient Light Sensor

A demonstration of SPI Master inside FPGA talking to ADC which is an external peripheral.

SPI- Serial Peripheral Interface

-> Used by lot a devices like Memory, Microcontrollers, I/O Devices, LCDs, Converters, ADCs, UARTs ( common for ICs)

![Screenshot 2025-05-25 154010](https://github.com/user-attachments/assets/48bb4e5b-787e-4ca7-bfe3-35e23e5639f2)

->The SPI Slave is an IC, and The SPI Master is usually a microcontroller or an FPGA (this case).
-> SPI master initiates the data transfer.
-> SCLK - Serial clock ( synchronous communication , ie faster like 16Mb/s, 32 Mb/s....) ,unlike UART (Asynchronous, slower that SPI 1Mb/s).
-> MOSI - Master Out Slave In (DATA LINE). (Write)
-> MISO - Master In Slave Out (DATA LINE). (Read)
-> SS' - Chip Select (bar/compliment indicates active low) ( data transfer happens).(I2C doesnot have this , it uses address).

Advantages

-> Multiple slaves possible.
-> FUll Duplex.
-> Higher speed than UART + I2C.
-> Ubiquitous (everywhere)

Disadvantages

-> More Pins than UART + I2C
-> Short distance is good , not for long distances (RS-485/ RS-232).
-> Lot of variants.

Modes of SPI

-> Four Modes at High Level ( 0,1,2,3).
-> each mode has a CPOL, CPHA.
-> CPOL - clock polarity
-> CPHA - clock phase
-> There are two CPOL and CPHA states 0 , 1.
-> Data smapling should be done by the receiver not at the beginning or the end of data exchange as it may result in 0 or 1. sampling should be done in the middle.

Demonstration ( without chipselect) 
