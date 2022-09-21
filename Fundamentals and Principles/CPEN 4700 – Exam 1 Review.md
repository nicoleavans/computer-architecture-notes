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

> Allows transfer of data between hardware, such as between the CPU and memory.

* The instruction execution cycle

> fetch instruction -> decode instruction -> generate operand addresses -> fetch operands -> perform operation -> store results ->

> A pneumonic device is "Fun day gaming first person shooters." 

* von Neumann/Princeton vs Aiken/Harvard and the bottleneck

> The von Neumann or Princeton architecture has a unified main memory to hold instructions and data. the Aiken or Harvard architecture had split program and data memory, which had potential performance benefits.

> The von Neumann bottleneck occurs when computer system throughput is limited by the single path to memory for instructions and data.

## 1.4
* Describe the different quality factors. Generality, ease of use, expandability, compatibility, and reliability

> generality - variety of tasks for which a system is well-suited

> ease of use - ease for systems programmer to write the OS, compiler, linker, etc. 

> expandability - how easy it is to increase the capabilities of an architecture, or to allow for simpler versions

> compatibility - the ability of two different computers to run the same machine language or executable program

> reliability - does the system stay up? high mtbf desirable.

## 1.5
* Original IBM PC CPU selection battle

> Intel 8086 chip was ready, Motorola 68000 chip wasn't. Regardless of which was superior, x86 became standard.

* Open vs proprietary arch.

> Open architecture, like the IBM PC, allows other manufacturers to produce compatible hardware. This may drive down prices. Proprietary architecture, such as the Apple Macintosh, keeps the architectural details secret. 


* Types of costs – monetary, power, volume/mass

> Monetary cost - cost of implementation and maintenance for hardware and software. 

> Power cost - the power used can result in further monetary cost. battery life could be reduced. in some situations, such as hardware for space flight, power may need to be reduced to what may be produced from solar or some other means. 

> volume or mass - size may be a factor, such as in a vehicle where cargo space may be sacrificed, or on spaceflights where every gram matters. 

## 1.6
* **Calculate** frequency and cycle time (given the other)

> $$
> \mathrm{frequency} = \frac{1}{\mathrm{cycle \ time}}
> $$

> $$
> \mathrm{cycle \ time} = \frac{1}{\mathrm{frequency}}
> $$

### A processor operates at 3.5 GHz. What is the cycle time?

$$
\mathrm{frequency} = \frac{1}{t_c}
$$

$$
3.5 \ \mathrm{GHz} = 3.5 \times 10^9 \frac{\mathrm{cycles}}{\mathrm{second}}
$$

$$
\frac{1}{3.5 \times 10^9} \approx 2.85714286 \times 10^{-10} = .285714286 \times 10^{-9} = .285714286 \ \mathrm{ns}
$$

* **Calculate** peak MIPS given CPI and frequency

> $$
> \mathrm{MIPS} = \frac{\mathrm{frequency}}{\mathrm{CPI}}
> $$

### A processor operates 1.25 GHz and has a maximum CPI of 0.8. What is the peak MIPS?

$$
\mathrm{MIPS} = \frac{\mathrm{frequency}}{\mathrm{CPI}}
$$

$$
1.25 \ \mathrm{GHz} = 1250 \ \mathrm{MHz} = 1250 \times 10^6 \frac{\mathrm{cycles}}{\mathrm{second}}
$$

$$
\frac{1250 \times 10^6 \frac{\mathrm{cycles}}{\mathrm{second}}}{.8} = 1.5625 \times 10^9 = 1562.5 \ \mathrm{MIPS} 
$$

* **Calculate** average cycles per instruction (CPI)

> $$
> \mathrm{CPI} = \frac{\mathrm{frequency}}{\mathrm{MIPS}}
> $$

> $$
> \mathrm{CPI} = \frac{\mathrm{cycles}}{\mathrm{instruction}}
> $$

### Analyzing a certain program, you find 50% of the instructions take a processor 1 cycle 30% take 2 cycles, and 20% take 4 cycles. What is the average CPI?

$$
.5(1) + .3(2) + .2(4) = .5 + .6 + .8 = 1.9 \ \mathrm{CPI_{average}}
$$

* **Calculate** FLOPS given CPI and frequency

> $$
> \mathrm{FLOPS} = \frac{\mathrm{frequency}}{\mathrm{CPI_{\mathrm{floating-point}}}}
> $$

### A processor has a CPI of 0.6 for floating point instructions and runs at 750 MHz. What is the FLOPS of  this system?

$$
\mathrm{FLOPS} = \frac{\mathrm{frequency}}{\mathrm{\mathrm{CPI}_{\mathrm{floating-point}}}}
$$

$$
\frac{750 \ \mathrm{M} \frac{\mathrm{cycles}}{\mathrm{seconds}}}{.6\frac{\mathrm{cycles}}{\mathrm{floating-point \ instructions}}} = 1250 \ \mathrm{M} \frac{\mathrm{floating-point \ instructions}}{\mathrm{seconds}} = 1250 \ \mathrm{MFLOPS}
$$

$$
1250 \ \mathrm{MFLOPS} = 1,250,000,000 \ \mathrm{FLOPS}
$$

* Memory access time vs. cycle time

> Memory access time is how long it takes to read/write data or instructions, and may be shorter than cycle time. The cycle time ideally matches the CPU clock cycle time, and may be slower than access time as some memory technologies have overhead or recovery times between reads/writes.

* **Calculate** memory bandwidth given cycle time and bus size

> $$
> \mathrm{bandwidth} = \frac{\mathrm{bytes (width)}}{\mathrm{seconds}}
> $$

### A memory system has a cycle time of 7 ns, and a 32 bit wide bus. What is the memory bandwidth?

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

* Describe overclocking and underclocking

> Overclocking reduces power efficiency to increase CPU performance. Underclocking increases power efficiency at the cost of CPU performance.

* Describe benchmarking

> Benchmarking is utilized to demonstrate the computational power of various computing systems. Various benchmarks test different facets of performance, such as testing integer math or floating-point math.

* Benchmark used for TOP500

> The LINPACK benchmark is used for the TOP500.

* Benchmark often used for MIPS

> Dhrystones can be used to calculate MIPS. 

* SPEC benchmarks

> Industry standard and widely seen as fair and useful due to use of real code and requirement of full disclosure of system hardware and software.

# Chapter 2

## 2.1
* Ideal characteristics of memory

> * low cost 
> * high speed 
> * high information density 
> * nonvolatile
> * read/write capable
> * low power use
> * durable (MTBF)
> * removeable

* Inherent tradeoffs in memory 

> Fast memory is likely to be expensive and have less capacity. Slower memory is likely to be cheaper and larger in storage size. 

* Three main types of memory by technology used

> * semiconductor
> * magnetic
> * optical

* Properties, advantages, and disadvantages of various types
  * Semiconductor: DRAM, SRAM, flash

    > Semiconductor memory tends to be faster than other technologies. DRAM took over from magnetic core memory due to it being read/writeable, information dense relative to other semiconductor memory, and low cost. DRAM is volatile, must be refreshed, and slow comapred to other semiconductor memories. SRAM is used when higher speed is needed, but is less dense and more expensive (and still volatile). SRAM is typically used for internal registers and cache. Flash memory is cheaper than DRAM and nonvolatile, so widely used as secondary storage. It is descended from semiconductor ROMs, and while it can be rewritten, writes may be slower.  

  * Magnetic: hard disk, tape

    > Magnetic HDD's are very cheap and have high information density, but are very slow and can fail catastrophically due to moving physical parts. Magnetic tapes, typically used for archival, is nonvolatile, inexpensive, and very slow.  

  * Optical: CD-ROM, DVD

    > Optical devices are typically used as backup media and to hold entertainment content. CD-ROM was read-only, and held 100's of MB. DVD's could be read-only or read/write depending on if it was DVD-ROM or DVD±RW. They can hold several GB. 

* MRAM – what is it and why is it different/better

> MRAM, or magnetic RAM, is essentially a semiconductor/magnetic hybrid. It operates on the principal of magnetic resistance. It is nonvolatile and randomly addressable. It has the potential to replace DRAM, which would lead to the possibility of 'instant-on' computers.

* Construct a memory hierarchy

> Pretend it's a pyramid:

| CPU registers |
| ------------- |  
| L1 cache |
| L2 cache |
| L3 cache |
| main memory |
| disk memory |
| backup storage |

* CPU-memory gap problem

> There are two main speed gaps in a computer system: the gap between CPU and main memory, and the gap between main memory and secondary memory. Using a hierarchical memory system, we can bridge those gaps with cache and virtual memory, respectively.

## 2.2 and 2.3
* Describe three types of memory organization and give an example of each

> * Random Access Memory (RAM) - DRAM (RAM literally means random access memory, and specifies the ability to access any item in memory with the same access time.)
> * Sequential Access Memory (SAM) - magnetic tape (SAM is sequential access, meaning items that are further away take longer to access.)
> * Content Addressable Memory (CAM) - associative memory (CAM contents can be checked for one or more matches simultaneously based on the content of the data.)

* RAM

> RAM literally means random access memory, and specifies the ability to access any item in memory with the same access time.

* High order interleaving advantages and disadvantages

> Advantages: simple to implement, devices that remain idle can be utilized by other devices. 

> Disadvantages: does nothing to speed up access by a single CPU

* Low order interleaving advantages and disadvantages – when does it perform well vs poorly

> Advantages: sequentially accessed data/instructions can have overlapped accesses, potentially speeding up effective memory access time according to the number of memory devices. in a 4-way interleave, 
> $t_{a \ \mathrm{effective}}$
> could be ideally 
> $\frac{t_a}{4}$
> .

> Disadvantages: complex to implement, CPU can monopolize all memory devices, preventing other devices such as GPUs, I/O, or other CPUs from using it. 

> It performs well in high-performance machines, especially vector computers due to a high volume of sequential accesses. Not ideal for general-purpose computers.

* **Calculate** max theoretical speed increase from low order interleaving

### A memory technology with a cycle time of 3 ns is designed with 4 way low order interleaving. Assuming the bus is large enough, what is the fastest the effective cycle time can be?

$$
t_c = 3 \ \mathrm{ns}
$$

$$
t_{a \ \mathrm{effective}} = \frac{t_c}{\mathrm{interleave \ factor}}
$$

$$
\frac{3 \ \mathrm{ns}}{4} = .75 \ \mathrm{ns}
$$

$$
\frac{3 \ \mathrm{ns}}{.75 \ \mathrm{ns}} = 4
$$

> Effective cycle time could be up to 4 times faster.

* SAM

> SAM is sequential access memory, meaning items that are further away take longer to access.

* Relative addressing

> Relative addressing refers to identifying where data is not by a unique address, but as a relative value to the last accessed location.

* CAM

> Content Addressable Memory (CAM) contents can be checked for one or more matches simultaneously based on the content of the data.

* Argument, mask, and match registers

> If using CAM, you have an argument - what you're trying to match. 

> Mask is used to specify irrelevant bits - should this bit be matched or not.

> The match register tells you if you have a match.

## 2.4
* Describe cache and why it’s used

> A cache memory is a small, fast memory that holds a subset of a larger, slower memory. It is used as a high-speed buffer memory between the CPU and main memory to bridge the speed gap between CPU and main memory.

* L1 vs L2 vs L3

> L1 is split into data and instructions - about 8-32 KB.

> L2 is general-purpose but core specific - about 256 KB - 1 MB. 

> L3 is larger and shared with all cores - about 8-32 MB. 

* Describe locality of reference, why programs exhibit it, and know the three types

> Locality of reference refers to the tendency of programs to access code and data that have recently been accessed, or that are near items that were recently accessed. Accesses to memory tend to be concentrated in just a few regions of memory.

> Programs tend to exhibit locality of reference for a variety of reasons:
> * program code stored sequentially
> * program loops execute the same code repeatedly
> * subroutines are called repeatedly
> * common data structures are stored sequentially
> * scalar data usually placed in common block by compilers

> 1. Temporal - if a given memory location is accessed, it has a high probability of being accessed again in the near future.
> 2. Spatial - locations near a recently accessed location are likely to be accessed again soon.
> 3. Sequential - the very next item in memory is likely to be accessed after the one before it.

* Describe and **calculate** hit and miss ratios

> Hit ratio refers to the percentage of the times a requested piece of data is resident in cache. A miss ratio is the percentage of times a requested piece of data is not resident in cache and must be fetched from main memory. 

### A given program runs with 240,000 cache misses and 4,730,000 cache hits. What are the hit and miss ratios?

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

* Describe the three types of cache misses

> compulsory misses - sometimes called cold start misses. the first time the program accesses an area of memory, the location will not yet be cached.

> capacity misses - since cache is finite, data may not fit. when cache fills up, adding new info means evicting old info. 

> conflict misses - occurs only in direct-mapped cache, when two or more regions of main memory in use map to the same line.

* **Calculate** effective average memory access time

### A system’s cache cycle time is 0.8 ns, and its main memory access time is 5 ns. Using the hit and miss counts from question 7, find the effective memory access time.

$$
t_c = .8 \ \mathrm{ns}
$$

$$
t_{a \ \mathrm{effective}} = \mathrm{hit \ ratio}(t_{a \ \mathrm{cache}}) + \mathrm{miss \ ratio}(t_{a \ \mathrm{main}})
$$

$$
t_{a \ \mathrm{effective}} = .9517(.8 \ \mathrm{ns}) + .0483(5 \ \mathrm{ns}) = .76136 \ \mathrm{ns} + .2415 \ \mathrm{ns} = 1.00286 \ \mathrm{ns}
$$

* Describe a refill line

> Chunk of data from memory stored in a single location in cache together - analagous to a page.

* Fully associative vs. n-way set associative vs direct mapping (describe and advantages/disadvantages)

> Fully-associative memory utilizes CAM to create cache where any line can have contents from anywhere in memory. Addresses consist of a tag to match on, and the byte - the offset within the refill line. Tends to have a higher hit ratio but is complex to implement and expensive.

> N-way set associative mapping is similar to direct-mapping, but each location is now partitioned into two or more subsets operating in parallel. This helps alleviate the number of conflict misses that may arise from a direct-mapped system. Data cache generally benefits more from increased associativity. 

> Direct-mapping is cheap and easy to implement, but any given block of main memory can only reside in one specific cache line. The address now must contain an index in addition to tag and byte. The index specifies which cache line to check. 

* Given a main memory size, cache size, line size, and associativity, **calculate** number of cache lines, as 
well as tag, index, and byte of an address

### A system with 8 GB of DRAM as a main memory has a 16 MB L3 cache with 8 way interleaving, and 128 byte refill lines. What are the sizes of the tag, index, and bytes fields for this cache? List all three answers. What are these values if the the cache is direct mapped?

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

# //TODO add example working backward

* Advantage of having separate instruction and data cache

> Separate instruction and data cache prevents the von Neumann bottleneck, where computer system throughput is limited by having a single path to memory for instructions and data. 

* Write through vs. write back policies (describe, and advantages/disadvantages)

> Write-through cache updates main memory each time a write is performed on data present in memory - effectively rendering all write accesses cache misses. It is simple to implement.

> Write-back cache adds a dirty bit to check if data has been modified, and only writes back to main memory if the data is to be evicted from cache.

* Dirty bit

> The dirty bit holds a boolean value indicating if the contents have been modified.

* Cache replacement policies – LRU, LFU, FIFO, and random (describe)

> LRU (Least Recently Used) - least recently used piece of data is evicted from cache. somewhat complex, requires hardware to track time since last access.

> LFU (Least Frequently Used) - least frequently used piece of data is evictec from cache. complex to implement, requires a hit counter in hardware. risks evicting data that simply hasn't been used much yet. 

> FIFO (First in first out) - simple to implement, but least optimal. evicts data similar to how a stack pops data. 

> Random chooses a random value to evict. Used due to larger cache making replacement algorithms less relevant.

* Valid bit

> Used for cache initialization to verify data resident in cache isn't garbage data from a reset or context switch.

* Prefetching

> When we are moving things into cache before they are asked for. Sequential prefetching is one way, but there can also be predictive prefetching.

## 2.5
* Virtual memory

> Bridges the speed gap between main and secondary memory. Allows programs to have a large virtual address space for their exclusive use, from the program perspective. 

* Logical address vs. physical address

> A physical address refers to a physical location within memory, a unique identifier to point to that location. A logical (or virtual) address refers to a location within a program's virtual memory, and must be translated to a physical address before accessing.

* MMU

> The memory management unit handles virtual to physical address translation by maintaining tables with translation information.

* Page table base register

> A page table base register in the MMU points to 
the starting location of the page table in memory.

* Paging vs segmented virtual memory

> Paged memory uses fixed-size pages to load information from secondary memory. It is a hardware-oriented approach. Page faults can occur when a requested page has not been loaded from secondary memory. Internal fragmentation is possible from unused space within pages. It is more efficient than segmentation.

> Segmentation has variable-sized segments. It is a software-oriented approach. Segment faults can occur when a requested segment has not been loaded from secondary memory. External fragmentation is possible from space between loaded segments not being a good fit for the next segment to be mapped. It is less efficient than paging. 

* Multiple level page tables

It is easier for the hardware to deal with a greater number of smaller sized tables, so they are frequently broken up into multiple levels of tables.

* Page fault

> Analogous to a cache miss, this is when a requested page has not been loaded from secondary memory. It is much more costly in terms of performance than a cache miss, but happens less frequently.

* Thrashing

> Thrashing can occur when the smae pages are continuously displaced and then reloaded. 

* TLB

> The TLB (translation lookaside buffer) is an internal cache to hold recent or frequently used table entries.

* Compare and contrast cache and virtual memory

> Similarities:
> * both hold data/instructions for the CPU
> * both use hardware for mapping
> * both transfer blocks of data between a larger, slower memory and a smaller, faster memory
> * both suffer in performance if data is not there

> Differences:
> * segment/page faults tend to happen much less than cache misses
> * segment/page faults take orders of magnitude longer than cache misses
> * cache is purely hardware, virtual memory is controlled by software (OS) and hardware (MMU)

* Physical vs. virtual addressed cache -  four different implementations

> Virtual addressing is fast - we can check for a hit without waiting for the MMU. It has more consistent performance as virtual addresses don't change with different programs as physical addresses do. If used, then cache needs to be flushed on context switch to avoid matching on garbage data. Physical addressing is slower. 

> PIPT (physically indexed, physically tagged) - most systems use this beyond the lowest cache levels. address is fully translated via TLB and page tables before cache is checked.

> VIVT (virtually indexed, virtually tagged) - cache uses purely virtual addresses. TLB lookup happens after. Can be faster, but subject to aliasing.

> VIPT (virtually indexed, physically tagged) - avoids aliasing. x86 uses this for L1 and L2 caches. TLB lookup and cache lookup happen in parallel.

> PIVT (physically indexed, virtually tagged) - not used

* Aliasing

> Aliasing is when the same physical location gets mapped into two places in virtual memory. VIVT addressed cache is subject to aliasing.