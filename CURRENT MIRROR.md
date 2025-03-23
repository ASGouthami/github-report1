# Experiment 6 : CURRENT MIRROR (Design in LTspice using 180 nm technology lib)
## Introduction :
A current mirror circuit is an essential analog building block used to replicate and regulate current in integrated circuits. It ensures that the output current closely matches the reference current, regardless of load variations. Commonly implemented using MOSFETs or BJTs, current mirrors are widely used in biasing, active loads, and current amplification in analog and mixed-signal circuits. The project aims to develop efficient mirror circuits, simulate their performance, and analyze the results in terms of gain, accuracy, and power consumption.

Here is a circuit of basic current mirror:

![Screenshot 2025-03-23 153311](https://github.com/user-attachments/assets/41ff46a4-edbc-4463-928a-7c0fff060b5b)

## Aim of the experiment ( Design question) : Design and analyse current mirror circuit as a active load in amplifier circuits.

### circuit diagram:
![Screenshot 2025-03-23 155247](https://github.com/user-attachments/assets/4d32426c-47db-4e49-a5d6-880940f0bed1)

#### Given design requirements:
gain(Av) > -10 V/V, 
Supply voltage Vdd = 1.8V,
Power dissipation P<= 1mW

#### Design steps:
Step: Power Budget & Total Current

Given: 𝑃_total<1𝑚𝑊, 𝑉𝐷𝐷=1.8𝑉

wkt, I_Total = P/ VDD =1mW/1.8v =0.55556mA

Since: 𝐼_total= 𝐼_ref+𝐼_x

therefore, I_ref =I_x = I_total/2 = 0.2778mA

## Procedure:
For LTspice simulation, TSMC018 library file was included which is crucial for acccurate MOSFET simulation in TSMC 0.18um( 180nm)CMOS technology. Stored this library file in the LTspice folder or the same directory as our simulation file. Carried out DC, AC and Transcient analysis of the differential amplifier circuit.

### Current mirror for aspect ratio 1:1 

To obtain the current value according to the given ratio, the provided values of W/L for M1 is 101.592um/180nm , M2 is 101.592um/180nm, and M3 is 101.592um/180nm.
Vin is selected in such a way that all the mosfets should be in saturation region so the given Vin is 0.5V. for 1:1 ratio Iref=Ix

![Screenshot 2025-03-23 193541](https://github.com/user-attachments/assets/aa3e95a1-c0d8-4ae3-a599-02d6cb66d007)


### DC analysis (for 1:1 mirror ratio)


![Screenshot 2025-03-23 213656](https://github.com/user-attachments/assets/e4f9067a-f7b1-40c0-bddf-4c8d75f241f3)

The drain current with channel length modulation is expressed as:

ID = (1/2) * μn * Cox * (W/L) * (VGS - Vth)^2 * (1 + λ * VDS)

For a 1:1 current mirror, we have the relationship:

Iref = Ix

Using the equation for both transistors:

(1/2)*μn* Cox* (W1/L1)* (VGS1 - Vth)^2 * (1 + λ * VDS1) = (1/2)* μn* Cox* (W2/L2) * (VGS2 - Vth)^2* (1 + λ * VDS2)

For transistors in a 1:1 ratio:

W1/L1 = W2/L2

The equation reduces to:

(VGS1 - Vth)^2 * (1 + λ * VDS1) = (VGS2 - Vth)^2 * (1 + λ * VDS2)

If VGS1 = VGS2, then: (1 + λ * VDS1) = (1 + λ * VDS2)

This implies VDS1 = VDS2, ensuring the current mirror operation remains consistent.

The aspect ratio of MOSFET M3 and M2 is made equal, and  here from the simulation we can see that 𝑉𝑥 is approximately equal to 𝑉𝑜𝑢𝑡.

where for Mosfet M3 and M2, W=101.592um and l=180nm. 

Both NMOS and PMOS satisfies the condition of saturation region.


### Transient analysis (for 1:1 mirror ratio): 
Transient analysis in LTSpice is used to simulate a circuit’s time-domain response to time-varying inputs such as pulses, sine waves, or step inputs. Transient analysis is crucial in high speed applications where rise time, fall time, propagation delay determines the amplifiers suitability for fast signals. It evaluates the behavior of mosfet in response to sudden changes in input voltage and load.

Performed the transient analysis keeping the sinusoidal voltage signal DC offset as 0.5V, amplitude 20mV , frequency 1KHz and the AC amplitude as 1V. In the configure analysis, select stop time as 5ms. And the output waveform had amplitude of 0.5957V (peak voltage).
![Screenshot 2025-03-23 190342](https://github.com/user-attachments/assets/55831373-6952-4a32-be29-9c5febc39864)

![Screenshot 2025-03-23 190759](https://github.com/user-attachments/assets/ff34bfa5-f657-47ea-b1b7-1bc3f25136ac)



### AC analysis (for 1:1 mirror ratio): 

#### Steps to get Ac analysis Waveform:

   * In simulation tab select AC Analysis.
   * In the AC Analysis tab, select Type of Sweep as Decade.
   * Enter the number of points per decade (ex:20) and the frequency range ( 0.1Hz to 1THz).

![Screenshot 2025-03-23 190006](https://github.com/user-attachments/assets/b67c9a81-f5ef-4374-9296-73e4ffefc804)

Gain is 29.1dB

### Current mirror for aspect ratio 1:2 

As we know It=Iref+Ix

Therefore, for 1:2 aspect ratio 2*Iref=Ix

It = Iref + 2*Iref

So,Iref=It/3

It=P/Vdd

It=1mW/1.8V

It=0.555mA.

Therefore,Iref=0.185mA.

Here ,The aspect ratio of MOSFET M2 is twice of M3

To obtain the current value according to the given ratio, the provided values of W/L for M1 is 135um/180nm , M2 is 203.184um/180nm, and M3 is 101.592um/180nm.


![Screenshot 2025-03-23 235339](https://github.com/user-attachments/assets/5fa3c940-bee3-4dce-9f1d-04cad6d326e4)

### DC analysis (for 1:2 mirror ratio) :

![Screenshot 2025-03-23 235813](https://github.com/user-attachments/assets/f9aac8cf-ad58-4754-bb77-9d22a3a849a1)

### Transient analysis ( for 1:2 mirror ratio) :

    * Replace DC input with an AC signal.
    
    * Use SINE(dc_offset, Amplitude, Frequency).
    
    * Go to "Simulate" > "Edit Simulation Cmd" > "Transient". 
    
    * Set Stop Time: 5ms.
    
    * Our dc_offset = 0.5V and assume amplitude as 20mV and frequency as 1Khz. And the amplitude of obtained output waveform was 0.585V (peak voltage)


![Screenshot 2025-03-24 000352](https://github.com/user-attachments/assets/ba4b3a6b-a7b0-4da5-9d18-6ae762d3e760)


![Screenshot 2025-03-24 000312](https://github.com/user-attachments/assets/9e388b17-37bc-445b-9e45-3920218f3750)

### AC analysis  ( for 1:2 mirror ratio) :


![Screenshot 2025-03-24 003304](https://github.com/user-attachments/assets/b70ca731-19b2-435d-be72-47621ce9f200)


Gain is 29.102dB








