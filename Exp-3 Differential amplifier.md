# Experiment-3 : Design and Analysis of MOS differential amplifier circuit

## Introduction
A MOS differential amplifier is a key circuit in analog design, used in operational amplifiers, comparators, and analog signal processing. It provides amplification of the difference between two input signals while rejecting common-mode signals (such as noise).

A “single-ended” signal is defined as one that is measured with respect to a fixed potential, usually the
ground. A differential signal is defined as one that is measured between two nodes that
have equal and opposite signal excursions around a fixed potential .  

![Screenshot 2025-03-03 195927](https://github.com/user-attachments/assets/dbdc7334-4b72-469b-873c-d8123b582256)

Here is a basic differential pair

![Screenshot 2025-03-03 200417](https://github.com/user-attachments/assets/7d213267-955f-45a9-994c-d0c76716bb2c)

The two differential inputs, Vin1 and Vin2, having a certain CM level, Vin,C M , are applied to the gates. The
outputs are also differential and swing around the output CM level, Vout,C M .
Such a circuit indeed offers
some of the advantages of differential signaling: high rejection of supply noise, higher output swings, etc.

## Aim of the experiment: Design and analyse differential amplifier circuit for the following specifications:
VDD= 2.2V , P<=2.2mW , Vincm =1.2V , Vocm = 1.25V , Vp = 0.4V 
Perform: DC analysis, transient analysis, frequency response and extract the parameters.


![Screenshot 2025-03-04 194042](https://github.com/user-attachments/assets/8a00714e-48c5-4f41-8c8d-d9f0e7a79d9a)

solution: we know that P= VI -->Iss = P/V = 2.2mW/2.2V = 1mA

 Iss = 1mA

 ID = Iss/2 = 1m/2 --> ID = 0.5mA

 (from VDD = IDRD + Vocm)

 RD = (VDD - Vocm)/ID --> RD = (2.2-1.25)/0.5m --> RD = 1.9Kohm

 Rss = Vp/Iss = 0.4/1m --> Rss = 400ohm

 ## circuit diagram:

 A)With Resistor Rss
 
![Screenshot 2025-03-04 201203](https://github.com/user-attachments/assets/37ebbf0a-f323-4916-971e-996e0e48c8f3)

B) Resistor Rss replaced with current source

![Screenshot 2025-03-04 224142](https://github.com/user-attachments/assets/6eb6b9e5-bfb7-4105-b32b-bedd5648c84c)


C) Resistor Rss replaced with NMOSFET

![Screenshot 2025-03-04 224733](https://github.com/user-attachments/assets/f3eadefa-6944-4821-86f6-c9b410c3bb90)


## Key components and their roles:
1) M1 & M2 (CMOSN - NMOS Transistors):

 Act as the differential pair, amplifying the difference between the input voltages VinCM1 and VinCM2.

 2) R1 & R2 (1.9kΩ Resistors):

 Act as load resistors, converting the amplified current difference into output voltage signals VoCM1 and VoCM2.

 3) R3 (400Ω Resistor):
   
   Provides a stable bias for the differential pair by setting the tail current through the NMOS transistors.
   
4) V1 & V2 (1.2V, 1.2V Voltage Sources):

 Provide the differential input signals to the amplifier.

5) V3 (2.2V Voltage Source):

 Acts as the power supply (Vdd) for the circuit.

 6) Vp (Common Source Node):

  Connects the sources of M1 and M2 and helps define the operation point of the transistors. 

## Procedure:
  For LTspice simulation, TSMC018 library file was included which is crucial for acccurate MOSFET simulation in TSMC 0.18um( 180nm)CMOS technology. Stored this library file in the LTspice folder or the same directory as our simulation file. Carried out DC, AC and Transcient analysis of the differential amplifier circuit.

## Design and analysis
###  A) With Resistor Rss:

The circuit is designed to reject common-mode signals and amplify only the difference between VinCM1 and VinCM2.The output swing is limited by the supply voltage VDD​ and transistor saturation conditions.

#### 1.DC Analysis- To fix the operating point (Q-point)


 ![Screenshot 2025-03-04 225421](https://github.com/user-attachments/assets/ea526cf7-3bc4-4e2b-8de4-2559819f84d9)

 
![Screenshot 2025-03-04 225805](https://github.com/user-attachments/assets/397f2226-e525-492b-9f7f-f66025aac647) ![Screenshot 2025-03-04 230120](https://github.com/user-attachments/assets/6916cee2-7526-40e9-8c2d-e66e86f968d1)

Length( of M1 and M2) = L = 180nm

Width ( of M! and M2) = W = 6.4125um

To verify the mosfets are in saturation region : VGD <= VTn

(1.2V -1.25V) <= 0.495V

-0.05V <= 0.495V

and VDS >= Vov

(1.25 - 0.4) >= (1.2 - 0.4) - 0.495

0.85V >= 0.305V

Therefore mosfets are in saturation region .

The Q-points of both the mosfets(M1 and M2) are (0.85V, 0.5mA)

#### 2. Transient Analysis

Transient analysis in LTSpice is used to simulate a circuit’s time-domain response to time-varying inputs such as pulses, sine waves, or step inputs. Transient analysis is crucial in high speed applications where rise time, fall time, propagation delay determines the amplifiers suitability for fast signals. It evaluates the behavior of mosfet in response to sudden changes in input voltage and load.

Input waveform and output waveform
![Screenshot 2025-03-04 234256](https://github.com/user-attachments/assets/f1c40720-3a89-40b4-96d8-6d93181c473e)

Input and output waveform together

![Screenshot 2025-03-04 233507](https://github.com/user-attachments/assets/e07dcf48-8e41-454b-8773-59ce51fbc6a8)

From the graph ,we can observe the 180 degree phase shift in the output signal and the output voltage (at Vocm node) is amplified .

Input voltage amplitude given was 50mV.

Gain = Vout_peak/Vin_peak 

 = 0.199/0.05 = 3.98V/V



