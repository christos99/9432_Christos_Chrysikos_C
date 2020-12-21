# 9432_Christos_Chrysikos_C


## Part 1:

### 1.
[Output of Xeon](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/Xeon.txt)

#### Dynamic Power (Power Modeling):  
Circuits dissipate dynamic power when they charge and discharge the capacitive loads to switch states. Dynamic power is proportional to the total load capacitance, the supply voltage, the voltage swing during switching, the clock frequency, and the activity factor. Dynamic Power does  seem to be affected by the program that we run but not as much as of changing system paramateters.

[Reference](https://www.hpl.hp.com/research/mcpat/McPATAlpha_TechRep.pdf)

#### Leakage (Power Modeling):

Transistors in circuits leak, dissipating static power. Leakage current depends on the width of the transistors and the local state of the devices. There are two leakage mechanisms. Subthreshold leakage occurs because a small current passes between the source and drain of off-state transistors. Gate leakage is the current leaking through the gate terminal, and varies greatly with the state of the device. Leakage is not affected by the executable but from the characteristics of the system,same for all applications.

[Reference](https://www.hpl.hp.com/research/mcpat/McPATAlpha_TechRep.pdf)



### 2.

In order to have longer battery life we need to know which processor consumes less energy, not power(Watts). Therefore we need the dynamic power the leakage and the simulation time. These are data that are extracted both from McPAT and from gem5. 


### 3.  
The power that each proccessor consumes is a combination of dyanmic and static (leakage) power. We now that after the finalization of the program the system still runs and therefore we need to compare the static power of those 2 cpu's to find whick one is more efficient. Extracting from bibliography ARM have significantly smaller static power consumtion than x86 cpu's.

Let's assume that Xeon takes 10 seconds to run a program. Being 40 times faster than ARM, ARM A9 needs 40 seconds to run the same program.

**Runtime Dynamic** 

  * Xeon == 72.9199 W  
    EDP == (72.9199 + GL) x 10 == 729.199 + 10GL mJ
  * ARM A9  == 2.96053 W  
    EDP == (2.96053 + GL) x 40 == 118.4212 + 40GL mJ
    
 It is obvious that even though the ARM A9 runs for a longer period of time, it is much more energy efficient than the Xeon proccessor. In order for the Xeon proccessor to be as energy efficient as ARM it would need to run 245.5 times faster than ARM.
  
     
* [Output of Xeon](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/Xeon.txt)  
* [Output of ARM](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/ARM.txt)


## Part 2:


### 1.
Energy Consumed for all the different occasions.

#### L1 Cache

* 64kB :
  * specbzip:304.612318 mJ
  * spechmmer:230.257257 mJ
  * specjeng:1225.410820 mJ
  * speclibm:469.125388 mJ
  * specmcf:214.602407 mJ
* 128kB :
  * specbzip:404.934228 mJ
  * spechmmer:310.009355 mJ
  * specjeng:1660.129841 mJ
  * speclibm:634.297256 mJ
  * specmcf:289.067039 mJ
* 256kB :
  * specbzip:478.687097 mJ
  * spechmmer:487.544624 mJ
  * specjeng:1995.164951 mJ
  * speclibm:449.788309 mJ
  * specmcf:347.131705 mJ


#### L1 Cache Assoc

* 6
  * specbzip:239.703350 mJ
  * spechmmer:182.315531 mJ
  * specjeng:940.009153 mJ
  * speclibm:362.957233 mJ
  * specmcf:184.659352 mJ
* 8
  * specbzip:239.703350 mJ
  * spechmmer:182.315531 mJ
  * specjeng:940.009153 mJ
  * speclibm:362.957233 mJ
  * specmcf:184.659352 mJ
* 10
  * specbzip:239.703mJ
  * spechmmer:182.315mJ
  * specjeng:940.009153 mJ
  * speclibm:362.957233 mJ
  * specmcf:184.659352 mJ
* 12
  * specbzip:239.703350 mJ
  * spechmmer:182.315531 mJ
  * specjeng:940.009153 mJ
  * speclibm:362.957233 mJ
  * specmcf:184.659352 mJ

#### L2 Cache

* 512kB
  * specbzip:243.260147 mJ
  * spechmmer:181.772249 mJ
  * specjeng:932.459064 mJ
  * speclibm:360.837240 mJ
  * specmcf:183.856990 mJ
* 1024kB
  * specbzip:240.673442 mJ
  * spechmmer:181.995179 mJ
  * specjeng:935.426950 mJ
  * speclibm:361.694166 mJ
  * specmcf:184.121653 mJ
* 2048kB
  * specbzip:239.703350 mJ
  * spechmmer:182.315531 mJ
  * specjeng:940.009153 mJ
  * speclibm:362.957233 mJ
  * specmcf:184.659352 mJ
* 4096kB
  * specbzip:239.557962 mJ
  * spechmmer:182.978396 mJ
  * specjeng:946.424763 mJ
  * speclibm:364.911324 mJ
  * specmcf:185.915461 mJ


#### L2 Cache Assoc

* 4
  * specbzip:239.703350 mJ
  * spechmmer:182.315531 mJ
  * specjeng:940.009153 mJ
  * speclibm:362.957233 mJ
  * specmcf:184.659352 mJ
* 8
  * specbzip:239.703350 mJ
  * spechmmer:182.315531 mJ
  * specjeng:940.009153 mJ
  * speclibm:362.957233 mJ
  * specmcf:184.659352 mJ
* 16
  * specbzip:239.703350 mJ
  * spechmmer:182.315531 mJ
  * specjeng:940.009153 mJ
  * speclibm:362.957233 mJ
  * specmcf:184.659352 mJ
* 32
  * specbzip:239.703350 mJ
  * spechmmer:182.315531 mJ
  * specjeng:940.009153 mJ
  * speclibm:362.957233 mJ
  * specmcf:184.659352 mJ
 
* [Energy Results Files-specbzip](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/specbzip) 
* [Energy Results Files-spechmmer](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/spechmmer)
* [Energy Results Files-specjeng](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/specjeng) 
* [Energy Results Files-speclibm](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/speclibm)
* [Energy Results Files-specbmcf](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/specmcf) 


### 2.

### GRAPHS

* specbzip

![specbzip](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specbzip.png)

* spechmmer

![spechmmer](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/spechmmer.png)

* specjeng

![specjeng](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specjeng.png)

* speclibm

![specjeng](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/speclibm.png)

* specmcf

![specmcf](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specmcf.png)



Ωραία εργασία, το αντικείμενο που ασχολήθηκαμε είναι αρκετά επίκαιρο και ενδιαφέρον.
Παρατηρήσεις:
* Δεν ηταν ευκόλη η κατανόηση των εξόδων από τον McPAT στην αρχη.
* Δεν διευκρινίζεται πουθένα στην βιβλιογραφία τι είναι ακριβώς το EDP και EDAP.
* Στην άρχη είχα θέμα με το να τρέξω τον McPAT έπρεπε να βάλω εξτρα python2 από μπρόστα για να τρέξει.
* Οι πρώτες θεωρητικές ερωτήσεις αδύνατον να απαντηθούν με σιγουριά στην φάση που ζητούνται. Ισως στο τελος θα ηταν πιο απλό (αφού δηλαδή έχουν γίνει οι προσωμοιώσεις)


