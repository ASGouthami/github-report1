# Linear integrated circuits-exp1
## DC,AC and Transient analysis of CS amplifier
### (Problem 1)
### Introduction:
The common source amplifier is the basic configuration of mosfet used in analog circuits. It serves as voltage amplifier where, the input is applied to gate terminal, output is taken from drain terminal, source terminal is grounded and the body terminal is connected to the lowest potential i.e gnd. 
The circuit has NMOS as active device, passive resistor(Rd) as load. The circuit is biased using a DC voltage source(1.8V here), and an AC input signal is applied to gate.
The analysis of CS amplifier involves- DC analysis,AC analysis and Transient analysis(using LTspice software)

objective: The objective of this report is to analyse the DC biasing conditions, gain, output impedence and frequency response.
### Key components used and their roles:
1.Vd(Drain supply voltage): Provides the nessesary DC biasing for the N-mosfet.

2.Rd(drain resistor):Provides the required voltage drop to amplify the signal, and sets the output voltage(DC operating point).

3. AC input(at gate): enables amplification by controling drain current.

### circuit diagram:
![Image](https://github.com/user-attachments/assets/126e8794-4bd5-4100-838e-90e58d624d87)

### Procedure:
For LTspice simulation, TSMC018 library file was included which is crucial for acccurate MOSFET simulation in TSMC 0.18um( 180nm)CMOS technology. Stored this library file in the LTspice folder or the same directory as our simulation file. Carried out DC, AC and Transcient analysis of the CS amplifier circuit.


### Component details:
 Drain resistor converts the drain current to output voltage, limits the current through the transistor and affects the small-signal gain.

Here NMOS transistor must operate in saturation region, for amplification.

Model:CMOSN

MOSFET lengt(L): 180nm

MOSFET Width(W):0.2um

Threshold Voltage(Vtn): 0.366V

Resistor(Rd):1K

Supply voltage(Vdd): 1.8V

Input AC signal(signal generator):
      * DC voltage(DC offset): 0.9V
      * Amplitude: 50mV
      * Frequency: 1KHz


### DC analysis( simulation):
In DC analysis the goal is to establish the stable operationg point for the MOSFET, ensuring it remains in the saturation region for proper amplification.

![Image](https://github.com/user-attachments/assets/02d80bac-c555-4f31-9347-0314dee3c94a)
From the simulation: if L= 180nm, W= 1um
                    Vout= 1.647V and Id= 0.0001527A


If the power rating( power dissipation across the resistor) is 100uW, given supply voltage is 1.8V, then the current through the resistor is given by:

 Id = power/Voltage = 100u/1.8
                     
= 5.55*10^-5  (or 55.5uA)

 
Now, (from the above calculation) Since the calculated value of current does not match the simulated value, must try maintaining the mosfet length at 180nm and vary/adjust the width to get the required current value.

| Length | Width | Id |
|--------|--------|--------|
| 180nm | 1um| 0.0001527 |
| 180nm | 2um | 0.000275 |
| 180nm |0.1um | 48.1uA | 
| 180nm |  0.2um| 55.5uA| 


NMOS transistor should be operated in saturation region, this can be confirmed by the DC operating point analysis.

Id= 55.5uA

1)Vgd<= Vtn  and 2)Vds>=(Vgs-Vtn)

*Vds= Vd- Vs = 1.744-0 =1.744

*Vgd = 0.9-1.744 = -0.844

*Vov = Vgs-Vtn = (0.9-0) -0.366 = 0.534

So, therefore 1)--> -0.844<=0.366

2)--> 1.744>=0.534  

The DC operating point is (1.744V, 55.5uA)


### Transient analysis:

Transient analysis in LTSpice is used to simulate a circuit’s time-domain response to time-varying inputs such as pulses, sine waves, or step inputs. Transient analysis is crucial in high speed applications where rise time, fall time, propagation delay determines the amplifiers suitability for fast signals. It evaluates the behavior of mosfet in response to sudden changes in input voltage and load.

![Image](https://github.com/user-attachments/assets/1777641c-ff17-4487-8528-bcab4ef5715b)

In this experiment ,we are finding the gain and output impedence of the circuit. Performed the transient analysis keeping the sinusoidal voltage signal DC offset as 0.9V, amplitude 50mV , frequency 1KHz and the AC amplitude as 1V. In the configure analysis, select stop time as 3ms.

From the graph(simulation):

For L=180nm, W = 0.2um

We can observe 180 degree phase shift in the amplified output voltage signal/wave.

We know that, gain is calculated by:

*gain = Vout/Vin

=1.744/0.9

 =1.93

* output impedence, Rout = Rd =1Kohm

   Overall gain: Av = gm * Rout

  =1.93*1K

  = 1.93K

  
 ### AC analysis

 The AC analysis in LTspice is used to study the frequency response of an amplifier, including gain, bandwidth and phase shift. In AC analysis MOSFET is treated as a linear small-signal amplifier, where the drain current is proportional to small variations in gate volatge .By applying a small-signal AC input, we can know how the circuit amplifies signals and how it behaves under varying frequencies.

 iD = gm*vgs
 where gm is the transconductance. The voltage gain of the amplifier is given by

 Av= -gm* RD 

 The negative sign indicates the 180 degree phase shift between the input and output signals.

 In the simulation,  for the same circuit go to edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of poinits per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected response.

![Image](https://github.com/user-attachments/assets/0cb3d795-6bf7-4e0c-a5a5-4e4c83270ad3)

From the above graph the gain is 2dB.

The gain is nearly constant (flat response) over a wide frequency range, which indicates a stable amplification in the mid-band region.

 The gain drops sharply at high frequencies, indicating the cutoff frequency (fH) or bandwidth limitation due to MOSFET capacitances (Cgs, Cgd) and parasitic effects.

 The gain remains stable across a wide range of frequencies before it starts to roll off at high frequencies.

 From the graph, fH is approximately in the GHz range, meaning the amplifier has a wide bandwidth.


 ### Inference

 1.The CS amplifier provides the voltage gain by inverting the input signal.
 
 2.The gain depends on Vgs, transistor parameters, and drain resistance.

 3. The circuit has flat gain response in the mid-frequency range.

 4. At high frequencies (>100 MHz to GHz range), the gain starts decreasing due to MOSFET parasitic capacitances (Cgs, Cgd).

 5. The upper cutoff frequency (fH) is in the GHz range, making the amplifier suitable for high-speed applications.

 6. The circuit is suitable for low to moderate gain amplification.

 7. Works well for high-speed applications due to its wide bandwidth.

 8. The circuit can be optimized for RF and analog signal processing.









### (Problem 2)
### Introduction

The common source amplifier is the basic configuration of mosfet used in analog circuits. It serves as voltage amplifier where, the input is applied to gate terminal of NMOS, output is taken from drain terminal, source terminal of nmos is grounded and the body terminal is connected to the lowest potential i.e gnd. 
The circuit has NMOS as active device, a passive resistor(Rd) is replaced by PMOS transistor, where its gate terminal is connected to a bias voltage Vb. The source of PMOS is biased using a DC voltage source(1.8V here), and body terminal of PMOS is connected to source.
The analysis of CS amplifier involves- DC analysis,AC analysis and Transient analysis(using LTspice software)

objective: The objective of this report is to analyse the DC biasing conditions, gain, output impedence and frequency response, when RD is replaced by PMOS in CS amplifier circuit.

### Key components used and their roles:
1. V1( 1.8 DC source): Provides the power supply voltage (Vdd) for the circuit, ensuring proper MOSFET operation.

2. PMOS: Acts as the active load or current source for the NMOS transistor (M2).
   
3. NMOS: Acts as the main amplifying transistor in a common-source configuration.
 
4.Vb( bias voltage, V2 here) : Provides a bias voltage to the PMOS transistor’s gate, setting the operating point.

5.V3- AC input(at gate of nmos): enables amplification by controling drain current.

### Circuit diagram:


![Screenshot 2025-02-17 202254](https://github.com/user-attachments/assets/40bff19a-091c-42cb-b310-6df73b56bd9f)

### Procedure:
For LTspice simulation, TSMC018 library file was included which is crucial for acccurate MOSFET simulation in TSMC 0.18um( 180nm)CMOS technology. Stored this library file in the LTspice folder or the same directory as our simulation file. Carried out DC, AC and Transcient analysis of the circuit.



### Component details:
Here NMOS and PMOS transistor must operate in saturation region, for amplification.

Model:CMOSN

MOSFET lengt(L): 240nm

MOSFET Width(W):480nm

Threshold Voltage(Vtn): 0.366V

Input AC signal(signal generator):
      * DC voltage(DC offset): 0.9V
      
   * Amplitude: 50mV
      
   * Frequency: 1KHz



Mode2:CMOSP

MOSFET lengt(L): 240nm

MOSFET Width(W):500nm

Threshold Voltage(Vtn): -0.39V

V1(DC source voltage) : 1.8V

Vb(bias voltage, V2): 0.42V


### DC analysis(Simulation):
In DC analysis the goal is to establish the stable operationg point for the MOSFET, ensuring it remains in the saturation region for proper amplification.

Again considering the Power rating as 100uW, given supply voltage is 1.8V, then the current through the circuit is given by:

 Id = power/Voltage = 100u/1.8
                     
= 5.55*10^-5  (or 55.5uA)

Now,we need to change the length(same for both transistors) and width of PMOS and NMOS . Vb must be set so as to keep both the transistors in saturation region.

|PMOS | NMOS | Vb | ID | Vout |
|--------|--------|--------|--------|--------|
| 1)L= 280nm,W= 500nm| L= 280nm, W= 480nm| 0.42V | 54.5uA | 1.376V|
|2) L= 280nm, W= 900nm | L= 280nm, W= 580nm | 0.3V | 57.3uA | 1.483V|
| 3)L= 320nm, W= 10.29um | L= 320nm, W= 0.61um | 0.9V | 52.4uA | 1.74V |
| 4)L = 240nm, W= 500nm | L= 240nm, W= 480nm | 0.42V | 55.54uA | 0.776V |

From the simulation, by dc analysis the only values for which for the transistors remain in saturation region is 4th values.

![Screenshot 2025-02-17 202355](https://github.com/user-attachments/assets/4b4d2273-f83c-443c-bfd0-c4813ba144b4)




* Conditions for PMOS to be in saturaion region are :

   Vgd>= Vtp --> (1) and Vds <= Vov --> (2)
  
  here Vg = 0.42V, Vd = 0.776V, Vtp = -0.39V, Vs = 1.8V
  
  (1) -->  0.42-0.776 >= -0.39
  
  -0.356V >= -0.39V
  
  (2) --> 0.776-1.8 <= (0.42-1.8) -(-0.39)
  
  -1.024V <= -0.99V

  Therefore PMOS is in saturation region.

* Conditions for NMOS to be in saturation region are :

    Vgd <= Vtn --> (3) and Vds >= Vov -->(4)

    here Vg = 0.9V, Vd = 0.776V, Vtn = 0.366V, Vs = 0V

   (3) --> 0.9 - 0.776 <= 0.366
 
    0.124 <= 0.366

    (4) --> 0.776 - 0 >= (0.9 - 0) - 0.366

     0.776V >= 0.534V

Therefore NMOS is in saturation region. 

so, Therefore, the dc bias voltage applied to the gate of PMOS is Vb = 0.42V

The DC operating point of PMOS is (-1.024V, 55.5uA)  (Vds, ID)

The DC operating point of NMOS is (0.776V, 55.5uA)








### Transcient analysis:

Transient analysis in LTSpice is used to simulate a circuit’s time-domain response to time-varying inputs such as pulses, sine waves, or step inputs. Transient analysis is crucial in high speed applications where rise time, fall time, propagation delay determines the amplifiers suitability for fast signals. It evaluates the behavior of mosfet in response to sudden changes in input voltage and load.


![Screenshot 2025-02-17 203047](https://github.com/user-attachments/assets/f638adb5-d0fa-45d5-b3ba-44b08e60317d)



In this experiment ,we are finding the gain and output impedence of the circuit. Performed the transient analysis keeping the sinusoidal voltage signal DC offset as 0.9V, amplitude 50mV , frequency 1KHz and the AC amplitude as 1V. In the configure analysis, select stop time as 3ms.

From the graph, we can see that the output signal is amplified( with amplitude of ~ 446.4mV, whereas input signal amplitude was 50mV). We can observe 180 degree phase shift in the amplified output voltage signal/wave.

We know that, gain is calculated by:

*gain = Voutp-p/Vinp-p

= (777.25-329.91)mV/ (950-900)mV

= 8.94






### AC analysis:


The AC analysis in LTspice is used to study the frequency response of an amplifier, including gain, bandwidth and phase shift. In AC analysis MOSFET is treated as a linear small-signal amplifier, where the drain current is proportional to small variations in gate volatge .By applying a small-signal AC input, we can know how the circuit amplifies signals and how it behaves under varying frequencies.

iD = gm*vgs
 where gm is the transconductance.

 In the simulation,  for the same circuit go to edit simulation option, change from transient to ac analysis. Set type of sweep as decade, number of poinits per decade as 20, start and stop frequency as 0.1Hz and 1THz to get the expected response.


![Screenshot 2025-02-17 203244](https://github.com/user-attachments/assets/efbe7861-c495-4725-a169-9eb66e37275f)

From the graph, the gain at low frequencies is approximately 24 dB.

The gain remains relatively stable up to a certain frequency.
At higher frequencies, the gain starts dropping sharply. The presence of parasitic capacitances in MOSFETs could be causing this roll-off.

Due to its high gain and wide bandwidth, this amplifier circuit can be used in RF and high-speed communication systems. High gain (~24 dB) at low frequencies.





### Inference:
1.The PMOS active load significantly improves gain and output resistance, leading to better amplification.

2. From the frequency response curve , the bandwidth is influenced by the parasitic capacitances of the PMOS transistor.

3. From AC analysis voltage gain is higher than CS amplifier with a resistive load.

4. When a PMOS transistor is used as the load, its output resistance  is much higher than a physical resistor, leading to a higher voltage gain.

5.The presence of parasitic capacitances in MOSFETs could be causing this roll-off.




## Conclusion:

1.Higher Gain: A PMOS load provides a much higher resistance than a resistor, increasing voltage gain.

2. Compact Design:CS amplifier with PMOS as resistive load takes up less space, making it ideal for integrated circuits (ICs).

3. Larger Output Swing: Allows better utilization of the supply voltage, enabling a wider output range.

4. Using a PMOS active load provides self-biasing, making the circuit more stable compared to using a resistor.

5. Lower Power Consumption: Reduces power dissipation compared to using a resistor.

   Replacing a resistor with a PMOS active load significantly improves gain, power efficiency, and frequency response, making it the preferred choice in integrated circuit (IC) amplifiers.




















 

                                         








