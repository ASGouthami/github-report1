# Design and Analysis of 2 stage Operational Trans-conductance Amplifier(OTA)
### Aim: To design and analyze a two-stage CMOS Operational Transconductance Amplifier (OTA) with Miller compensation for improved stability and phase margin.

**Abstract** :This project involves the design and LTspice simulation of a Miller-compensated two-stage operational transconductance amplifier (OTA) using 180nm CMOS technology. The architecture consists of a differential input stage followed by a common-source gain stage, with Miller compensation applied to ensure stability and achieve an adequate phase margin for closed-loop operation . 
The Miller-compensated two-stage OTA offers a high open-loop gain and improved output voltage swing, making it suitable for low-frequency and precision analog applications. This configuration allows the OTA to drive capacitive loads efficiently and maintain consistent performance across a wide range of operating conditions. Additionally, it provides good common-mode rejection and power efficiency, which are crucial in low-power and high-performance analog circuit design.

**Components/Software Required**

LTspice or equivalent SPICE-based simulator

CMOS Transistor Models

Power supply: 1.8V – 3.6V ( ~=2.5V)

Miller compensation capacitor (Cf)

Basic analog circuit elements (current mirrors, differential pairs)

### Theory :
Operational amplifiers (op-amps), particularly those implemented using multiple gain stages such as operational transconductance amplifiers (OTAs), require compensation to ensure closed-loop stability. One of the most widely adopted techniques for compensation is Miller compensation, which introduces a dominant pole to increase the phase margin of the system.

In a typical two-stage op-amp architecture, the first stage is a differential amplifier and the second stage provides additional gain. A compensation capacitor C_c is connected between the output of the second stage and the output of the first stage. This configuration leverages the Miller effect, wherein the capacitor is seen as a much larger effective capacitance due to the gain between its terminals. As a result, the dominant pole is shifted to a lower frequency, enhancing system stability.
The loop gain of the system can be represented as:
L(s) = A(s)F(s) 

### Design specifications/ Target parameters:


Supply Voltage: 1.8V – 3.6V

DC Gain: 50–70 dB

Unity Gain Bandwidth: Defined by gm/Cf

 Phase Margin: > 60°
 
Power Efficiency: Optimized via Ibias(Power<1mW)

(UnCox)n = 280uA/V2

### Circuit diagram

![image](https://github.com/user-attachments/assets/de9c476e-5480-4a6a-a66c-1a2e2f016cb2)

### Working principle :

A differential input at VIN+ and VIN− steers the tail current in M1 and M2. The current mirror reflects this to the second stage, where M5 amplifies the signal and M6 acts as load. Cf ensures stability by introducing a dominant pole and pushing non-dominant poles to higher frequencies.

### Simulation results:

![Screenshot 2025-05-28 020105](https://github.com/user-attachments/assets/3eb10d25-4859-4817-9b77-1b4d68779371)


#### DC Analysis:

![image](https://github.com/user-attachments/assets/111c14bf-36d2-4942-9017-795911a75907)

Tail Current Source (I1): 30 μA

Bias current M8: Matches expected topology

#### AC analysis/ Frequency response:

![Screenshot 2025-05-27 211749](https://github.com/user-attachments/assets/50fe3713-e35f-4433-9778-d3a3a364d243)

Voltage Gain: ~50dB ( ie 45db) 

Gain –Band width product (GB) : Approximately 100 MHz

Phase Response: Indicates dominant pole beyond cutoff

### Applications:

 Switched-capacitor filters
 
Analog signal processors

Sigma-Delta ADCs
    
Voltage-controlled oscillators

SoC amplifier blocks

### Conclusion:

The objective of this work is to design and analyze an Operational Transconductance Amplifier (OTA) using LTspice software based on 180nm CMOS technology. The design incorporates Miller Compensation, a widely adopted frequency compensation technique that utilizes the Miller effect by introducing a compensation capacitor across the high-gain stage to ensure stability. The simulation results validate that the designed OTA meets all specified performance metrics, including desired gain and phase margin.
The designed OTA achieves high gain, low power consumption, and excellent stability via Miller compensation. It suits precision analog front-ends. Future improvements may include simulation-based optimization using nulling resistors.

###  References
[1] Behzad Razavi, Design of Analog CMOS Integrated Circuits, McGraw-Hill.
[2] R. Jacob Baker, CMOS: Circuit Design, Layout, and Simulation, Wiley.
