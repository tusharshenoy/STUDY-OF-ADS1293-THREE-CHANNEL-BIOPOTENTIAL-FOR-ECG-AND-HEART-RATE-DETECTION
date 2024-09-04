# Study-Of-ADS1293-Three-Channel-Biopotential-For-ECG

## Project Overview

This project demonstrates a robust system for remote ECG signal monitoring, leveraging the capabilities of IoT and modern biopotential analog front-end (AFE) technology. The system captures ECG data through a 3-lead setup using the ADS1293 module, processes the data via NI myRIO, and transmits it wirelessly to the ThingSpeak platform for real-time monitoring and analysis.

## Abstract

The electrocardiogram (ECG) is a vital tool for assessing heart function, providing insights into rhythm, rate, and electrical impulses. In this project, the ADS1293, a three-channel biopotential AFE, is employed to acquire ECG signals. These signals are then processed using NI myRIO via SPI communication. The processed data is transmitted wirelessly using an ESP WiFi module to the ThingSpeak platform for remote monitoring. This system enhances the ability of healthcare providers to monitor ECG data remotely, improving patient care and diagnostic capabilities.

## System Block Diagram

The following block diagram illustrates the system architecture:

```
[ECG Leads] -> [ADS1293 Module] -> [NI myRIO] -> [LabVIEW for Visualization] -> [ESP WiFi Module] -> [ThingSpeak Platform]
```

## Components

### Hardware
- **ADS1293 AFE**: A high-resolution, low-power biopotential analog front-end designed for ECG applications.
- **NI myRIO-1900**: An embedded evaluation board by National Instruments, used for real-time applications and educational purposes.
- **ESP WiFi Module**: Facilitates wireless data transmission to the ThingSpeak IoT platform.

### Software
- **LabVIEW**: A graphical programming language used for system development, data acquisition, and real-time visualization.
- **ThingSpeak**: An IoT platform for data analysis, storage, and visualization.

## Methodology

### SPI Communication
The ADS1293 module communicates with the NI myRIO using SPI protocol, which accesses control registers and manages data acquisition. The ECG data is acquired in real-time and processed for remote monitoring via ThingSpeak.

### Data Transmission
The processed ECG data is transmitted to the ThingSpeak IoT platform using the ESP WiFi module, enabling continuous and accessible remote monitoring.

### LabVIEW Integration
LabVIEW is used for configuring the ADS1293 registers, acquiring ECG data, and providing a graphical interface for real-time signal visualization.

## System Implementation

### Initial Configuration
The system is initialized by setting up the ADS1293’s registers using LabVIEW. The SPI protocol is employed to establish communication between the ADS1293 and NI myRIO.

### Continuous Data Acquisition
The ECG data is continuously read from the ADS1293 module and visualized in real-time using LabVIEW. This data is also transmitted to ThingSpeak for remote monitoring.

### Auto-Incrementing Address Mode
The ADS1293’s auto-incrementing address mode is used for efficient data block access during continuous data acquisition.

## Pin Configuration

The table below shows the pin configuration between the ADS1293 and NI myRIO:

| ADS1293 Pin | Function     | NI myRIO Pin     |
|-------------|--------------|------------------|
| MOSI        | Slave In     | DIO7 / SPI.MOSI  |
| MISO        | Slave Out    | DIO6 / SPI.MISO  |
| SCK         | Serial Clock | DIO5 / SPI.CLK   |
| CS          | Chip Select  | DIO4             |
| VCC         | Digital VDD  | +3.3V            |
| GND         | Digital GND  | DGND             |

## Register Map

Below is a sample register map of the ADS1293 used in this project:

| Register Name  | Description                          | Access | Address | Default Value |
|----------------|--------------------------------------|--------|---------|---------------|
| FLEX_CH1_CN    | Flexible Routing Switch Control (Ch1)| R/W    | 0x01    | 0x00          |
| FLEX_CH2_CN    | Flexible Routing Switch Control (Ch2)| R/W    | 0x02    | 0x00          |
| CMDET_EN       | Common-Mode Detect Enable            | R/W    | 0x0A    | 0x00          |
| RLD_CN         | Right-Leg Drive Control              | R/W    | 0x0C    | 0x00          |
| OSC_CN         | Output Clock Control and Clock Source| R/W    | 0x12    | 0x00          |
| AFE_SHDN_CN    | Analog Front End Shutdown Control    | R/W    | 0x14    | 0x00          |

## Conclusion

This project successfully implements a remote ECG monitoring system using ADS1293 and NI myRIO, with data transmission facilitated by an ESP WiFi module to the ThingSpeak platform. The integration of IoT for real-time monitoring enhances the accessibility and effectiveness of ECG data analysis in healthcare.