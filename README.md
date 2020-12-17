# 9432_Christos_Chrysikos_C


## Part 1:

### 1.

#### Dynamic Power (Power Modeling):  
Circuits dissipate dynamic power when they charge and discharge the capacitive loads to switch states. Dynamic power is proportional to the total load capacitance, the supply voltage, the voltage swing during switching, the clock frequency, and the activity factor.

[Reference](https://www.hpl.hp.com/research/mcpat/McPATAlpha_TechRep.pdf)

#### Leakage (Power Modeling):

Transistors in circuits leak, dissipating static power. Leakage current depends on the width of the transistors and the local state of the devices. There are two leakage mechanisms. Subthreshold leakage occurs because a small current passes between the source and drain of off-state transistors. Gate leakage is the current leaking through the gate terminal, and varies greatly with the state of the device.

[Reference](https://www.hpl.hp.com/research/mcpat/McPATAlpha_TechRep.pdf)

The dynamic power and the leakage are not affected by the different progrmas runnning or the time but only affected by the physical parameters of the circuit (processor).
