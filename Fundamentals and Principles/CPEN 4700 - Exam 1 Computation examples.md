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
1.25 \ \mathrm{GHz} = 1250 \ \mathrm{MHz} = 1250 \frac{\mathrm{cycles}}{\mathrm{second}}
$$

$$
\frac{1250 \ \mathrm{M}\frac{\mathrm{cycles}}{\mathrm{second}}}{2.6 \frac{\mathrm{cycles}}{\mathrm{instruction}}} \approx 480.7692308 \ \mathrm{M} \frac{\mathrm{instructions}}{\mathrm{second}} = 480.7692308 \ \mathrm{MIPS}
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
\mathrm{bandwidth} = \frac{\mathrm{bytes}}{\mathrm{seconds}}
$$

$$
\frac{32 \ \mathrm{bit}}{7 \ \mathrm{ns}} = \frac{4 \ \mathrm{bytes}}{7 \ \mathrm{ns}} = \frac{4}{7} \ \mathrm{Bps} \approx .5714 \ \mathrm{Bps}
$$

# How do we do this with frequency?

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