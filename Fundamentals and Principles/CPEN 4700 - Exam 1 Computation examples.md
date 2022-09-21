CPEN 4700 - Exam 1 Computation examples
1. Calculate frequency and cycle time (given the other)
   
> A processor operates at 3.5 GHz. What is the cycle time?

$$
\mathrm{frequency} = \frac{1}{t_c}
$$

$$
3.5 \ \mathrm{GHz} = 3.5 \times 10^9 \frac{\mathrm{cycles}}{\mathrm{second}}
$$

$$
\frac{1}{3.5 \times 10^9} \approx 2.85714286 \times 10^{-10} = .285714286 \times 10^{-9} = .285714286 \ \mathrm{ns}
$$

2. Calculate peak MIPS given CPI and frequency

> A processor operates 1.25 GHz and has a maximum CPI of 0.8. What is the peak MIPS?

$$
\mathrm{MIPS} = \frac{\mathrm{frequency}}{\mathrm{CPI}}
$$

$$
1.25 \ \mathrm{GHz} = 1250 \ \mathrm{MHz} = 1250 \times 10^6 \frac{\mathrm{cycles}}{\mathrm{second}}
$$

$$
\frac{1250 \times 10^6 \frac{\mathrm{cycles}}{\mathrm{second}}}{.8} = 1.5625 \times 10^9 = 1562.5 \ \mathrm{MIPS} 
$$

3. Calculate average cycles per instruction (CPI)
   
> Analyzing a certain program, you find 50% of the instructions take a processor 1 cycle 30% take 2 cycles, and 20% take 4 cycles. What is the average CPI?

$$
.5(1) + .3(2) + .2(4) = .5 + .6 + .8 = 1.9 \ \mathrm{CPI_{average}}
$$

4. Calculate FLOPS given CPI and frequency
   
> A processor has a CPI of 0.6 for floating point instructions and runs at 750 MHz. What is the FLOPS of  this system?

$$
\mathrm{FLOPS} = \frac{\mathrm{frequency}}{\mathrm{\mathrm{CPI}_{\mathrm{floating-point}}}}
$$

$$
\frac{750 \ \mathrm{M} \frac{\mathrm{cycles}}{\mathrm{seconds}}}{.6\frac{\mathrm{cycles}}{\mathrm{floating-point \ instructions}}} = 1250 \ \mathrm{M} \frac{\mathrm{floating-point \ instructions}}{\mathrm{seconds}} = 1250 \ \mathrm{MFLOPS}
$$

$$
1250 \ \mathrm{MFLOPS} = 1,250,000,000 \ \mathrm{FLOPS}
$$

5. Calculate memory bandwidth given cycle time or frequency and bus size
   
> A memory system has a cycle time of 7 ns, and a 32 bit wide bus. What is the memory bandwidth?

$$
\mathrm{bandwidth} = \frac{\mathrm{bytes(width)}}{\mathrm{seconds}}
$$

$$
\frac{32 \ \mathrm{bit}}{7 \ \mathrm{ns}} = \frac{4 \ \mathrm{bytes}}{7 \times 10^{-9} \ \mathrm{s}} = 571428571.4 \frac{\mathrm{bytes}}{\mathrm{s}} = 571.429 \times 10^6 \frac{\mathrm{bytes}}{\mathrm{s}}
$$

$$
571.429 \times 10^6 \frac{\mathrm{bytes}}{\mathrm{s}} = 571.429 \frac{\mathrm{megabytes}}{\mathrm{s}} = 571.429 \ \mathrm{MBs}
$$

> To do this with frequency, calculate cycle time from frequency.

6. Calculate max theoretical speed increase from low order interleaving
   
> A memory technology with a cycle time of 3 ns is designed with 4 way low order interleaving. Assuming the bus is large enough, what is the fastest the effective cycle time can be?

$$
t_c = 3 \ \mathrm{ns}
$$

$$
t_{a \ \mathrm{effective}} = \frac{t_c}{\mathrm{interleave \ factor}}
$$

$$
\frac{3 \ \mathrm{ns}}{4} = .75 \ \mathrm{ns}
$$

7. Calculate hit and miss ratios
   
> A given program runs with 240,000 cache misses and 4,730,000 cache hits. What are the hit and miss ratios?

$$
\mathrm{hit \ ratio} = \frac{\mathrm{number \ of \ hits}}{\mathrm{number \ of \ hits + number \ of \ misses}}
$$

$$
\frac{4,730,000}{240,000+4,730,000} = \frac{4,730,000}{4,970,000} = \frac{4730}{4970} \approx .9517102616
$$

$$
\mathrm{miss \ ratio} = \frac{\mathrm{number \ of \ misses}}{\mathrm{number \ of \ hits + number \ of \ misses}} = 1 - \mathrm{hit \ ratio}
$$

$$
\frac{240,000}{4,970,000} = \frac{240}{4970} \approx .04828973843
$$

$$
\mathrm{hit \ ratio} \approx .9517
$$

$$
\mathrm{miss \ ratio} \approx .0483
$$

8. Calculate effective average memory access time
   
> A system’s cache cycle time is 0.8 ns, and its main memory access time is 5 ns. Using the hit and miss counts from question 7, find the effective memory access time.

$$
t_c = .8 \ \mathrm{ns}
$$

$$
t_{a \ \mathrm{effective}} = \mathrm{hit \ ratio}(t_{a \ \mathrm{cache}}) + \mathrm{miss \ ratio}(t_{a \ \mathrm{main}})
$$

$$
t_{a \ \mathrm{effective}} = .9517(.8 \ \mathrm{ns}) + .0483(5 \ \mathrm{ns}) = .76136 \ \mathrm{ns} + .2415 \ \mathrm{ns} = 1.00286 \ \mathrm{ns}
$$

9. A system with 8 GB of DRAM as a main memory has a 16 MB L3 cache with 8 way interleaving, and 128 byte refill lines. What are the sizes of the tag, index, and bytes fields for this cache? List all three answers. What are these values if the the cache is direct mapped?

$$
8 \ \mathrm{GB} = 2^{3} * 2^{30}- \ \mathrm{bytes} = 2^{33} \ \mathrm{bytes} 
$$

> Thus, a 33 bit address. 

$$
16 \ \mathrm{MB} = 2^4 * 2^{20} = 2^{24} \ \mathrm{bytes \ in \ cache}
$$

$$
128 \ \mathrm{byte \ refill \ line} = 2^7
$$

> Thus, 7 bits required to address the refill line. This is the value for byte regardless of type. 

$$
\frac{2^{24}}{2^7} = 2^{17} \mathrm{lines \ in \ cache}
$$

> In a direct mapped cache, the number of lines determines index, so our index would be 17. The tag for that can be found by subtracting the index and byte bits from the total address length, 33 bits. 

$$
33 - 17 - 7 = 9
$$

> To find the index for the 8 way set associative cache, we need to adjust based on the number of ways:

$$
\frac{2^{17} \ \mathrm{lines \ in \ cache}}{2^3 \ \mathrm{ways}} = 2^{14} \ \mathrm{sets}
$$

> Thus the index for the 8-way set associative cache is 14. The tag can be found by subtracting the index and byte bits from the total address length, 33 bits.

$$
33 - 7 - 14 = 12
$$

| | tag | index | byte |
| - | - | - | - |
| 8-way | 12 | 14 | 7 | 
| direct-mapped | 9 | 17 | 7 | 

10.   An older system has 64 MB of main memory, and the processor has a 16 KB fully associative cache with 32 byte refill lines. How many lines are in the cache? What are the sizes of the tag, index, and byte fields if they exist? How would this change if the cache was 4-way set associative?

$$
64 \ \mathrm{MB} = 2^6 * 2^{20} = 2^{26}
$$

> Thus, 26 bit memory address.

$$
16 \ \mathrm{KB} = 2^{14} \ \mathrm{bytes \ in \ cache}
$$

$$
32 \ \mathrm{byte} = 2^5
$$

> Thus, our byte size is 5 bits. For the fully-associative cache, all that is left to do is subtract that from the total address size to calculate our tag size.

$$
26 - 5 = 21
$$

> For the four-way set associative cache, we need to determine the index by first finding how many lines are in cache:

$$
\frac{2^{14}}{2^5} = 2^9 \ \mathrm{lines \ in \ caches}
$$

> Then we adjust that to account for the 4-ways:

$$
\frac{2^9}{4} = \frac{2^9}{2^2} = 2^7
$$

> Thus we need 7 bits to select the correct cache line, our index value. We then subtract the index and byte bits from the total address size to calculate tag size:

$$
26-5-7 = 14
$$

| | tag | index | byte |
| - | - | - | - |
| fully-associative | 21 |  | 5 | 
| four-way | 14 | 7 | 5 |