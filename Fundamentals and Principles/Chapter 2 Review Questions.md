# Chapter 2 Review Questions

1. Consider the various aspects of an ideal computer memory discussed in section 2.1.1 and the characteristics of available memory devices discussed in Section 2.1.2. Fill in the columns of the table below with the following types of memory devices, in order from most desirable to least desirable: magnetic hard disk, semiconductor DRAM, CD-R, DVD-RW, semiconductor ROM, DVD-R, semiconductor flash memory, magnetic floppy disk, CD-RW, semiconductor static RAM, semiconductor EPROM

> Note:
> * hard disk
> * floppy disk
> * CD-R
> * CD-RW
> * DVD-R
> * DVD-RW
> * RAM
> * SRAM
> * DRAM
> * ROM
> * EPROM
> * flash memory



| cost/bit | speed | information density | volatility | readable/writable? | power consumption | durability | removable/portable? | 
| -- | -- | -- | -- | -- | -- | -- | -- | 
| (*lower is better*) | (*higher is better*) | (*higher is better*) | (*non-volatile is better*) | (*both is usually better*) | (*lower is better*) | (*more durable is better*) | (*more portable is usually better*) | 
| floppy disk |  SRAM  | DRAM | hard disk (nonvolatile) | DRAM (both) |    |    | floppy disk |   
| hard disk |  DRAM  | SRAM | floppy disk (nonvolatile)   | SRAM (both) |    |    |  CD-R  |
|  CD-R  |  RAM  |  ROM  |  flash (nonvolatile)  |  DVD-RW (both)  |    |    |  CD-RW  |
|  CD-RW  |  ROM  |  EPROM  |  CD-R (nonvolatile)  | CD-RW (both)   |    |    |  DVD-R  |
|  DVD-R  |  EPROM  | RAM   |  CD-RW (nonvolatile) | RAM (both)   |    |    |  DVD-RW  |
|  DVD-RW  |  flash  |  flash  |  DVD-R (nonvolatile)  |  hard disk (both)  |    |    | hard disk   |
|  flash  |  hard disk  |  hard disk  |  DVD-RW (nonvolatile)  |  floppy disk (both)  |    |    |  flash  |
| RAM   |  floppy disk  |  floppy disk  |  ROM (nonvolatile)  | flash (read-mostly)   |    |    |  EPROM  |
|  DRAM  |  CD-R  |  DVD-R  |  EPROM (nonvolatile)  |  EPROM (read only)[^1]  |    |    |  ROM  |
|  ROM  | CD-RW | DVD-RW   |  RAM (volatile)  |  DVD-R (read only)  |    |    |  RAM  |
|  EPROM  |  DVD-R  | CD-R   | DRAM (volatile) | CD-R (read only) |    |    |  DRAM  |
| SRAM   | DVD-RW | CD-RW   | SRAM (volatile) | ROM (read only) |    |    |  SRAM  |

[^1]: EPROMs can be reprogrammed in a separate circuit after erasure with ultraviolet light.

2. Describe in your own words what a hierarchical memory system is and why it is used in the vast majority of modern computer systems.

<details><summary>Answer</summary>
<p>

> A hierarchical memory system uses a mixture of different types of devices in a system in order to trade off the advantages and disadvantages of each memory system. 
</p>
</details>

3. What is the fundamental, underlying reason that low-order main memory interleaving and/or cache memories are needed and used in virtually all high-performance computer systems?

<details><summary>Answer</summary>
<p>

> The CPU is much faster than current memory technologies, and low-order main memory interleaving and/or cache memories allow the speed of memory access to approach the speed of the CPU, vastly improving overall performance. 
</p>
</details>

4. A main memory system is designed using 15 ns RAM devices using a four-way low-order interleave.
   1. What would be the effective time per main memory access under ideal conditions?

    <details><summary>Answer</summary>
    <p>

    > Say the cycle time is 
    $t$
    nanoseconds. Under ideal conditions, the effective time per main memory access would be 
    $\frac{t}{4}$
    , or 
    $\frac{15}{4} = 3.75 \ \mathrm{ns}$

    </p>
    </details>

   2. What would constitute ideal conditions? (In other words, under what circumstances could the access time you just calculated be achieved?)

    <details><summary>Answer</summary>
    <p>

    > Consecutively numbered memory locations would have each successive access to a different device, constituting ideal conditions for low-order interleaving.
    </p>
    </details>

   3. What would constitute worst-case conditions? (In other words, under what circumstances would memory accesses be the slowest?) What would the access time be in this worst case scenario? If ideal conditions exist 80% of the time and worst-case conditions occur 20% of the time, what would be the average time required per memory access?

    <details><summary>Answer</summary>
    <p>
    
    > The worst case scenario would occur if we tried to access every fourth memory location, continually accessing the same device. Effective cycle time will revert to 
    $t$
    , or 
    $15 \ \mathrm{ns}$
    . 
    
    > If ideal conditions exist 80% of the time and worst-case situations 20% of the time:
    $$
    .8(3.75 \ \mathrm{ns}) + .2(15 \ \mathrm{ns})
    $$

    $$
    3 \ \mathrm{ns} + 3 \ \mathrm{ns} = 6 \ \mathrm{ns}
    $$

    </p>
    </details>

   4. When ideal conditions exist, we would like the processor to be able to access memory every clock cycle with no wait states (that is, without any cycles wasted waiting for memory to respond). Given this requirement, what is the highest processor bus clock frequency that can be used with this memory system?

    <details><summary>Answer</summary>
    <p>

    > unsure

    </p>
    </details>

   5. Other than increased hardware cost and complexity, are there any potential disadvantages of using a low-order interleaved memory design? If so, discuss one such disadvantage and the circumstances under which it might be significant.

    <details><summary>Answer</summary>
    <p>
    
    > In systems with multiple processors (or other devices that need to access memory), the memory system is designed to maximize the bandwidth of transfers to or from a single device. So, if one processor is taking advantage of accessing sequentially numbered memory locations, it is using up the full bandwidth of all the memory devices and there is no opportunity for any other processor or device to access memory without halting the first. 
    </p>
    </details>


5. Is it correct to refer to a typical semiconductor integrated circuit ROM as a random access memory? Why or why not? Name and describe two other logical organizations of computer memory that are not random access.

<details><summary>Answer</summary>
<p>

> It is correct. The critical property of RAM is that all locations are accessed in equal time. ROMs can access any value in the same time. Magnetic disk and CD, among numerous other organizations, are not random access.
</p>
</details>

6. Assume that a given system's main memory has an access time of 6.0 ns, and its cache has an access time of 1.2 ns (five times as fast). What would the hit ratio need to be in order for the effective memory access time to be 1.5 ns (four times as fast as main memory)?

<details><summary>Answer</summary>
<p>

> I have no idea, based on the text

$$
\mathrm{hit \ ratio} = p_h = \frac{\mathrm{number \ of \ hits}}{(\mathrm{number \ of \ hits}) + (\mathrm{number \ of \ misses})}
$$

$$
t_{a \ \mathrm{cache}} = \mathrm{speed \ ratio} \times \mathrm{main \ memory \ access \ time} = \frac{1}{5} \times 1.2 \ \mathrm{ns} = .24 \ \mathrm{ns}
$$

$$
1.5 \ \mathrm{ns} = .24 \ \mathrm{ns} \ \times p_h + 1.5 \ \mathrm{ns} \ \times (1- p_h)
$$

</p>
</details>

7. A particular program runs on a system with cache memory. The program makes a total of 250,000 memory references; 235,000 of these are to cached locations.
   1. What is the hit ratio in this case?

    <details><summary>Answer</summary>
    <p>

    $$
    \mathrm{hit \ ratio} = p_h = \frac{\mathrm{number \ of \ hits}}{(\mathrm{number \ of \ hits}) + (\mathrm{number \ of \ misses})}
    $$

    $$
    p_h = \frac{235,000}{250,000} = .94
    $$

    </p>
    </details>

   2. If the cache can be accessed in 1.0 ns but the main memory requires 7.5 ns for an access to take place, what is the average time required by this program for a memory access, assuming all accesses are reads? 

    <details><summary>Answer</summary>
    <p>

    $$
    t_{a \ \mathrm{effective}} = t_{a \ \mathrm{cache}} \times p_h  + t_{a \ \mathrm{main}} \times (1- p_h)
    $$

    $$
    t_{a \ \mathrm{effective}} = 1 \times .94 + 7.5 \times .06
    $$

    $$
    t_{a \ \mathrm{effective}} = .94 + .45 = 1.39 \ \mathrm{ns}
    $$

    </p>
    </details>

   3. What would be the answer to (7.2) if a write-through policy is used and 75% of memory accesses are reads?

    <details><summary>Answer</summary>
    <p>

    > not really sure
    
    </p>
    </details>

8. Is hit ratio a dynamic or static performance parameter in a typical computer memory system? Explain your answer.

<details><summary>Answer</summary>
<p>

> Hit ratio is a dynamic performance parameter. The cache contents change over time, beginning empty and gaining accuracy as the program runs, so the performance tends to get better over time. 
</p>
</details>

9. What are the advantages of set-associative cache organization as opposed to a direct-mapped or fully associative mapping strategy?

<details><summary>Answer</summary>
<p>

> Set-associative cache is cheaper and simpler than fully-associative cache, but has a potentially higher hit ratio and thus better system performance than direct-mapped cache. 

</p>
</details>

10. A computer has 64 MB of byte-addressable main memory. A proposal is made to design a 1 MB cache memory with a refill line (block) size of 64 bytes.
    1.  Show how the memory address bits would be allocated for a direct mapped cache organization.

    <details><summary>Answer</summary>
    <p>

    $$
    \mathrm{refill \ line \ size} = 64 \ \mathrm{bytes}
    $$

    $$
    32 \ \mathrm{address \ bits}
    $$
    
    | $11 \ \mathrm{bits}$ | $15 \ \mathrm{bits}$ | $6 \ \mathrm{bits}$ |
    | -- | -- | -- |
    | $\mathrm{Tag}$ | $\mathrm{Index}$ | $\mathrm{Byte}$ | 

    </p>
    </details>

    2.  Repeat (10.1) for a four-way set-associative cache organization.

    <details><summary>Answer</summary>
    <p>

    > Honestly, I'm just guessing. Clarify how this calculation is made in lecture

    $$
    \mathrm{refill \ line \ size} = 64 \ \mathrm{bytes}
    $$

    | $13 \ \mathrm{bits}$ | $13 \ \mathrm{bits}$ | $6 \ \mathrm{bits}$ |
    | -- | -- | -- |
    | $\mathrm{Tag}$ | $\mathrm{Index}$ | $\mathrm{Byte}$ | 

    </p>
    </details>

    3.  Repeat (10.1) for a fully associative cache organization.

    <details><summary>Answer</summary>
    <p>

    > If the byte-addressable main memory uses 
    $32 \ \mathrm{bit}$
    addresses and each refill line contains
    $2^6 = 64 \ \mathrm{bytes}$
    , then the associative tags will be the upper
    $32 - 6 = 26$
    address bits. 

    | $26 \ \mathrm{bits}$ | $6 \ \mathrm{bits}$ | 
    | -------------- | --------------- |
    | $\mathrm{Tag}$ | $\mathrm{Byte}$ |

    </p>
    </details>

    4.  Given the direct-mapped organization and ignoring any extra bits that might be needed (valid bit, dirty bit, etc.), what would be the overall size ("depth" by "width") of the memory used to implement the cache? What type of memory devices would be used to implement the cache (be as specific as possible)? 

    <details><summary>Answer</summary>
    <p>
    </p>
    </details>

    5.  Which line(s) of the direct-mapped cache could main memory location $1 \mathrm{E} 0027 \mathrm{A}_{16}$ map into? (Give the line number\[s\], which will be in the range of 0 to \[n-1\] if ther are n lines in the cache.) Give the memory address (in hexadecimal) of another location that could not reside in cache at the same time as this one (if such a location exists).

    <details><summary>Answer</summary>
    <p>
    </p>
    </details>


11. Define and describe virtual memory. What are its purposes, and what are the advantages and disadvantages of virtual memory systems? 

<details><summary>Answer</summary>
<p>

> In a system using virtual memory, each program has its own virtual address space within which all memory references are contained. 

> In many cases, the code and data for a program are larger than the amount of main memory physically present in a system. With multitasking, other programs can be resident in memory at the same time. The purpose of this large virtual address space is to give the programmer (and compiler) the illusion of huge main memory exclusively allocated for the progra, thus freeing the programmer of the burden of memory management.

> Freeing programmers from memory management concerns is one advantage. Another is the ability to utilize the very large, very slow secondary memory at higher speeds by implementing paged or segmented schemes. This is similar to how cache bridges the gap between main memory and CPU. 

> A disadvantage of this scheme is that virtual addresses must be translated into physical addresses, which takes time. The hardware required adds expense and complexity to the system.

</p>
</details>

12.   Name and describe the two principal approaches to implementing virtual memory systems. How are they similar, and how do they differ. Can they be combined, and if so, how? 

<details><summary>Answer</summary>
<p>

> Paged and segmented are the two principal approaches to virtual memory systems.

> They are similar in that with both systems, blocks of memory are transferred from secondary to main memory on demand, much like cache. 

> They are different in that paged virtual memory uses fixed-size blocks of memory to transfer between main and secondary memory, while segmented virtual memory uses variable-sized blocks of memory. Paged memory can suffer from internal fragmentation, while segmented memory can suffer from external fragmentation.

> The two approaches can be combined into segmentation with paging. Segments are composed of one or more pages, allowing segments to be of variable size up to a maximum. 

</p>
</details>

13.   What is the purpose of having multiple levels of page or segment tables rather than a single table for looking up address translations? What are the disadvantages, if any, of this scheme.

<details><summary>Answer</summary>
<p>

> With multiple levels, it is no longer necessary to maintain one large table. This allows lookup to be done in a stepwise fashion. It takes longer, but the smaller tables are easier and more efficient to deal with.

</p>
</details>

14.  A process running on a system with demand-paged virtual memory generates the following reference string (sequence of requested pages): 

> 4, 3, 6, 1, 5, 1, 3, 6, 4, 2, 2, 3

The operating system allocates each process a maximum of four page frames at a time. What will be the number of page faults for this process under each of the following page replacement policies? 
    1. LRU
    2. FIFO
    3. LFU (with FIFO as tiebreaker)

<details><summary>Answer</summary>
<p>

| LRU: | | 
| -- | -- |
| 4, 3, 6, 1 | loaded initially |
| 3, 6, 1, 5 | page fault 1 |
| 3, 6, 1, 4 | page fault 2 |
| 3, 6, 2, 4 | page fault 3 |

| FIFO: | | 
| ---- | -- |
| 4, 3, 6, 1 | loaded initially | 
| 3, 6, 1, 5 | page fault 1 |
| 6, 1, 5, 4 | page fault 2 |
| 1, 5, 4, 2 | page fault 3 |
| 5, 4, 2, 3 | page fault 4 |

| LFU: | (FIFO tiebreaker) | 
| --- | --- |
| 4, 3, 6, 1 | loaded initially |
| 3, 6, 1, 5 | page fault 1 |
| 3, 6, 1, 4 | page fault 2 |
| 3, 6, 1, 2 | page fault 3 |

> Page fault 1 uses FIFO tiebreaker to remove 4. Page fault 2 uses LFU to remove 5. Page fault 3 uses LFU to remove 4. 

</p>
</details>

15.   In what ways are cache memory and virtual memory similar? In what ways are they different? 

<details><summary>Answer</summary>
<p>

Cache memory and virtual memory both use techniques to make a slower, larger memory accessible via a faster, smaller memory. Cache memory bridges the gap between the CPU and main memory, while virtual memory bridges the gap between main memory and secondary memory. Both concepts rely heavily on the locality of reference to anticipate the CPU's needs. Virtual memory deals with much larger blocks of data than cache, and likely as a result, page or segment faults tend to occur less than cache misses.

</p>
</details>

1.    In systems that make use of both virtual memory and cache, what are the advantages of a virtually addressed cache? Does a physically addressed cache have any advantages of its own, and if so, what are they? Describe a situation in which one of these approaches would have to be used because the other would not be feasible. 

<details><summary>Answer</summary>
<p>

> Virtually addressed caches are advantageous because they are fast. The cache controller does not have to wait on the MMU to translate the address before checking for a hit.

> Because all the cache tags and indices are based on a single physical address space, rather than a virtual address space for each process, information can be left in a physically addressed cache when a task switch occurs. In a virtually addressed cache we would be concerned that address
> $n$
> from one program is equivalent to address
> $n$ 
> in another, meaning cache has to be 'flushed' on each context change. This means a physically addressed cache could have a performance advantage in multithreaded multitasking systems with frequent task changes.

> Physically addressed caches may cause problems to exhibit performance variations between otherwise identical runs, which can significantly impact hit ratio. In a system that needs consistent high performance, physically addressed cache would not be feasible.

</p>
</details>

1s7.   Fill in the blanks bellow with the most appropriate term or concept discussed in this chapter: 

________ A characteristic of a memory device that refers to the amount of information that can be stored in a given physical space or volume.

________ A semiconductor memory device made up of a large array of capacitors; its contents must be periodically refreshed in order to keep them from being lost. 

________ A developing memory technology that operates on the principle of magnetoresistance; it may allow the devlopment of "instant-on" computer systems. 

________ A type of semiconductor memory device, the contents of which cannot be overwritten during normal operation but can be erased using ultraviolet light.

________ This type of memory device is also known as a CAM.

________ A register in an associative memory that contains the item to be searched for.

________ The principle that allows hierarchical storage systems to function at close to the speed of the faster, smaller level(s). 

________ This occurs when a needed instruction or operand is not found in cache, so a main memory access is required.
________ The unit of information that is transferred between a cache and main memory.

________ The portion of a memory address that determines wheter a cache line containst the needed information.

________ The most flexible but most expensive cache organization, in which a block of information from main memory can reside anywhere in the cache. 

________ A policy whereby writes to cached locations update main memory only when the line is displaced.

________ This is set or cleared to indicate whether a given cache line has been initialized with "good" information  or contains "garbage" because it is not yet initialized.

________ A hardware unit that handles the details of address translation in a system with virtual memory.

________ This occurs when a program makes reference to a logical segment of memory that is not physically present in main memory.

________ A type of cache used to hold virtual-to-physical address translation information.

________ This is set to indicate that the contents of a faster memory subsystem have been modified and need to be copied to the slower memory when they are displaced.

________ This can occur during the execution of a string or vector instruction when part of the operand is present in main physical memory and the rest is not. 

<details><summary>Answer</summary>
<p>

information density | A characteristic of a memory device that refers to the amount of information that can be stored in a given physical space or volume.

DRAM | A semiconductor memory device made up of a large array of capacitors; its contents must be periodically refreshed in order to keep them from being lost. 

MRAM | A developing memory technology that operates on the principle of magnetoresistance; it may allow the devlopment of "instant-on" computer systems. 

EPROM | A type of semiconductor memory device, the contents of which cannot be overwritten during normal operation but can be erased using ultraviolet light.

content addressable memory | This type of memory device is also known as a CAM.

argument register | A register in an associative memory that contains the item to be searched for.

locality of reference | The principle that allows hierarchical storage systems to function at close to the speed of the faster, smaller level(s). 

cache miss | This occurs when a needed instruction or operand is not found in cache, so a main memory access is required.

line | The unit of information that is transferred between a cache and main memory.

tag | The portion of a memory address that determines wheter a cache line contains the needed information. 

> not sure about tag

associative | The most flexible but most expensive cache organization, in which a block of information from main memory can reside anywhere in the cache. 

> not sure about associative

write-back | A policy whereby writes to cached locations update main memory only when the line is displaced.

valid bit | This is set or cleared to indicate whether a given cache line has been initialized with "good" information  or contains "garbage" because it is not yet initialized.

MMU memory management unit | A hardware unit that handles the details of address translation in a system with virtual memory.

segment fault | This occurs when a program makes reference to a logical segment of memory that is not physically present in main memory.

TLB translation lookaside buffer | A type of cache used to hold virtual-to-physical address translation information.

dirty bit | This is set to indicate that the contents of a faster memory subsystem have been modified and need to be copied to the slower memory when they are displaced.

delayed page fault | This can occur during the execution of a string or vector instruction when part of the operand is present in main physical memory and the rest is not. 

</p>
</details>