# Linear integrated circuits-exp1
## DC,AC and Transient analysis of CS amplifier
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

### Component details:
For LTspice simulation, TSMC018 library file was included which is crucial for acccurate MOSFET simulation in TSMC 0.18um( 180nm)CMOS technology. Stored this library file in the LTspice folder or the same directory as our simulation file. Drain resistor converts the drain current to output voltage, limits the current through the transistor and affects the small-signal gain.

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
![Image](https://github.com/user-attachments/assets/02d80bac-c555-4f31-9347-0314dee3c94a)
From the simulation: if L= 180nm, W= 1um
                    Vout= 1.647V and Id= 0.0001527A


If the power rating( power dissipation across the resistor) is 100uW, given supply voltage is 1.8V, then the current through the resistor is given by:

 Id = power/Voltage = 100u/1.8
                     
= 5.55*10^-5  (or 55.5uA)

 
Now, (from the above calculation) Since the calculated value of current does not match the simulated value, must try maintaining the mosfet length at 180nm and vary/adjust the width to get the required current value.


put tableeee here

NMOS transistor should be operated in saturation region, this can be confirmed by the DC operating point analysis.

Id= 55.5uA

1)Vgd<= Vtn  and 2)Vds>=(Vgs-Vtn)

*Vds= Vd- Vs = 1.744-0 =1.744

*Vgd = 0.9-1.744 = -0.844

*Vov = Vgs-Vtn = (0.9-0) -0.366 = 0.534

So, therefore 1)--> -0.844<=0.366

2)--> 1.744>=0.534  

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
                                          



 

                                         








