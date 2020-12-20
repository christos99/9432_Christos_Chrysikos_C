# 9432_Christos_Chrysikos_C


## Part 1:

### 1.
[Output of Xeon](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/Xeon.txt)

#### Dynamic Power (Power Modeling):  
Circuits dissipate dynamic power when they charge and discharge the capacitive loads to switch states. Dynamic power is proportional to the total load capacitance, the supply voltage, the voltage swing during switching, the clock frequency, and the activity factor.

[Reference](https://www.hpl.hp.com/research/mcpat/McPATAlpha_TechRep.pdf)

#### Leakage (Power Modeling):

Transistors in circuits leak, dissipating static power. Leakage current depends on the width of the transistors and the local state of the devices. There are two leakage mechanisms. Subthreshold leakage occurs because a small current passes between the source and drain of off-state transistors. Gate leakage is the current leaking through the gate terminal, and varies greatly with the state of the device.

[Reference](https://www.hpl.hp.com/research/mcpat/McPATAlpha_TechRep.pdf)

The dynamic power and the leakage are not affected by the different progrmas runnning or the time but only affected by the physical parameters of the circuit (processor).

## Part 2:


## Part 3:
Let's assume that Xeon takes 10 seconds to run a program. Being 40 times faster than ARM, ARM A9 needs 40 seconds to run the same program.

**Runtime Dynamic** 

  * Xeon == 72.9199 W  
    EDP == 72.9199 * 10 == 729.199
  * ARM A9  == 2.96053 W  
    EDP == 2.96053 * 40 == 118.4212
    
 It is obvious that even though the ARM A9 runs for a longer period of time, it is much more energy efficient than the Xeon proccessor. In order for the Xeon proccessor to be as energy efficient as ARM it would need to run 245.5 times faster than ARM.
  
     
* [Output of Xeon](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/Xeon.txt)  
* [Output of ARM](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/ARM.txt)


