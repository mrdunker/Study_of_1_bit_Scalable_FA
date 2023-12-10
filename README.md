# Study_of_1_bit_Scalable_FA

## INTRODUCTION

The rapid advancement of transistor scaling has led to a significant surge in research efforts concerning the low-power design of micro-electronic circuits. The need for high performance microelectronic circuit design has consequently increased dramatically.<br />

Large-scale arithmetic operations are necessary for many modern applications, including digital signal processing (DSP) chips, microprocessors, and image and video processing operations.<br />

This paper proposes a new hybrid FA that makes use of static CMOS logic, PTs, and TGs. Using Cadence tools, the FA was implemented in 45 nm technology. A  thorough analysis of the performance parameters of the proposed design have supply voltages ranging from 0.4 V to 1.2 V was done to assess the reliability.<br />

In addition, the FA has been extended to include wide word length adders to evaluate their performance characteristics in extensive circuits.

## DESIGN – FULL ADDER APPROACH

The model put forward has divided the architecture into four modules for generating the sum and carry bits. Two modules are allocated for sum and two for carry generation.<br />

Truth table for FA:

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/285464cf-ab00-4381-ad13-672cf4983299)


Carry Generation:
<br />
The Truth Table of a Full Adder reveals that when the input carry (Cin) is 0, the carry-out (Cout) is generated as an AND function of the input bits (A and B). Conversely, when Cin is 1, the Cout is generated as an OR function of A and B. <br />
The proposed carry generation part involves a novel AND-OR module (referred to as Module 1) based on Transmission Gate (TG) and Complementary Pass Transistor Logic (CPL).<br />

AND-OR Module Implementation:<br />

The AND-OR module is designed to efficiently implement both AND and OR gates. The implementation of these gates is quite similar, with the key distinction being the interchange of nMOS and pMOS transistors.<br />

Conditions for AND Gate Design:<br />
For the AND gate, the conditions for its design are explained:<br />
<br />
If A is 0, then the output is 0 (achieved by a pass transistor N2).<br />
If A is 1, then the output is B (achieved by TG1).<br />
Conditions for OR Gate Design:<br />
Similarly, for the OR gate, the conditions for its design are outlined:<br />
<br />
If A is 1, then the output is 1 (achieved by a pass transistor P2).<br />
If A is 0, then the output is B (achieved by TG2).<br />

Two-to-One Multiplexer (2:1 MUX):<br />

A Transmission Gate based 2:1 Multiplexer (Module 2) is introduced, comprising TG3 and TG4. This MUX is employed to select the appropriate carry-out signal from the AND-OR module based on the input carry Cin.<br />

Sum Generation: <br />
This report elucidates the design and integration of XOR gates within a novel Full Adder (FA) architecture, emphasizing the cascading of two XOR modules denoted as Module 3 and Module 4. These XOR gates share a consistent structure and are realized through the utilization of Transmission Gates (TGs) and Pass Transistors (PTs). The specific design conditions for each XOR module are detailed, outlining the logic operations based on input conditions. The proposed FA employs Module 3 and Module 4 to generate the sum output, enhancing the overall functionality and efficiency of the adder circuit.<br />

Design Details:<br />
XOR Gate Design for Module 3:<br />
Conditions:<br />
            1. If A is 0, then the output is B.                                   
            2. If A is 1 and B is 0, then the output is A.
            3. If A is 1 and B is 1, then the output is the complement of A (Ā).
<br />
Implementation:<br />
            ▪ TG 5 is employed for condition (1).
            ▪ Pass transistor P3 in Module 3 realizes condition (2).
            ▪ Pass transistor N3 in Module 3 implements condition (3).
<br />
XOR Gate Design for Module 4:<br />
Conditions:<br />
            4. If C in is 0, then the output is A⊕B.
            5. If C in is 1 and A⊕B is 0, then the output is C in.
            6. If C in is 1 and A⊕B is 1, then the output is also C in.
<br />
Implementation:<br />
 TG 6, P4, and N4 are utilized to implement conditions (4), (5), and (6) respectively.
These meticulously designed XOR gates contribute to the sum output generation in the proposed FA, showcasing a strategic combination of TGs and PTs to execute specific logic conditions efficiently.


![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/57aed781-b927-4797-8c76-cd2b01264800)
<br /> (Block diagram for proposed design)<br />


![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/8e8a4f48-e39e-4cb6-8a73-ffb665f47841)


## Simulations and Discussions

The proposed schematic is conceptualized using Cadence Virtuoso. The technology node used for the design put forward is 45nm and the model file integrated is GPDK45, that is 45nm tech node from Global Foundries. The input signals are provided at a frequency of 100MHz each. The overall delay, power, and power delay product (PDP) are determined. A capacitive load of 6fF (FO-4) is used. The capacitive load is introduced to generate results with significant realistic distortions.<br />
The parameters used for references and setting the benchmark are the propagation delay, dynamic power and Power delay product. Propagation delay in the context of a full adder refers to the time it takes for a change in input to produce a corresponding change in the output. It is a measure of how quickly signals propagate through the adder circuit.<br />
In a full adder, there are three key signals: the input bits (A, B, Cin), the sum (S), and the carry-out (Cout). The propagation delay is typically measured from a change in the input (such as a transition from 0 to 1 or vice versa) to when the corresponding change is observed at the output.<br />
For each stage of the full adder, the propagation delay depends on the logical operations and circuit elements involved in generating the sum and carry-out.<br />
Dynamic power in the context of a full adder refers to the power consumed by the circuit due to the charging and discharging of capacitive loads during the switching of digital signals. In digital circuits, including a full adder, dynamic power consumption is a significant aspect of energy usage and is influenced by factors such as the frequency of operation and the number of transitions between logic states.
The Power-Delay Product (PDP) is a metric used to evaluate the energy efficiency of a digital circuit, and it is particularly relevant when considering the trade-off between power consumption and speed. PDP considers both dynamic power consumption and propagation delay, providing a comprehensive measure of a digital circuit's efficiency.<br />

<br /><br />
The formula for the Power-Delay Product (PDP) is given by:
<br />
```PDP = Pdyn ⋅τ```
<br />Where:
<br />

    • Pdyn  is the dynamic power consumption of the circuit.
    • τ is the propagation delay of the circuit.

The schematic design for 1bit FA is shown below.<br />

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/c96ab2ae-0bb4-4bb8-b5fb-f998c51d2e0f)

The schematic is made as a unit block; thus, it allows easy scalable design for multiple bits FA. Parametric analysis was implemented to determine the sizes for the transistors, focusing upon the delay and power consumed. For GPDK45 the minimal length for the transistors is fixed at 45nm and smallest feasible width is 120nm and largest value is 1000nm. The optimal sizes are determined, and the said sizes are used to scale the FA design from 1bit to 64bits.<br /> 
The maximum allowed VDD for 45nm tech is 1.2V. The study starts to test the proposed FA design at different VDD values and infer from the delay and power consumed. <br />

## Analysis with VDD variations

The study goes over the supply voltage VDD and the inputs for the adder, which are A, B and Cin. As mentioned above the signals are set at 100MHz. The analysis is done for single bit adder. The schematic diagram for 1bit FA is shown.<br />

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/3cb44c67-b684-4cd4-87d3-15521dc9ad6e)


The transient analysis is performed from 1.2V to 0.4V; the delay and dynamic power are noted, and PDP is calculated. The observations are summarized in the table below.<br />

![Screenshot from 2023-12-10 21-17-35](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/0d54cdca-778e-44ba-8457-e659ea444a6d)

<br />
Upon the simulations, it is observed that till VDD of 0.5V, strong 1 and strong 0 are derived for sum and carry of the full adder. It can also be seen there is a steep rise in the propagation delay for the outputs. <br />
The expected power performance is verified, as the VDD is reduced the overall power consumption is reduced. The propagation delay has the inverse effect; that is, with the decrease in the VDD, the overall delay sees rise. To have a better performance comparison, PDP is used. It is observed that when VDD is decreased below 0.8V, the delay increases abruptly. A similar change can been in the PDP, the PDP is almost constant till 0.8V, below which, the PDP increase is exponential.<br />

For 1-BIT FA:
![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/2f4f26d9-ce59-40f6-a1ed-912eb5e73c84)

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/73f0a076-fe30-479d-8b2b-ea75e1a99be8)

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/46c44325-47fe-490f-9140-4ea524c267bb)
<br />

Thus, the study here onwards has tested the design using 0.8V as VDD and supply voltages for inputs A, B and Cin. The functionality of the proposed FA can be seen under the simulation results shown below. <br />
<br />
Inputs for 1-BIT FA:<br />
![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/900a439e-2b9f-4d33-90b9-1b8481564f24)
Outputs for 1-BIT FA:<br />
![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/2bd6fae4-cdd4-450c-b33f-d7a5529fb235)


## Ripple Carry Adders (RCA)

A ripple carry adder is a digital circuit used to add multiple binary numbers. It is one of the simplest forms of adders and is widely used in digital circuits and microprocessors. A major motivation for the proposed design for the Full Adder is to scale the adder to multiple bits without intermediate buffers or amplifiers to maintain the signal integrity. The reduction of these components leads to the reduction of overall power reduction. The study proceeds to analyze the performance of the design with multiple bits, namely 4, 8, 16, 32 and 64 bits.<br />

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/db204a54-76b7-475c-bd3c-c9f399b94a97)

Before testing the ripple carry adder for delay and power performance, it must be focused upon the input sequence for the worst possible delay. The worst-case delay will be achieved when the carry Cin gets propagated to Cn as shown in the block diagram for n-bit ripple carry adder. To achieve such a test case, the sequence used in the proposed study is pattern 10101...depending upon the number of bits it it being tested for. The sequence pattern for B is the inverted form of A, that is. 01010.... The input for Cin must go from 0 to 1 for the first unit of the ripple carry adder, when the A0 is going from 0 to 1 and simultaneously B0 goes from 1 to 0.<br /> 
FO-4 is used as the load, i.e., 6fF is integrated for measuring the delay and power performance. The recorded values for the delay and dynamic power; thus calculated PDP for each ripple carry adder. The data collected are depicted using the bar graphs below.<br />
<br />
Delay vs N-Bit FA:<br />
![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/63105ebb-6404-4522-abd0-c0ed497e4b72)
<br />
Dynamic Power vs N-Bit FA:<br />
![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/5ea6bb36-cae7-4317-8f24-860873f175e9)

From the data collected, the study firmly concludes the proposed design can be scaled up to 64 bits, thus, realization of a 64-bit Ripple Carry Adder without the use of intermediate buffers. The delay can be observed to have a linear increasing pattern, alongside the exponentially increasing trend in dynamic power. A similar exponential rising trend can be seen in the PDP.<br />

PDP vs N-bit FA:<br />
![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/ab9ea2cd-3310-47f3-be73-0f39a20d0787)


The schematic for 64bit Ripple Carry Adder:<br />

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/e468f042-708a-4b1e-bbc2-16d5d9d83f27)

<br />
The input and output waveforms are shown below for the 64bit adder:

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/43c26c25-f8cd-4226-b887-ef4aee4416d7)

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/7e1d3a7d-e36d-4b9f-92b9-b1210947e21d)

The observations taken for delay and dynamic power depicts, even though the proposed design consumes a large dynamic power and has a large delay in giving the expected output, yet the design produces a strong 1 and strong 0 as the output for sum and carry bits. One point to be noted, the input given of 100MHz, and the duty cycle is 50%. When scaled up to 64bit ripple carry adder, due to large delay being seen in the output, it is observed, that even though the outputs are maintained, the duty cycle is not 50%, on time for the Carry bit is more, and similarly the off time is more for the Sum bit in the output.<br />

## Analysis with FANOUT variations

he load driving capability is an important aspect for the performance of the proposed design of full adder. The initial testing for delay and dynamic power are done using fanout of 4, that is, it has the driving capability of successfully driving of 4-unit inverters. The FO-4 is taken as 6fF. The study has gone over various FOs from 4 to 64. The table below summaries the various load capacitance taken to realize the various FOs.<br />

![Screenshot from 2023-12-10 21-29-01](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/b6255d45-e17d-4b01-be71-fa45df797141)

<br />
The first set of observations are taken for a VDD of 1.2V documented in the table below.<br />

![Screenshot from 2023-12-10 21-29-19](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/bbe24dc8-cc3f-49ad-a60b-2088ede11d43)
<br />
It is observed, as the output load is increased, the overall delay to also raised, along with dynamic power of the circuit design proposed. Upon referencing the PDP values, there comes a massive spike increase after FO-16. Even with high-power consumption and delay, it is observed that strong 1 and 0 are produced for carry and sum bit outputs. <br />

The benchmark voltage taken for the proposed study is set as 0.8V. The observations for the various fanouts are summarized in the table below. <br />

![Screenshot from 2023-12-10 21-30-36](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/989bbcb2-c806-44b8-b024-356c6d4e9af1)

The variations in the parameters can be visualized in the bar graphs shown below<br />

<br />
Delay Comparison for VDD 0.8 and 1.2 for various FO; 1 BIT FA:<br />

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/1a3ccfd0-e058-465d-87e4-7fa34c9d4995)

Power Comparison for VDD 0.8 and 1.2 for various FO; 1 BIT FA:<br />

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/e962a203-8e8e-4724-839c-ecc8abee1739)


PDP Comparison for VDD 0.8 and 1.2 for various FO; 1 BIT FA:<br />

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/6c1a7283-8cfd-4709-b2a5-13e9492f9080)
<br />

By the comparison between the response of the proposed FA design for 0.8V and 1.2V, it is observed that the PDP values are almost constant for various fanouts, though the is a sharp rise from 32 onwards. It can be drawn from here that for the proposed design fanout up till FO-16 should be favorable, beyond which the power consumption is not suitable.<br />
To determine the favorable fanout for the proposed system conclusively, the study put together the data collected for varying FO for 1bit, 4bit leading up to 32bit FA.<br />

## Delay comparison at various FO for n-bit adder

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/9a283351-308b-4ca3-a75b-7e612638f913)

## Power comparison at various FO for n-bit adder

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/f73cac49-af2c-4140-a473-fd8dd99d382a)

## PDP comparison at various FO for n-bit adder

![image](https://github.com/mrdunker/Study_of_1_bit_Scalable_FA/assets/38190245/b612b8f5-14ba-41dd-9cda-a60e9eefec36)

<br />
The study can conclusively state, FO-16 is a favorable load in regards of the performance, and beyond which the power dissipation and delay in outputs goes above the suitable range

## CONCLUSION

The project presented has gone over the proposed design for a novel hybrid full adder,  and took over to reproduce the results by re-implementing the design proposed. Cadence Virtuoso is used as the platform for designing the schematic and running the simulations and final design of the layout. In relation to arrive to the optimized sizing for the transistors, parametric analysis was performed with delay and PDP as the constraints.<br /><br />
 
Using the same sizes simulation were done and delay, dynamic power and PDP were documented for 1-bit full Adder operating on 1.2V and 0.8V. Further working on 0.8 V, the proposed design was extended the 1-bit FA to 4-bit ,8-bit ,16-bit,32-bit and 64-bit found the delay,power. <br /><br />

We have also observed the effects of change in delay,power and PDP for different ranges of FANOUT ranging from FO-4 to FO-64. The observations made were noted down compared with each other to find out which FO is ideal.<br /><br />

It has been found out that if we go beyond FO-16 there is a significant increase in the PDP so as so it is not desired.<br />
