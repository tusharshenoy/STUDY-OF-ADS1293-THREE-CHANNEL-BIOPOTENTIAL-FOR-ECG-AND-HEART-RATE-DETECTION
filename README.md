# Study-Of-ADS1293-Three-Channel-Biopotential-For-ECG-and-Heart-Rate-Detection

## Abstract 
The electrocardiogram is an important diagnostic tool that evaluates the heart's electrical activity, providing insights into rhythm, rate and impulses. The ECG data acquisition module employs the ADS1293, a highly advanced, three-channel biopotential analog front-end (AFE), to acquire these signals. This IC is designed to support 3, 5, and 12 lead ECG systems which allows flexibility in monitoring varying degrees of cardiac function. For this demonstration, ADS1293 module is used to obtain 3-lead ECG data. The acquired ECG data is interfaced with NI myRIO using a SPI communication protocol to access internal data registers. The setup allows the storage of sampled ECG data for real-time visualization in the LabVIEW software. The recorded signals are analysed through LabVIEW which provides a functional method for evaluating various heart conditions.
        Keywords—Electrocardiogram, ADS1293, NI myRIO, LabVIEW.
	
## I. INTRODUCTION 
The electrocardiogram (ECG) is a simple, safe method for graphically recording the heart's electrical activity using electrodes placed on the body. This recording captures the changes that occur during the contraction (systole) and relaxation (diastole) phases of the atria and ventricles. The significance of continuous and remote ECG monitoring has grown considerably, particularly for individuals with chronic heart conditions, the elderly, and those at risk of sudden cardiac attack. Traditional in-clinic ECG tests provide only brief glimpses of heart activity, often missing transient but clinically important arrhythmias. Remote ECG monitoring overcomes this limitation by allowing continuous heart activity tracking over long periods, offering a more detailed and comprehensive view of a patient's cardiac health and leading to better diagnosis and management.
Remote health monitoring systems have emerged as important tools in modern healthcare, offering continuous and accessible monitoring of vital signs. These systems are particularly valuable for individuals with chronic conditions, elderly people and those who are at risk of sudden cardiac attacks, enabling driven management and timely intervention. A WLAN-based remote health monitoring system represents this capability by efficiently collecting multiple vital signs in real-time using the MQTT protocol, underscoring the importance of seamless and secure data transmission in remote healthcare applications [1].The evolution towards portable ECG monitoring solutions has addressed the need for cost-effective and user-friendly devices for home-based healthcare. An IoT-based portable ECG monitoring system exemplifies this trend, using IoT cloud infrastructure to enable effective monitoring and visualisation of ECG data, especially beneficial for elderly care at home [2]. Furthermore, advancements in signal processing and networking have significantly enhanced the accuracy and reliability of remote ECG monitoring systems. An IoT-based e-health monitoring system using ECG signals integrates wireless communication and hidden Markov models to address challenges in data acquisition, transmission and visualisation, thereby improving diagnostic capabilities remotely [3].
In parallel, the integration of cloud computing and BLE 4.0 technologies has facilitated the development of IoT-enabled cloud-based ECG monitoring systems. These systems employ sophisticated filtering algorithms to ensure real-time monitoring of heartbeat, PQRST wave, QRS complex intervals, and respiration rate remotely, demonstrating robustness in continuous healthcare monitoring [4]. Wearable monitoring nodes have further extended the reach of ECG monitoring into smart healthcare environments, transmitting data seamlessly to IoT clouds for comprehensive analysis and management [5]. Moreover, low-cost prototypes Utilising sensors like AD8232 and microcontrollers such as Nodemcu ESP 8266 have enabled remote ECG monitoring with data visualization on platforms like ThingSpeak, enhancing accessibility to healthcare professionals for timely intervention [6]. Innovations like IoT-based heartbeat monitoring systems with cloud storage and automated alerts underscore the potential of integrating sensor technologies with cloud-based analytics to improve patient outcomes [7]. In rural areas there is a need in Remote IoT-based ECG monitoring systems focus on reducing healthcare costs and aiding heart patients through data analysis and prediction, highlighting the transformative impact of technology in healthcare accessibility [8]. Another IoT-based patient monitoring system provides real-time ECG and temperature monitoring with automated notifications for critical conditions, ensuring continuous patient care [9]. Moreover, IoT-assisted frameworks ensure secure data transmission, focusing on patient data integrity and confidentiality in remote monitoring scenarios [10]. IoT applications like Blynk provide real-time, low-cost, and remotely accessible ECG monitoring solutions for heart patients, emphasizing affordability and accessibility in healthcare [11].
Building on these advancements, this project presents a system utilizing the ADS1293 for acquiring ECG data from a participant connected via three leads (LL - left leg, LA - left arm, RA - right arm and RL - right leg). These leads are interfaced with the ADS1293 ECG breakout board through a 3.5mm headphone jack. This integrated setup enables remote monitoring and detailed analysis of ECG data, significantly enhancing accessibility and usability in healthcare applications.

## II. SYSTEM DESCRIPTION

### 2.1	System Block Diagram
![Copy of MINIPROJECT (2)](https://github.com/user-attachments/assets/f4ae0db8-4b23-41fc-b259-e76db2fe0af1)

#### Figure 1 Block Diagram of the Setup
                                                           
The system utilizes ADS1293 for acquiring ECG data from a participant connected via three leads (LL - left leg, LA - left arm, RA - right arm and RL - right leg). These leads are interfaced with the ADS1293 ECG breakout board through a 3.5mm headphone jack. The NI myRIO makes the Data Acquisition possible and employs SPI communication protocol. This integrated setup enables remote monitoring and detailed analysis of the ECG data which improves the convenience and usability in healthcare applications.

### 2.2 System Components
#### ADS1293 Analog Front End (AFE)
The Texas Instruments ADS1293 is an analog front end which integrates three high-resolution channels capable of operating at up to 25.6ksps, each independently programmable for specific sample rates and bandwidths to optimize performance and power consumption. Key features include built-in EMI filters on input pins, flexible routing for lead-off detection, right leg drive, and reference terminal generation. An additional channel supports external analog pace detection which is complemented by a self-diagnostics alarm system to ensure operational reliability.
#### NI myRIO-1900
The NI myRIO-1900 is an embedded evaluation board which is developed by National Instruments, designed for real-time applications and educational purposes. It features reconfigurable I/O capabilities, incorporating an onboard FPGA and microprocessor. Primarily used in teaching and implementing concepts like controls, mechatronics, and capstone projects, it requires LabVIEW for development and is popular among students and for basic applications.

### 2.3 Software Used
#### LabVIEW
LabVIEW which when elaborated stands for Laboratory Virtual Instrument Engineering Workbench is a graphical programming language used largely in scientific, engineering and educational contexts. The Software uses a visual block diagram rather than traditional text-based coding, it helps in rapid system development and testing. Common applications include data acquisition, instrument control and industrial automation. It enables users to develop complex systems, gain insights from data and interface with industry protocols seamlessly.

## III. METHODOLOGY                                                       
### 3.1	Programming

The ADS1293 SPI facilitates access to its registers which controls the configuration, using a 4-wired synchronous interface. The interface is compatible with SPI interfaces commonly found on various DSP controllers and microcontrollers. The flexibility and compatibility of the SPI interface ensure seamless integration and communication within diverse system architectures.

Moreover, the ADS1293 provides the capability to adjust the digital output drive strength through the DIGO_STRENGTH register. This feature allows to program the strength of the transistors driving the serial data out pin at four different levels. The appropriate drive strength depends on the capacitive load on the SDO pin, with larger capacitive loads necessitating higher drive strength. By optimizing drive strength, interference from the SPI communication to the analog front-end signal path can be minimized. Therefore, selecting the lowest effective drive strength for a system configuration is advised to maintain signal integrity and reduce potential noise.

### 3.2 SPI Protocol
The ADS1293 employs a serial peripheral interface (SPI) to access its control registers. The SPI protocol features a 16-bit access cycle, consisting of an 8-bit command field and an 8-bit data field. The command field includes a write or read bit along with a 7-bit address 


![Figure 2 Serial Interface Protocol](https://github.com/user-attachments/assets/c921b17a-ebb2-4003-9abd-fc94b1ed6ef8)
#### Figure 2 Serial Interface Protocol
The R/W bit designates the direction of the operation, with 0 for write and 1 for read. Data is sampled on the falling edge of the serial clock, while input data is driven on the rising edge of SCLK. Extended access cycles can be achieved using the auto-incrementing address mode, enabling access to multiple registers in a single cycle by keeping the chip select (CSB) asserted for additional clock cycles. This mode is particularly advantageous for reading continuous data blocks, such as the ECG data registers.

### 3.3 Initial Configuration and Continuous Data Acquisition
In the 3-Lead ECG example shown in Figure 1, the left-leg (LL), left-arm (LA), right-arm (RA) and right-leg (RL) electrodes are connected to the pins IN1, IN2, IN3 and IN4. The ADS1293 uses the Common-Mode Detector to measure the common-mode of the system by averaging the voltage at the input pins IN1, IN2 and IN3 and uses this signal in the right-leg drive feedback circuit. The output of the RLD amplifier is connected to RL through IN4 to drive the common-mode of the system. The chip utilises an external crystal oscillator of 4.096-MHz which connected between 2 pins that is XTAL1 and XTAL2 to create the clock for the device.

 The initial configuration involves writing specific values to the ADS1293 registers to set up the input channels, enable the common-mode detector, connect the RLD amplifier, and establish decimation rates. This is accomplished using LabVIEW’s block coding interface, where the configuration values are written to the registers to initialize the ADS1293.

For continuous data acquisition, the auto-incrementing addressing mode is utilized to continuously read ECG data from the ADS1293. Logic operations, including shift and AND operations, are performed to concatenate the data values. These concatenated values are then stored in a queue and subsequently plotted as waveforms in LabVIEW. This process ensures real-time monitoring and visualization of ECG signals.

#### TABLE I. SPI connection reference for ADS1293 ECG breakout board with NI myRIO 

| ADS1293 Pin | Function     | NI myRIO Pin     |
|-------------|--------------|------------------|
| MOSI        | Slave In     | DIO7 / SPI.MOSI  |
| MISO        | Slave Out    | DIO6 / SPI.MISO  |
| SCK         | Serial Clock | DIO5 / SPI.CLK   |
| CS          | Chip Select  | DIO4             |
| VCC         | Digital VDD  | +3.3V            |
| GND         | Digital GND  | DGND             |

The Table 1 shows the connections between the pins of the ADS1293 and the corresponding pins on the NI myRIO. Each pin on the ADS1293 has a specific function and is connected to a particular pin on the NI myRIO to enable proper communication and operation.

### 3.4 Auto-Incrementing Address Mode
The ADS1293 supports auto-incrementing address mode, enabling access to multiple registers by keeping chip select (CSB) asserted beyond the standard 16 clocks of the 16-bit protocol. In this mode, CSB must stay asserted during 8*(1+N) SCLK cycles, where N is the number of bytes to be read or written. This is useful for accessing a block of registers with incrementing addresses. For instance, to read pace and ECG data registers from address 0x30 to 0x3F (16 bytes), initiate a read command at address 0x30 and extend CSB assertion for 136 clock cycles (8+8*16). During auto-incrementing read access, the SDO pin outputs register contents every 8 clock cycles after the initial 8 clocks of the command field. Similarly, during auto-incrementing write access, data is written to the registers every 8 clock cycles after the initial 8 clocks of the command field. The automatic address increment stops at address 0x4F for both read and write operations.
	  
### 3.5	LabVIEW Programming

The LabVIEW code initializes the SPI communication, configures the ADS1293 registers, and continuously acquires ECG data.

#### TABLE 2. Register Map of ADS1293

| Register Name  | Description                          | Access | Address | Default Value |
|----------------|--------------------------------------|--------|---------|---------------|
| FLEX_CH1_CN    | Flexible Routing Switch Control (Ch1)| R/W    | 0x01    | 0x00          |
| FLEX_CH2_CN    | Flexible Routing Switch Control (Ch2)| R/W    | 0x02    | 0x00          |
| CMDET_EN       | Common-Mode Detect Enable            | R/W    | 0x0A    | 0x00          |
| RLD_CN         | Right-Leg Drive Control              | R/W    | 0x0C    | 0x00          |
| OSC_CN         | Output Clock Control and Clock Source| R/W    | 0x12    | 0x00          |
| AFE_SHDN_CN    | Analog Front End Shutdown Control    | R/W    | 0x14    | 0x00          |


The Table 2 shows the register map which provides a detailed information about key registers used in configuring the ADS1293 device for ECG (Electrocardiogram) data acquisition. Each entry includes the register name, its description detailing its function, the register address for accessing it, the type of access (Read/Write), and its default value upon initialization. This map serves as a reference for setting up and understanding the operational parameters of the ADS1293 in ECG monitoring applications.
To configure the ADS1293 device for ECG data acquisition, several registers need to be set with specific values. Firstly, the FLEX_CH1_CN register (address 0x01) is set to 0x11, connecting first Channel positive input that is INP to IN2 and the negative input that is INN to IN1, defining the input paths for the first ECG channel. Similarly, the FLEX_CH2_CN register (address 0x02) is set to 0x19, connecting second Channel INP to IN3 and INN to IN1, establishing the input configuration for the second ECG channel. The CMDET_EN register (address 0x0A) is configured to 0x07, enabling the common-mode detector on input pins IN1, IN2, and IN3 to reduce noise and ensure signal integrity. The RLD_CN register (address 0x0C) is set to 0x04, connecting the output of the Right-Leg Drive amplifier internally to IN4, which stabilizes the common-mode voltage and improves ECG signal quality.
Further, the OSC_CN register (address 0x12) is configured to 0x04 to use an external crystal, feeding the oscillator output to the digital section for accurate timing in data acquisition. The AFE_SHDN_CN register (address 0x14) is set to 0x24, shutting down the signal path for the unused Channel 3, conserving power and reducing potential interference with active channels. The R2_RATE register (address 0x21) is set to 0x02, configuring the decimation rate of R2 to 5 for all channels, making the data more manageable for processing and storage. For Channel 1, the R3_RATE_CH1 register (address 0x22) is set to 0x02, setting the decimation rate of R3 to 6, and similarly for the Channel 2, the R3_RATE_CH2 register (address 0x23) is set to 0x02 to ensure consistent data processing across channels.
Additionally, the DRDYB_SRC register (address 0x27) is configured to 0x08, setting the DRDY source to Channel 1 ECG, ensuring the data ready signal corresponds to the fastest channel. The CH_CNFG register (address 0x2F) is set to 0x30, enabling both the Channels 1 and 2 ECG for loop a read back mode, allowing continuous data acquisition and read-back for these channels. Finally, the CONFIG register (address 0x00) is set to 0x01 to start the data conversion process, initiating the continuous acquisition of ECG data. Time stamping is done, and the ECG signals are collected for the duration specified by the user, providing a precise and user-defined recording period for the ECG data.

## IV.RESULTS AND DISCUSSION      
 
The 3-lead ECG data acquisition module is developed and tested with the help of NI myRIO. The ECG signal is monitored using NI LabVIEW, Figure 3 shows the programming interface or GUI of the LabVIEW software.
![Figure 4 Programming Interface of LabVIEW](https://github.com/user-attachments/assets/42e9e71c-9452-41f9-8b4d-3feb2710728f)
#### Figure 3  Programming Interface of LabVIEW


![Figure 5 ECG Data Acquisition Setup](https://github.com/user-attachments/assets/38cefd3e-79f8-4c0e-bec2-b5542feb6180)
#### Figure 4 ECG Data Acquisition Setup


ADS1293 module is interfaced with the NI myRIO using jumper wires to ensure accurate signal transmission which is demonstrated in Figure 4. The ADS1293 communicates with the NI myRIO through the SPI (Serial Peripheral Interface) protocol which enables a high-speed data transfer. The ECG electrodes are connected using a 3.5 mm jack, which allows for easy attachment and detachment. The captured waveforms for channel 1 and channel 2 ECG are shown in Figures 5 and 6, respectively.

![Figure 7 Channel 1 ECG Waveform](https://github.com/user-attachments/assets/08cdf5c0-ee5a-488c-8385-b4bd439a86cd)
#### Figure 5 Channel 1 ECG Waveform


![Figure 6 Channel 2 ECG Waveform](https://github.com/user-attachments/assets/b501c860-6112-4ce5-a86a-9e4f0a3c435c)
#### Figure 6 Channel 2 ECG Waveform
   


V. CONCLUSION  
        The ADS1293-based ECG monitoring system represents a significant advancement in healthcare technology, offering an effective solution for continuous cardiac monitoring. The successful integration of hardware components, real-time signal processing and user-friendly interface design highlights the practicality of employing Analog Front-End (AFE) devices like the ADS1293 in ECG monitoring applications.
Remote monitoring capabilities are carried out, which enables the analysis and storage of ECG data. Utilising the graphical user interface of LabVIEW, waveform plotting and analysis. This system demonstrates the potential to transform how ECG monitoring is conducted and the way for enhanced healthcare solutions in the ECG monitoring domain.


VI.  REFERENCES 
 
[1] H. T. Yew, M. F. Ng, S. Z. Ping, S. K. Chung, A. Chekima, and J. A. Dargham, "IoT Based Real-Time Remote Patient Monitoring System," 2020 16th IEEE International Colloquium on Signal Processing & Its Applications (CSPA), Langkawi, Malaysia, 2020, pp. 176-179, doi: 10.1109/CSPA48992.2020.9068699.

[2] T. Shaown, I. Hasan, M. M. R. Mim, and M. S. Hossain, "IoT-based Portable ECG Monitoring System for Smart Healthcare," 2019 1st International Conference on Advances in Science, Engineering and Robotics Technology (ICASERT), Dhaka, Bangladesh, 2019, pp. 1-5, doi: 10.1109/ICASERT.2019.8934622.

[3] M. Neyja, S. Mumtaz, K. M. S. Huq, S. A. Busari, J. Rodriguez, and Z. Zhou, "An IoT-Based E-Health Monitoring System Using ECG Signal," GLOBECOM 2017 - 2017 IEEE Global Communications Conference, Singapore, 2017, pp. 1-6, doi: 10.1109/GLOCOM.2017.8255023. 
[4] Sahu, M. L., Atulkar, M., Ahirwal, M. K., & Ahamad, A. (2021). IoT-enabled cloud-based real-time remote ECG monitoring system. Journal of Medical Engineering & Technology, 45(6), 473–485. https://doi.org/10.1080/03091902.2021.1921870
[5] Yang, Z., Zhou, Q., Lei, L. et al. (2016). An IoT-cloud Based Wearable ECG Monitoring System for Smart Healthcare. J Med Syst 40, 286. https://doi.org/10.1007/s10916-016-0644-9
[6] Pagadala Pavan Kumar, Thokala Santhosh Naidu, S.Vishnu (2019). Retrieval Number: A10211291S52019/2019©BEIESP. DOI: 10.35940/ijeat.A1021.1291S52019
[7] S. Joseph, D. F. D. Shahila, and S. Patnaik, "IOT based Remote Heartbeat Monitoring," 2019 International Conference on Advances in Computing, Communication and Control (ICAC3), Mumbai, India, 2019, pp. 1-5, doi: 10.1109/ICAC347590.2019.9036735
[8] Rahman, Md. Obaidur; Mehedi Shamrat, F. M. Javed; Kashem, Mohammod Abul; Akter, Most. Fahmida; Chakraborty, Sovon; Ahmed, Marzia; Mustary, Shobnom (2022). International Journal of Electrical & Computer Engineering, 12(4), 3739. DOI: 10.11591/ijece.v12i4.pp3739-3751
[9] A. Rahman, T. Rahman, N. H. Ghani, S. Hossain, and J. Uddin, "IoT Based Patient Monitoring System Using ECG Sensor," 2019 International Conference on Robotics, Electrical and Signal Processing Techniques (ICREST), Dhaka, Bangladesh, 2019, pp. 378-382, doi: 10.1109/ICREST.2019.8644065
[10] G. Xu, "IoT-Assisted ECG Monitoring Framework with Secure Data Transmission for Health Care Applications," in IEEE Access, vol. 8, pp. 74586-74594, 2020, doi: 10.1109/ACCESS.2020.2988059
[11] Hasan, D., & Ismaeel, A. (2020). Designing ECG Monitoring Healthcare System Based on Internet of Things Blynk Application. JASTT, 1(2), 106-111

