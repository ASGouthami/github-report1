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












