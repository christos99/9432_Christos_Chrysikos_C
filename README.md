# 9432_Christos_Chrysikos_C


## <ins>Part 1: Getting to know McPAT</ins>


### 1.
[Output of Xeon](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/Xeon.txt)

#### Dynamic Power :
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

We see that spechmmer has slighly greater dynamic power value than specbzip. Runtime does not affect the dynamic or static power but the energy consumtion of the system.



[Reference](https://www.hpl.hp.com/research/mcpat/McPATAlpha_TechRep.pdf)

#### Leakage :

Transistors in circuits leak, dissipating static power. Leakage current depends on the width of the transistors and the local state of the devices. There are two leakage mechanisms. Subthreshold leakage occurs because a small current passes between the source and drain of off-state transistors. Gate leakage is the current leaking through the gate terminal, and varies greatly with the state of the device. Leakage is not affected by the executable but from the characteristics of the system,same for all applications.

[Reference](https://www.hpl.hp.com/research/mcpat/McPATAlpha_TechRep.pdf)



### 2.

The proccessor with th 40 W is propably going to be faster and therefore finish an application in less time than thee 4W, which means that the system is going to require less energy. For a more accurate answer we whould need to know the leakge power of the proccessor because that is what consumes energy after the application is finshed. The dynamic power ,the leakage and the simulation time are data that are extracted both from McPAT and from gem5 and are vital for a more accurate answer.



### 3.  
The power that each proccessor consumes is a combination of dyanmic and static (leakage) power. We now that after the finalization of the program the system still runs and therefore we need to compare the static power of those 2 cpu's to find whick one is more efficient. Extracting from bibliography ARM have significantly smaller static power consumtion than x86 cpu's.

Let's assume that Xeon takes 10 seconds to run a program. Being 40 times faster than ARM, ARM A9 needs 40 seconds to run the same program.

**Runtime Dynamic** 

  * Xeon == 72.9199 W  
    EDP == (72.9199 + 36.8319) x 1 == 134.938 mJ
  * ARM A9  == 2.96053 W  
    EDP == (2.96053 + 0.108687) x 40 == 122.7652 mJ
    
 It is obvious that even though the ARM A9 runs for a longer period of time, but still is more energy efficient than the Xeon proccessor.
  
     
* [Output of Xeon](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/Xeon.txt)  
* [Output of ARM](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Output%20Files/ARM.txt)



## <ins>Part 2: gem5 and McPAT</ins>


### 1.
Here are in categories the parameter changed in every simulation (ex. default_configuration_of_gem5_L1_Cache_64kB). The ending of the name shows the changed parameter.

#### L1 Cache

* 64kB :
  * specbzip: 
    * Energy = 304.612318 mJ
    * Peak Power(Core + L2)  = 3.079 W
  * spechmmer:
    * Energy = 230.257257 mJ
    * Peak Power(Core + L2)  = 3.079 W
  * specjeng:
    * Energy = 1225.410820 mJ
    * Peak Power(Core + L2)  = 3.089 W
  * speclibm:
    * Energy = 469.125388 mJ
    * Peak Power(Core + L2)  = 3.088 W
  * specmcf:
    * Energy = 214.602407 mJ
    * Peak Power(Core + L2) = 3.088 W
* 128kB :
  * specbzip:
    * Energy = 404.934228 mJ
    * Peak Power(Core + L2) = 3.545 W
  * spechmmer:
    * Energy = 310.009355 mJ
    * Peak Power(Core + L2) = 3.545 W
  * specjeng:
    * Energy = 1660.129841 mJ
    * Peak Power(Core + L2) = 3.545 W
  * speclibm:
    * Energy = 634.297256 mJ
    * Peak Power(Core + L2) = 3.545 W
  * specmcf:
    * Energy = 289.067039 mJ
    * Peak Power(Core + L2) = 3.545 W
  
* 256kB :
  * specbzip:
    * Energy = 478.687097 mJ
    * Peak Power(Core + L2) = 3.86 W
  * spechmmer:
    * Energy = 487.544624 mJ
    * Peak Power(Core + L2) = 3.86 W
  * specjeng:
    * Energy = 1995.164951 mJ
    * Peak Power(Core + L2) = 3.87 W
  * speclibm:
    * Energy = 449.788309 mJ
    * Peak Power(Core + L2) = 3.86 W
  * specmcf:
    * Energy = 347.131705 mJ
    * Peak Power(Core + L2) = 3.86 W

    

#### L1 Cache Assoc

* 6
  * specbzip:
    * Energy = 239.703350 mJ
    * Peak Power(Core + L2) = 2.48 W
  * spechmmer:
    * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 2.48 W
  * specjeng:
    * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 2.48 W
  * speclibm:
    * Energy = 362.957233 mJ
    * Peak Power(Core + L2) = 2.485 W 
  * specmcf:
    * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W 
* 8
  * specbzip:
      * Energy = 239.703350 mJ
    * Peak Power(Core + L2) = 2.48 W
  * spechmmer:
      * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 2.48 W
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 2.48 W
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) = 2.485 W 
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W 
* 10
  * specbzip:
      * Energy = 239.703mJ
    * Peak Power(Core + L2) = 2.48 W
  * spechmmer:
      * Energy = 182.315mJ
    * Peak Power(Core + L2) = 2.48 W
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 2.48 W
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) = 2.485 W
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W
* 12
  * specbzip:
      * Energy = 239.703350 mJ 
    * Peak Power(Core + L2) = 2.48 W
  * spechmmer:
      * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 2.48 W
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 2.48 W
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) =  2.485 W
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W

#### L2 Cache

* 512kB
  * specbzip:
      * Energy = 2243.260147 mJ
    * Peak Power(Core + L2) = 2.315 W
  * spechmmer:
      * Energy = 181.772249 mJ
    * Peak Power(Core + L2) = 2.31  W
  * specjeng:
      * Energy = 932.459064 mJ
    * Peak Power(Core + L2) = 2.31 W
  * speclibm:
      * Energy = 360.837240 mJ 
    * Peak Power(Core + L2) = 2.315 W
  * specmcf:
      * Energy = 183.856990 mJ
    * Peak Power(Core + L2) = 2.315 W
* 1024kB
  * specbzip:
      * Energy = 240.673442 mJ
    * Peak Power(Core + L2) = 2.39 W
  * spechmmer:
      * Energy = 181.995179 mJ
    * Peak Power(Core + L2) = 2.38 W
  * specjeng:
      * Energy = 935.426950 mJ 
    * Peak Power(Core + L2) = 2.38 W
  * speclibm:
      * Energy = 361.694166 mJ
    * Peak Power(Core + L2) = 2.385 W
  * specmcf:
      * Energy = 184.121653 mJ
    * Peak Power(Core + L2) = 2.385 W
* 2048kB
  * specbzip:
      * Energy = 239.703350 mJ
    * Peak Power(Core + L2) = 2.48 W
  * spechmmer:
      * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 2.48 W
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 2.48 W
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) = 2.485 W 
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W
* 4096kB
  * specbzip:
      * Energy = 239.557962 mJ
    * Peak Power(Core + L2) = 2.61 W
  * spechmmer:
      * Energy = 182.978396 mJ
    * Peak Power(Core + L2) = 2.61 W
  * specjeng:
      * Energy = 946.424763 mJ
    * Peak Power(Core + L2) = 2.61 W 
  * speclibm:
      * Energy = 364.911324 mJ
    * Peak Power(Core + L2) = 2.615 W 
  * specmcf:
      * Energy = 185.915461 mJ
    * Peak Power(Core + L2) = 2.615 W


#### L2 Cache Assoc


* 4
  * specbzip:
      * Energy = 239.703350 mJ 
    * Peak Power(Core + L2) = 2.48 W
  * spechmmer:
      * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 2.48 W
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 2.48 W
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) =  2.485 W
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W
* 8
  * specbzip:
      * Energy = 239.703350 mJ 
    * Peak Power(Core + L2) = 2.48 W
  * spechmmer:
      * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 2.48 W
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 2.48 W
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) =  2.485 W
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W
* 16
  * specbzip:
      * Energy = 239.703350 mJ 
    * Peak Power(Core + L2) = 2.48 W
  * spechmmer:
      * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 2.48 W
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 2.48 W
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) =  2.485 W
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W
* 32
  * specbzip:
      * Energy = 239.703350 mJ 
    * Peak Power(Core + L2) = 2.48 W
  * spechmmer:
      * Energy = 182.315531 mJ
    * Peak Power(Core + L2) = 2.48 W
  * specjeng:
      * Energy = 940.009153 mJ
    * Peak Power(Core + L2) = 2.48 W
  * speclibm:
      * Energy = 362.957233 mJ
    * Peak Power(Core + L2) =  2.485 W
  * specmcf:
      * Energy = 184.659352 mJ
    * Peak Power(Core + L2) = 2.485 W
 
* [Energy Results Files-specbzip](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/specbzip) 
* [Energy Results Files-spechmmer](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/spechmmer)
* [Energy Results Files-specjeng](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/specjeng) 
* [Energy Results Files-speclibm](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/speclibm)
* [Energy Results Files-specbmcf](https://github.com/christos99/9432_Christos_Chrysikos_C/tree/main/Energy%20results/specmcf) 


### 2.

### GRAPHS

### EDP

* specbzip - EDP

![specbzip](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specbzip.png)

* spechmmer - EDP

![spechmmer](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/spechmmer.png)

* specjeng - EDP

![specjeng](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specjeng.png)

* speclibm - EDP

![speclibm](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/speclibm.png)

* specmcf - EDP

![specmcf](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specmcf.png)

### PeaK Power

* specbzip - Peak Power

![specbzip](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specbzip_Peak_Power.png)

* spechmmer - Peak Power

![spechmmer](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/spechmmer_Peak_Power.png)

* specjeng - Peak Power

![specjeng](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specjeng_Peak_Power.png)

* speclibm - Peak Power

![speclibm](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/speclibm_Peak_Power.png)

* specmcf - Peak Power

![specmcf](https://github.com/christos99/9432_Christos_Chrysikos_C/blob/main/Graphs/specmcf_Peak_Power.png)

## <ins>Conclussion</ins>

We can see from the above graphs that peak power is strictly correlated with L1 Cache size, the bigger the cache the greater the peak power. We assume that every relut we got can differ in some percentage from the reality. This occurs cause McPAT is a simulator just like gem5 and simulates the reults based on algorithms.






Ωραία εργασία, το αντικείμενο που ασχολήθηκαμε είναι αρκετά επίκαιρο και ενδιαφέρον.
Παρατηρήσεις:
* Δεν ηταν ευκόλη η κατανόηση των εξόδων από τον McPAT στην αρχη.
* Δεν διευκρινίζεται πουθένα στην βιβλιογραφία τι είναι ακριβώς το EDP και EDAP.
* Στην άρχη είχα θέμα με το να τρέξω τον McPAT έπρεπε να βάλω εξτρα python2 από μπρόστα για να τρέξει.
* Οι πρώτες θεωρητικές ερωτήσεις αδύνατον να απαντηθούν με σιγουριά στην φάση που ζητούνται. Ισως στο τελος θα ηταν πιο απλό (αφού δηλαδή έχουν γίνει οι προσωμοιώσεις)


