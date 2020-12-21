# 9432_Christos_Chrysikos_C


## Part 1:

### 1.
[Output of Xeon](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/Xeon.txt)

#### Dynamic Power (Power Modeling):  
Circuits dissipate dynamic power when they charge and discharge the capacitive loads to switch states. Dynamic power is proportional to the total load capacitance, the supply voltage, the voltage swing during switching, the clock frequency, and the activity factor. Dynamic Power does  seem to be affected by the program that we run but not as much as of changing system paramateters.

Example using the same system running two different benchmarks:

* [specbzip](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Energy%20results/specbzip/L1_128_specbzip-energy.txt) 
  * dynamic power = 0.439631 W  
  * leakage = 2.129390 W 
  * runtime = 0.157622 s 
  
* [spechmmer](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Energy%20results/spechmmer/L1_128_spechmmer-energy.txt)
  * dynamic power = 0.491212 W  
  * leakage = 2.129390 W 
  * runtime = 0.118297 s 

We see that spechmmer has slighly greater dynamic power value than specbzip. It is a fact that both programms run on the same system and the only diffennce is runntime.



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
  * specbzip: 
    * Energy = 304.612318 mJ
    * Peak Power(Core + L2)  = 
  * spechmmer:
    * Energy = 230.257257 mJ
    * Peak Power(Core + L2)  = 
  * specjeng:
    * Energy = 1225.410820 mJ
    * Peak Power(Core + L2)  = 
  * speclibm:
    * Energy = 469.125388 mJ
    * Peak Power(Core + L2)  = 
  * specmcf:
    * Energy = 214.602407 mJ
    * Peak Power(Core + L2) = 3.088 W
* 128kB :
  * specbzip:
    * Energy = 404.934228 mJ
    * Peak Power(Core + L2) = 
  * spechmmer:
    * Energy = 310.009355 mJ
    * Peak Power(Core + L2) = 
  * specjeng:
    * Energy = 1660.129841 mJ
    * Peak Power(Core + L2) = 
  * speclibm:
    * Energy = 634.297256 mJ
    * Peak Power(Core + L2) = 
  * specmcf:
    * Energy = 289.067039 mJ
    * Peak Power(Core + L2) = 3.545 W
  
* 256kB :
  * specbzip:
    * Energy = 478.687097 mJ
    * Peak Power(Core + L2) = 
  * spechmmer:
    * Energy = 487.544624 mJ
    * Peak Power(Core + L2) = 
  * specjeng:
    * Energy = 1995.164951 mJ
    * Peak Power(Core + L2) = 
  * speclibm:
    * Energy = 449.788309 mJ
    * Peak Power(Core + L2) = 
  * specmcf:
    * Energy = 347.131705 mJ
    * Peak Power(Core + L2) = 3.86 W

    

#### L1 Cache Assoc

* 6
  * specbzip:
    * Energy = 239.703350 mJ
    * Peak Power(Core + L2) = 
  
  * spechmmer:
    * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 
  * specjeng:
    * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 
  * speclibm:
    * Energy = 362.957233 mJ
    * Peak Power(Core + L2) = 
  * specmcf:
    * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W 
* 8
  * specbzip:
      * Energy = 239.703350 mJ
    * Peak Power(Core + L2) = 
  * spechmmer:
      * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) = 
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W 
* 10
  * specbzip:
      * Energy = 239.703mJ
    * Peak Power(Core + L2) = 
  * spechmmer:
      * Energy = 182.315mJ
    * Peak Power(Core + L2) = 
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) = 
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W
* 12
  * specbzip:
      * Energy = 239.703350 mJ 
    * Peak Power(Core + L2) = 
  * spechmmer:
      * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) = 
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W

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

* specbzip - EDP

![specbzip](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specbzip.png)

* spechmmer - EDP

![spechmmer](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/spechmmer.png)

* specjeng - EDP

![specjeng](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specjeng.png)

* speclibm - EDP

![specjeng](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/speclibm.png)

* specmcf - EDP

![specmcf](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specmcf.png)


* specbzip - Peak Power

![specbzip]()

* spechmmer - Peak Power
![spechmmer]()

* specjeng - Peak Power

![specjeng]()

* speclibm - Peak Power

![specjeng]()

* specmcf - Peak Power

![specmcf](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specmcf_Peak_Power.png)




Ωραία εργασία, το αντικείμενο που ασχολήθηκαμε είναι αρκετά επίκαιρο και ενδιαφέρον.
Παρατηρήσεις:
* Δεν ηταν ευκόλη η κατανόηση των εξόδων από τον McPAT στην αρχη.
* Δεν διευκρινίζεται πουθένα στην βιβλιογραφία τι είναι ακριβώς το EDP και EDAP.
* Στην άρχη είχα θέμα με το να τρέξω τον McPAT έπρεπε να βάλω εξτρα python2 από μπρόστα για να τρέξει.
* Οι πρώτες θεωρητικές ερωτήσεις αδύνατον να απαντηθούν με σιγουριά στην φάση που ζητούνται. Ισως στο τελος θα ηταν πιο απλό (αφού δηλαδή έχουν γίνει οι προσωμοιώσεις)


