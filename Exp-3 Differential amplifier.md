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

B) Resistor Rss replaced with current source Iss

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

#### 1.DC Analysis- To fix the operating point (Q-point):
In DC analysis the goal is to establish the stable operationg point for the MOSFET, ensuring it remains in the saturation region for proper amplification.

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



** Now, increase the Vincm to 1.3V from 1.2V (0.1V increase), these are the respective changes.

Vocm changes to 1.1V from 1.25V and Vp changes to 0.46V from 0.4V.

![Screenshot 2025-03-05 003029](https://github.com/user-attachments/assets/8a940557-780d-4170-8d87-030519da13c5)

![Screenshot 2025-03-05 003124](https://github.com/user-attachments/assets/87b60173-aea2-4d11-8ca1-3d1342629503)

so, there is a slight variation in the Q-point as (0.644V, 0.576mA)


#### 2. Transient Analysis:

Transient analysis in LTSpice is used to simulate a circuit’s time-domain response to time-varying inputs such as pulses, sine waves, or step inputs. Transient analysis is crucial in high speed applications where rise time, fall time, propagation delay determines the amplifiers suitability for fast signals. It evaluates the behavior of mosfet in response to sudden changes in input voltage and load.

Performed the transient analysis keeping the sinusoidal voltage signal DC offset as 1.2V, amplitude 50mV , frequency 1KHz and the AC amplitude as 1V. In the configure analysis, select stop time as 5ms.

Input waveform and output waveform
![Screenshot 2025-03-04 234256](https://github.com/user-attachments/assets/f1c40720-3a89-40b4-96d8-6d93181c473e)

Input and output waveform together

![Screenshot 2025-03-04 233507](https://github.com/user-attachments/assets/e07dcf48-8e41-454b-8773-59ce51fbc6a8)

From the graph ,we can observe the 180 degree phase shift in the output signal and the output voltage (at Vocm node) is amplified .

Input voltage amplitude given was 50mV.

From the graph,
Overall Gain(Av) = Vout_peak/Vin_peak 

 = 0.199/0.05 = 3.98V/V

 From calculations,
 gm = 2ID/Vov = (2* 0.5m)/ (0.8 - 0.495)
   = 3.278m

 Rout = Rd = 1.9Kohm
 
 Overall gain :Av = gm * Rd
 
 = 3.278m * 1.9K = 6.22V/V. 

 #### 3. AC analysis:

The AC analysis in LTspice is used to study the frequency response of an amplifier, including gain, bandwidth and phase shift. In AC analysis MOSFET is treated as a linear small-signal amplifier, where the drain current is proportional to small variations in gate volatge .By applying a small-signal AC input, we can know how the circuit amplifies signals and how it behaves under varying frequencies.

For the same circuit, in the configure analysis select decade as type of sweep, with starting frequenciy o.1Hz and stop frequency as 1THz. 

 ![Screenshot 2025-03-05 001349](https://github.com/user-attachments/assets/fb8ea219-02f5-4990-9343-5d51d7474067)

From the graph , the gain in dB scale is 12.6dB - 3dB = 9.6dB

#### 4. To calculate maximum input swing and output swing

Vincm_min = Vth1 + Vov = 0.495 + 0.4 = 0.895V

Vincm_max = VDD -(RD*Iss)/2 + Vth = 2.2 -(1.9k * 1m)/2 + 0.495 = 1.745V

Therefore Vincm = (Vincm_min + Vincm_max)/2 = 1.32V

and Vocm_min = Vov1 +Vov3 = (0.8 - 0.495) +0.4 = 0.705V

Vocm_max = VDD - IDRD = 2.2 -(0.5m* 1.9K) = 1.25V

Therefore Vocm = (Vocm_min + Vocm_max)/2 = 0.977V


![Screenshot 2025-03-05 010122](https://github.com/user-attachments/assets/15e1c509-e9be-4955-b36c-5ded18677781)

Here the dc offset voltage is set to 1.32V, input amplitude to 500mV, to observe the clipped output waveform.

The Vo_pp (of clipped waveform) was 1.693V

### B) Resistor Rss replaced with current source Iss:

Replacing R3 with an active current source improves gain and CMRR. Better performance can be achieved by using an active current source instead of R3.

#### 1.DC analysis - To fix the operating point (Q-point):

In DC analysis the goal is to establish the stable operationg point for the MOSFET, ensuring it remains in the saturation region for proper amplification.

![Screenshot 2025-03-05 012553](https://github.com/user-attachments/assets/e6996cab-0a91-4bfb-b728-36baa274f855)

![Screenshot 2025-03-05 012058](https://github.com/user-attachments/assets/c145e2ab-7fbe-435c-9063-56668775b322)


Mosfet aspect ratio was same ie, L= 180nm, W = 6.4175um

Verified the mosfets are in saturation region by : VGD <=Vtn and VDS >= Vov.

The Q-point of both the mosfets are (0.85V, 0.5mA).

#### 2. Transient analysis:
Performed the transient analysis keeping the sinusoidal voltage signal DC offset as 1.2V, amplitude 50mV , frequency 1KHz and the AC amplitude as 1V. In the configure analysis, select stop time as 5ms.

Input and output waveform of MOSFET1(M1)
![Screenshot 2025-03-05 014415](https://github.com/user-attachments/assets/d67624b4-3ce3-4dd0-8b57-f4eadfe5b6e4)

Input and output waveforms of both MOSFETs (M1 and M2)


![Screenshot 2025-03-05 014252](https://github.com/user-attachments/assets/a5ea3abc-f150-457b-a254-932186fef4ac)

From the graph ,we can observe the 180 degree phase shift in the output signal and the output voltage (at Vocm node) is amplified .

Input voltage amplitude given was 50mV.

From the graph,

Overall Gain(Av) = Vout_peak/Vin_peak

=0.1992/0.05 = 3.984V/V


 From calculations,
 gm = 2ID/Vov = (2* 0.5m)/ (0.8 - 0.495)
   = 3.278m

 Rout = Rd = 1.9Kohm
 
 Overall gain :Av = gm * Rd
 
 = 3.278m * 1.9K = 6.22V/V. 

 #### 3.AC analysis:

 The AC analysis in LTspice is used to study the frequency response of an amplifier, including gain, bandwidth and phase shift.

 For the same circuit, in the configure analysis select decade as type of sweep, with starting frequenciy o.1Hz and stop frequency as 1THz. 


![Screenshot 2025-03-05 015726](https://github.com/user-attachments/assets/b5095a63-b96c-4940-9da5-5cc554a482c8)


From the graph , the gain in dB scale is 12.6dB - 3dB = 9.6dB

#### 4. To calculate maximum input swing and output swing

As calculated earlier,

Vincm = (Vincm_min + Vincm_max)/2 = 1.32V

and  Vocm = (Vocm_min + Vocm_max)/2 = 0.977V


Input and output at M1
![Screenshot 2025-03-05 020912](https://github.com/user-attachments/assets/728209ea-f81f-41e2-9927-861330560eb9)

Input and output at both M1 and M2
![Screenshot 2025-03-05 020845](https://github.com/user-attachments/assets/a23db349-bc3b-4de2-9440-f9e3054b407a)

Here the dc offset voltage is set to 1.32V, input amplitude to 500mV, to observe the clipped output waveform.

The Vo_pp (of clipped waveform) was 1.697V

### C) Resistor Rss replaced with NMOSFET:
When the tail resistor (R3R3​) is replaced by an NMOS current source, the differential amplifier exhibits improved performance in terms of gain, output swing, and common-mode rejection.
Provides better biasing and stability compared to a simple resistor or ideal current source.

#### 1.DC analysis - To fix the operating point (Q-point):

In DC analysis the goal is to establish the stable operationg point for the MOSFET, ensuring it remains in the saturation region for proper amplification.

![Screenshot 2025-03-05 022137](https://github.com/user-attachments/assets/35d11402-7e36-445e-b54f-eb6261e9fbe4)


![Screenshot 2025-03-05 022906](https://github.com/user-attachments/assets/fe178540-0aec-4d8a-95eb-4b0866f52906)

Here the bias voltage(gate voltge of M3) must be calculated to ensure that the mosfet is in saturation region.

It is given by : Vb = Vp + Vtn
 Vb = 0.4V + 0.49V = 0.89V

 and Length and Width of M3 is
 
![Screenshot 2025-03-05 023254](https://github.com/user-attachments/assets/75df5c2c-3612-48a9-bf0c-df3b79b73ade)

Verified the mosfets are in saturation region by : VGD <=Vtn and VDS >= Vov.

Therefore Q-point of M3 is (0.4V, 1mA)
Q-point of M1 and M2 is (0.85V, 0.5mA)


#### 2. Transient analysis:
Performed the transient analysis keeping the sinusoidal voltage signal DC offset as 1.2V, amplitude 50mV , frequency 1KHz and the AC amplitude as 1V. In the configure analysis, select stop time as 5ms.

Input and output waveforms at M1
![Screenshot 2025-03-05 024345](https://github.com/user-attachments/assets/b064b44b-56a7-477e-a49f-98bf559e7339)

Input and output waveforms at M1 and M2
![Screenshot 2025-03-05 024105](https://github.com/user-attachments/assets/4315dafb-14c4-420a-99b5-18f96394275c)

From the graph ,we can observe the 180 degree phase shift in the output signal and the output voltage (at Vocm node) is amplified

Input voltage amplitude given was 50mV.

From the graph,

Overall Gain(Av) = Vout_peak/Vin_peak
= 0.1992V/0.05V  = 3.984V/V


 From calculations,
 gm = 2ID/Vov = (2* 0.5m)/ (0.8 - 0.495)
   = 3.278m

 Rout = Rd = 1.9Kohm
 
 Overall gain :Av = gm * Rd
 
 = 3.278m * 1.9K = 6.22V/V. 

 #### 3.AC analysis:

 The AC analysis in LTspice is used to study the frequency response of an amplifier, including gain, bandwidth and phase shift.

 For the same circuit, in the configure analysis select decade as type of sweep, with starting frequenciy o.1Hz and stop frequency as 1THz. 

 ![Screenshot 2025-03-05 025520](https://github.com/user-attachments/assets/7b98184f-ad33-4d7d-9650-12cf90198985)

 From the graph , the gain in dB scale is 12.6dB - 3dB = 9.6dB

 #### 4. To calculate maximum input swing and output swing

As calculated earlier,

Vincm = (Vincm_min + Vincm_max)/2 = 1.32V

and  Vocm = (Vocm_min + Vocm_max)/2 = 0.977V


Input and output at M1
![Screenshot 2025-03-05 030012](https://github.com/user-attachments/assets/b7628f97-4b08-4a9a-a8fc-09a5da47efd8)

Input and output at both M1 and M2
![Screenshot 2025-03-05 025948](https://github.com/user-attachments/assets/6f39d93c-2209-4286-8bb8-573f1c3b276d)

Here the dc offset voltage is set to 1.32V, input amplitude to 500mV, to observe the clipped output waveform.

The Vo_pp (of clipped waveform) was 1.725V.
