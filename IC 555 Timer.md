# Design and simulation of 555 timer based Monostable and Astable multivibrators for pulse generation and pulse width control applications

## Introduction

The 555 timer integrated circuit (IC) is one of the most popular and versatile components used in analog electronics. It was introduced by Signetics in 1972 and has since found widespread applications in timers, oscillators, pulse generation, and waveform shaping circuits. The 555 timer can operate primarily in three modes: astable, monostable, and bistable. In this project, we focus on the astable and monostable modes to generate precise pulse waveforms and control pulse widths for applications such as pulse width modulation (PWM), timing delays, and triggering circuits.

555 timer can operate in multiple modes: Astable, Monostable, and Bistable.

The objective of this project is to design and simulate two experimental setups using the 555 timer IC in LTspice simulation software.

The first setup is an astable multivibrator generating a PWM waveform with a fixed pulse width of approximately 0.5 milliseconds.

The second setup is a monostable multivibrator triggered by the output of the astable circuit after passing through a differentiator and clipper stage. The monostable circuit produces a single output pulse whose width can be varied externally by changing component values.

    Here is the pin configuration of 555 timer IC
![Screenshot 2025-05-27 193839](https://github.com/user-attachments/assets/37cc1962-f113-41bf-b257-8b3d330868d1)


![Screenshot 2025-05-27 214430](https://github.com/user-attachments/assets/f0238470-b10e-4e34-a6b3-f40c314129f5)

 **Internal circuit of 555 timer IC**

3 Resistors: Create 1/3 Vcc and 2/3 Vcc.

2 Comparators: Compare input with reference voltages.

Flip-Flop: Stores output state.

Discharge Transistor: Controls capacitor discharge.

Output Stage: Drives the output pin.

**Operation:**

    When Pin 2 voltage < 1/3 Vcc → Output goes HIGH, discharge transistor OFF (capacitor charges).

    When Pin 6 voltage > 2/3 Vcc → Output goes LOW, discharge transistor ON (capacitor discharges).

 ### Monostable state
 Also known as a one-shot multivibrator.
It has only one stable state.

**Operation**: The 555 timer produces a single output pulse of a fixed duration in response to a trigger input (a negative pulseThis configuration consists of one stable and one unstable state. The stable state can be chosen as either high or low by the user. If the stable output is set at high (1), the output of the timer is high (1).

**Trigger**: A negative pulse at the trigger pin (Pin 2) starts the timing cycle.

**Output**: The output (Pin 3) goes HIGH for a time period 𝑇=1.1×𝑅×𝐶 then returns LOW. 

**Applications**: Pulse generation, timers, switch debouncing, missing pulse detection.

### Astable state
It is also known as a free-running multivibrator.
It has no stable state, hence the name astable.

**Operation**: The 555 timer continuously oscillates between HIGH and LOW states without any external trigger, generating a square wave (pulse train).This means there will be no stable level of output. So the output will be swinging between high and low. This character of unstable output is used as a clock or square wave output for many applications.

**Output**: The output (Pin 3) produces a continuous series of pulses with frequency and duty cycle controlled by two resistors and one capacitor.

Frequency & Duty Cycle:Frequency 𝑓=1.44/(𝑅1+2𝑅2)𝐶f , Duty Cycle depends on 𝑅1 and 𝑅2 .

**Application**s: Clock pulses, LED flashers, tone generation, PWM signals.

### Bistable state

Also known as a flip-flop multivibrator.
It has two stable states and can remain in either state indefinitely without any input signal.

In bistable mode, both the output states are stable. At each interrupt, the output changes from low (0) to high (1) and vice versa, and stays there. For example, if we have a high (1) output, it will go low(0) once it receives an interrupt and stays low (0) till the next interrupt changes the status. ​

## Problem statement: Generate the waveform with pulse width of 0.5ms using monostable multivibrator with 555 timer IC.

#### case 1: 

![Screenshot 2025-05-27 191108](https://github.com/user-attachments/assets/50ecd0a9-b1d3-415d-9bc9-bb61c052989b)


1.The input trigger just initiates the output change.

2.The duration of the output pulse (HIGH or LOW) is determined by the values of the resistor (R) and capacitor (C) in the timing circuit, not by the trigger pulse width.

#### case 2:

![Screenshot 2025-05-27 191754](https://github.com/user-attachments/assets/3973c701-82eb-4e5d-8be8-f5be1e34dad1)

1.It generates a single output pulse of fixed duration (1 ms).

2.During that 1 ms, it ignores any further triggers

3.Only after returning to the stable state, it can respond to a new trigger.

#### case 3:


![Screenshot 2025-05-27 192430](https://github.com/user-attachments/assets/b7934e8e-4969-4b91-ba48-7ab8f43d208b)

1.When the 0.2 ms trigger arrives, it activates the monostable.

2.The monostable then generates a fixed output pulse of 0.5 ms, regardless of the trigger pulse duration.

3.After 0.5 ms, the output returns to its stable (LOW) state.

### Astable multivibrator and monostable multivibrator using 555 timer IC

**AIM**: Generate pulse of width 0.5ms using 555 timer IC.

**Procedure**

 Build the circuit as per the Circuit diagram.
 
 Calculate the resistor R and capacitor C for Astable multivibrator Differentiator, clipper and Monostable multivibrator.
 
Analyze the capacitor charging and discharging Voltage per time.

Analyze the ton period when input is triggered.

**Calculations**:

![WhatsApp Image 2025-05-27 at 22 50 33_6942b42c](https://github.com/user-attachments/assets/6a177354-44e2-4d6c-a5c6-f674f3d78c5c)

![WhatsApp Image 2025-05-27 at 22 50 34_f8386334](https://github.com/user-attachments/assets/49604045-a276-4b86-b0cc-2b44cdab3451)

![WhatsApp Image 2025-05-27 at 22 50 35_9e04cfac](https://github.com/user-attachments/assets/d841fa3c-0628-4196-a0b7-561d2261f2f5)


#### case 1:

![Screenshot 2025-05-28 012256](https://github.com/user-attachments/assets/89a1b922-0276-4b6c-9576-0f185744173b)

First wave is output of Astable Multivibrator, Second waveform is Output of Differentiator Circuit output, 3rd wave is the output of Negative Clipper circuit and fourth waveform is output of Monostable Multivibrator pulse width is 0.5ms.

#### Case 2:

![Screenshot 2025-05-28 012546](https://github.com/user-attachments/assets/7f15618d-fba8-4da9-b8ad-37a656719200)

First wave is output of Astable Multivibrator, Second waveform is Output of Differentiator Circuit output, 3rd wave is the output of Negative Clipper circuit and fourth waveform is output of Monostable Multivibrator pulse width is 0.5ms. cap value .1u

#### case 3:

in case 3 the ton<toff which is not possible in astable Multivibrator , thus we can use an inverter to invert the pulse generated.
V1 is Output of the Astable Multivibrator, V2 is Capacitor Voltage of Astable Multivibrator, V3 is Output of Differentiator, V4 is Capacitor Voltage of Monostable Multivibrator, Vout is Output of Monostable Multivibrator pulse width is 0.5ms

## Inference:


Controlling ON and OFF Times Isn't Always Straightforward We saw that changing resistor and capacitor values lets us control how long the signal stays ON and OFF. But it’s not always possible to get any values we want with the basic 555 timer setup.

The 555 Timer Has Its Limits In some cases (like when OFF time needs to be longer than ON), the normal 555 astable circuit can’t give us the result directly. That’s why in Case 3, we had to flip the signal using an inverter.

Inverters Can Help Us Get the Waveform We Want By adding a simple NOT gate (built using a transistor), we were able to reverse the timing — this gave us more flexibility in generating the waveform we needed.

Very Short Pulses Need Precise Components In Case 2, we worked with very fast pulses (just fractions of a millisecond). To do that, we needed low resistor and capacitor values — which also showed us the importance of accuracy and how component selection affects timing.


We Can Detect Edges Using a Differentiator A differentiator circuit helped us catch the exact moment the signal goes from LOW to HIGH. This is useful when we only want to react to changes, not the full pulse.

Monostable 555 Gives Clean, Consistent Pulses Finally, when we triggered a monostable 555 with those edges, we got clean, uniform pulses every time. This is super helpful when we need a reliable output regardless of input width.

