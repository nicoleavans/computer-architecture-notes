CPEN 4700 – Exam 1 Review

# Chapter 1

## 1.2
* History – first design for programmable computer, who designed it, who programmed for it

> The first programmable computer was the Analytical Engine designed by Charles Babbage. Countess Ada of Lovelace conceptualized using punch cards as removeable programs.


* Difference between analog and digital computers

> Analog computers do not perform discrete computations on numbers as digital computers do, but rather operations such as addition, subtraction, integration, and differentiation of analog signals, usually represented by electrical voltages. Analog computers operate on real measured values. 

## Generations of Computing

| Generation | Advancements | 
| ---------- | -------- |
| 1st | The von Neumann architecture's stored-program design enabled software and multipurpose machines to exist. Vaccuum tubes were a critical implementation technology, but they were unreliable, with low MTBF (mean time between failures). This meant the computer could only run for so long without stopping to replace tubes.  |
| 2nd | Transistors replaced vaccuum tubes, making computers more reliable. Magnetic core memory led to multiprogramming (having more than one program resident in memory at the same time). Programming languages such as Fortran, Algol, and COBOL were developed, making programming more accessible and efficient. | 
| 3rd | Integrated circuits replaced discrete transistors, allowing for smaller, cheaper, and faster computers: minicomputers. The existence of minicomputers made computing more accessible. The large machines of generations past began to be replaced by supercomputers, with extraordinary scientific computing ability.  | 
| 4th | Beginning in this generation, a CPU could be fabricated on a single chip - a microprocessor. This led to the microcomputer - a personal computer. IBM released their PC with an open architecture, allowing competitors to create compatible clones. This drove prices down and computers were more accessible than ever. Office software influenced the increasing acceptance and adoption of computers. | 
| 5th | During this generation, networking became pervasive, as users wished to connect devices to other devices - be it through LANs, WANs, the internet or other means. VLSI and ULSI empowered CPUs as they became increasingly internally parallel. Parallelism using multiple processors became more common even in business and personal machines. Even supercomputers increasingly made use of standard microprocessor chips.  | 
| 6th | With processors commonly containing billions of transistors, it was possible to add more computing cores, essentially creating single chip multiprocessor systems. 64-bit versions of processors and operating systems became necesssary due to the increase in main memory sizes in all sorts of systems. Wireless connectivity through Wi-Fi and cellular networks enabled mobile computers such as tablets and smartphones to gain popularity and use. Cloud computing utilized wireless connectivity to allow remote computing systems to provide local devices with computational services or data storage. |

* SoC 
  
> System on a chip. The Apple M1 chip has all computational hardware on one chip, reducing latency and increasing efficiency.

## 1.3
* Three main subsystems of a computer

> 1. CPU
> 2. Memory
> 3. I/O

* bus

> allows transfer of data between hardware, such as between the CPU and memory.

* The instruction execution cycle

>get instruction -> decode instruction -> create operand addresses -> get operands -> do operation -> store results ->

* von Neumann/Princeton vs Aiken/Harvard and the bottleneck

## 1.4
* Describe the different quality factors. Generality, ease of use, expandability, compatibility, and reliability

## 1.5
* Original IBM PC CPU selection battle
* Open vs proprietary arch.
* Types of costs – monetary, power, volume/mass

## 1.6
* **Calculate** frequency and cycle time (given the other)
* **Calculate** peak MIPS given CPI and frequency
* **Calculate** average cycles per instruction (CPI)
* **Calculate** FLOPS given CPI and frequency
* Memory access time vs. cycle time
* **Calculate** memory bandwidth given cycle time and bus size
* Describe overclocking and underclocking
* Describe benchmarking
* Benchmark used for TOP500
* Benchmark often used for MIPS
* SPEC benchmarks

# Chapter 2

## 2.1
* Ideal characteristics of memory
* Inherent tradeoffs in memory 
* Three main types of memory by technology used
* Properties, advantages, and disadvantages of various types
* Semiconductor: DRAM, SRAM, flash
* Magnetic: hard disk, tape
* Optical: CD-ROM, DVD
* MRAM – what is it and why is it different/better
* Construct a memory hierarchy
* CPU-memory gap problem

## 2.2 and 2.3
* Describe three types of memory organization and give an example of each
* RAM
* High order interleaving advantages and disadvantages
* Low order interleaving advantages and disadvantages – when does it perform well vs poorly
* **Calculate** max theoretical speed increase from low order interleaving
* SAM
* Relative addressing
* CAM
* Argument, mask, and match registers

## 2.4
* Describe cache and why it’s used
* L1 vs L2 vs L3
* Describe locality of reference, why programs exhibit it, and know the three types
* Describe and calculate hit and miss ratios
* Describe the three types of cache misses
* **Calculate** effective average memory access time
* Describe a refill line
* Fully associative vs. n-way set associative vs direct mapping (describe and advantages/disadvantages)
* Given a main memory size, cache size, line size, and associativity, **calculate** number of cache lines, as 
well as tag, index, and byte of an address
* Advantage of having separate instruction and data cache
* Write through vs. write back policies (describe, and advantages/disadvantages)
* Dirty bit
* Cache replacement policies – LRU, LFU, FIFO, and random (describe)
* Valid bit
* Prefetching

## 2.5
* Virtual memory
* Logical address vs. physical address
* MMU
* Page table base register
* Paging vs segmented virtual memory
* Multiple level page tables
* Page fault
* Thrashing
* TLB
* Compare and contrast cache and virtual memory
* Physical vs. virtual addressed cache -  four different implementations
* Aliasing