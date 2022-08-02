# Chapter 2 Review Questions\

1. Consider the various aspects of an ideal computer memory discussed in section 2.1.1 and the characteristics of available memory devices discussed in Section 2.1.2. Fill in the columns of the table below with the following types of memory devices, in order from most desirable to least desirable: magnetic hard disk, semiconductor DRAM, CD-R, DVD-RW, semiconductor ROM, DVD-R, semiconductor flash memory, magnetic floppy disk, CD-RW, semiconductor static RAM, semiconductor EPROM

> Editor's Note:
> * magnetic hard disk
> * magnetic floppy disk
> * CD-R
> * CD-RW
> * DVD-R
> * DVD-RW
> * semiconductor RAM
> * semiconductor static RAM
> * semiconductor DRAM
> * semiconductor ROM
> * semiconductor EPROM
> * semiconductor flash memory

| cost/bit (lower is better) | speed (higher is better) | information density (higher is better) | volatility (non-volatile is better) | readable/writable? (both is usually better) | power consumption (lower is better) | durability (more durable is better) | removable/portable? (more portable is usually better) | 
| -- | -- | -- | -- | -- | -- | -- | -- | 
|    |    |    |    |    |    |    |    |   
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
|    |    |    |    |    |    |    |    |
2. Describe in your own words what a hierarchical memory system is and why it is used in the vast majority of modern computer systems.
3. What is the fundamental, underlying reason that low-order main memory interleaving and/or cache memories are needed and used in virtually all high-performance computer systems?
4. A main memory system is designed using 15 ns RAM devices using a four-way low-order interleave.
   1. What would be the effective time per main memory access under ideal conditions?
   2. What would constitute ideal conditions? (In other words, under what circumstances could the access time you just calculated be achieved?)
   3. What would constitute worst-case conditions? (In other words, under what circumstances would memory accesses be the slowest?) What would the access time be in this worst case scenario? If ideal conditions exist 80% of the time and worst-case conditions occur 20% of the time, what would be the average time required per memory access?
   4. When ideal conditions exist, we would like the processor to be able to access memory every clock cycle with no wait states (that is, without any cycles wasted waiting for memory to respond). Given this requirement, what is the highest processor bus clock frequency that can be used with this memory system?
   5. Other than increased hardware cost and complexity, are there any potential disadvantages of using a low-order interleaved memory design? If so, discuss one such disadvantage and the circumstances under which it might be significant.
5. Is it correct to refer to a typical semiconductor integrated circuit ROM as a random access memory? Why or why not? Name and describe two other logical organizations of computer memory that are not random access.
6. Assume that a given system's main memory has an access time of 6.0 ns, and its cache has an access time of 1.2 ns (five times as fast). What would the hit ratio need to be in order for the effective memory access time to be 1.5 ns (four times as fast as main memory)?
7. A particular program runs on a systme with cache memory. The program makes a total of 250,000 memory references; 235,000 of these are to cached locations.
   1. What is the hit ratio in this case?
   2. If the cache can be accessed in 1.0 ns but the main memory requires 7.5 ns for an access to take place, what is the average time required by this program for a memorya access, assuming all accesses are reads? 
   3. What would be the answer to (7.2) if a write-through policy is used and 75% of memory accesses are reads?
8. Is hit ratio a dynamic or static performance parameter in a typical computer memory system? Explain your answer. 
9. What are the advantages of set-associative cache organization as opposed to a direct-mapped or fully associative mapping strategy?
10. A computer has 64 MB of byte-addressable main memory. A proposal is made to design a 1 MB cache memory with a refill line (block) size of 64 bytes.
    1.  Show how the memory address bits would be allocated for a direct mapped cache organization.
    2.  Repeat (10.1) for a four-way set-associative cache organization.
    3.  Repeat (10.1) for a fully associative cache organization.
    4.  Given the direct-mapped organization and ignoring any extra bits that might be needed (valid bit, dirty bit, etc.), what would be the overall size ("depth" by "width") of the memory used to implement the cache? What type of memory devices would be used to implement the cache (be as specific as possible)? 
    5.  Which line(s) of the direct-mapped cache could main memory location $1 \mathrm{E} 0027 \mathrm{A}_{16}$ map into? (Give the line number\[s\], which will be in the range of 0 to \[n-1\] if ther are n lines in the cache.) Give the memory address (in hexadecimal) of another location that could not reside in cache at the same time as this one (if such a location exists). 
11. Define and describe virtual memory. What are its purposes, and what are the advantages and disadvantages of virtual memory systems? 
12. Name and describe the two principal approaches to implementing virtual memory systems. How are they similar, and how do they differ. Can they be combined, and if so, how? 
13. What is the purpose of having multiple levels of page or segment tables rather than a single table for looking up address translations? What are the disadvantages, if any, of this scheme. 
14. A process running on a system with demand-paged virtual memory generates the following reference string (sequence of requested pages): 

> 4, 3, 6, 1, 5, 1, 3, 6, 4, 2, 2, 3

The operating system allocates each process a maximum of four page frames at a time. What will be the number of page faults for this process under each of the following page replacement policies? 
    1. LRU
    2. FIFO
    3. LFU (with FIFO as tiebreaker)
15. In what ways are cache memory and virtual memory similar? In what ways are they different? 
16. In systems that make use of both virtual memory and cache, what are the advantages of a virtually addressed cache? Does a physically addressed cache have any advantages of its own, and if so, what are they? Describe a situation in which one of these approaches would have to be used because the other would not be feasible. 
17. Fill in the blanks bellow with the msot appropriate term or concept discussed in this chapter: 

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