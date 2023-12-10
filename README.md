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





