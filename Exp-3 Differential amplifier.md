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


 
![Screenshot 2025-03-04 201203](https://github.com/user-attachments/assets/37ebbf0a-f323-4916-971e-996e0e48c8f3)

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


  For LTspice simulation, TSMC018 library file was included which is crucial for acccurate MOSFET simulation in TSMC 0.18um( 180nm)CMOS technology. Stored this library file in the LTspice folder or the same directory as our simulation file. Carried out DC, AC and Transcient analysis of the CS amplifier circuit.

  


 
