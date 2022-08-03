# Chapter 1: Fundamentals of Quantitative Design and Analysis

## 1.1 Introduction
The RISC (Reduced Instruction Set Computer) based machines focused the attention of designers on two critical performance techniques:
* The exploitation of *instruction-level parallelism* initially through pipelining and later through multiple instruction issue
* use of caches initially in simple forms and later using more sophisticated organizations and optimizations.
(ARM is a RISC infrastructure.) 

In 1974, Robert Dennard observed that power density was constant for a given area of silicon even as you increased the number of transistors because of smaller dimensions of each transistor. Remarkably, transistors could go faster but use less power. *Dennard scaling* ended around 2004 because current and voltage couldn't keep dropping and still maintain the dependability of integrated circuits. This change forced the microprocessor industry to use multiple efficient processors or cores instead of a single inefficient processor. 

This milestone signaled a historic switch from relying solely on instruction-level parallelism (ILP), to *data-level parallelism* (DLP), *thread-level parallelism* (TLP), and *request-level paralellism* (RLP). Whereas the compiler and hardware exploit ILP implicitly without the programmer's attention, DLP, TLP, and RLP are explicitly parallel, requiring the restructuring of the application so that it can exploit explicit parallelism. 

*Amdahl's Law* (Section 1.9) prescribes practical limits to the number of useful cores per chip. If 10% of a task is serial, then the maximum performance benefit from parallelism is 10 no matter ow many cores you put on the chip. 

In 1965, Gordon Moore predicted that the number of transistors per chip would double every year, amended in 1975 to every two years. That prediction, *Moore's Law*, lasted about 50 years, but no longer holds due to a combination of:
* transistors no longer getting much better because of the slowing of Moore's Law and the end of Dennard scaling. 
* the unchanging power budgets for microprocessors
* the replacement of the single power-hungry processor with several energy-efficient processors
* the limits to multiprocessing to achieve Amdahl's law

## 1.2 Classes of Computers
| Feature | Personal Mobile Device (PMD) | Desktop | Server | Clusters/Warehouse-Scale Computer | Internet of Things/Embedded |
| ------- | ---------------------------- | ------- | ------ | --------------------------------- | --------------------------- | 
| *price of system* | \$100-\$1000 | \$300-\$2500 | \$5000-\$10,000,000 | \$100,000-\$200,000,000 | \$10-\$100,000 | 
| *price of microprocessor* | \$10-\$100 | \$50-\$500 | \$200-\$2000 | \$50-\$250 | \$0.01-\$100 |
| *critical system design issues* | cost, energy, media performance, responsiveness | price-performance, energy, graphics performance | throughput, availability, scalability, energy | price-performance, throughput, energy proportionality | price, energy, application-specific performance |

### Classes of Parallelism and Parallel Architectures
There are basically two kinds of parallelism in applications:
1. *Data-level parallelism* (DLP) arises because there are many data items that can be operated on at the same time.
2. *Task-level parallelism* (TLP) arises because tasks of work are created that can operate independently and largely in paralle. 

Computer hardware can in turn exploit these two kinds of application parallelism in four major ways:
1. *Instruction-level parallelism* exploits DLP at modest levels with compiler help using ideas like pipelining and at medium levels using ideas like speculative execution.
2. *Vector architectures, GPUs and multimedia instruction sets* exploit DLP by applying a single instruction to a collection of data in parallel. 
3. *Thread-level parallelism* exploits either DLP or TLP in a tightly coupled hardware model that allows for interaction between parallel threads.
4. *Request-level parallelism* exploits parallelism among largely decoupled tasks specified by the programmer or the operating system.

When Flynn (1966) studied the parallel computing efforts in the 1960s, he found a simple classification whose abbreviations we still use. They target DLP and TLP. He looked at the parallelism in the instruction and data streams called for by the instructions at the most constrained component of the multiprocessor and placed all computers in one of four categories:

| Acronym | Expanded | Description |
| ------- | -------- | ----------- | 
| SISD | *single instruction stream, single data stream* | This category is the uni-processor. The programmer thinks of it as the standard sequential computer, but it can exploit ILP.[^1] |
| SIMD | *single instruction stream, multiple data streams* | The same instruction is executed by multiple processors using different data streams. SIMD computers exploit DLP by applying the same operations to multiple items of data in parallel. Each processor has its own data memory, but there is a single instruction memory and control processor, which fetches and dispactches instructions. [^2] |
| MISD | *multiple instruction streams, single data stream* | No commercial mutliprocessor of this type has been built to date, but it rounds out this simple classification.
| MIMD | *multiple instruction streams, multiple data streams* | Each processor fetches its own instructions and operates on its own data, and it targets task-level parallelism. In general, MIMD is more flexible than SIMD and thus more generally applicable, but it is inherently more expensive than SIMD. For example, MIMD computers can also exploit DLP, although the overhead is likely to be higher than would be seen in a SIMD computer. This overhead means that grain size must be sufficiently large to exploit the parallelism efficiently.[^3] |

[^1]: Chapter 3 covers SISD architectures that use ILP techniques such as superscalar and speculative execution.

[^2]: Chapter 4 covers DLP and three architectures that exploit it: vector architectures, multimedia extensions to standard instruction sets, and GPUs. 

[^3]: Chapter 5 covers tightly coupled MIMD architectures, which exploit *thread-level parallelism* because multiple cooperating threads operate in parallel. Chapter 6 covers loosely coupled MIMD architectures - specifically, *clusters* and *warehouse-scale computers* - that exploit *request-level parallelism*, where many independent tasks can proceed in parallel natrually with little need for communication or synchronization. 

## 1.3 Defining Computer Architecture
### Instruction Set Architecture (ISA)
We use the term ISA to refer to the actual programmer-visible instruction set. The ISA serves as the boundary between the software and hardware. The seven dimensions of an ISA:

| Dimension | Description |
| --------- | ----------- | 
| *Class of ISA* | Nearly all ISAs today are classified as general-purpose register architectures, where the operands are either registers or memory locations. The 80x86 has 16 general-purpose registers and 16 that can hold floating-point data, while RISC-V has 32 general-purpose and 32 floating-point registers.[^4] The two popular versions of this class are *register-memory* ISAs, such as the 80x86, which can access memory as part of many instructions, and *load-store* ISAs, such as ARMv8 and RISC-V, which can access memory only with load or store instructions. All ISAs announced since 1985 are load-store. |
| *Memory addressing* | Virtually all desktop and server computers, including the 80x86, ARMv8, and RISC-V, use byte-addressing to access memory operands. Some architectures, like ARMv8, require that objects must be *aligned*. An access to an object of size $s$ at byte address $A$ is aligned if $A\mod{s=0}$. The 80x86 and RISC-V do not require alignment, but accesses are generally faster if operands are aligned. 
| *Addressing modes* | In addition to specifying registers and constant operands, addressing modes specify the address of a memory object. RISC-V addressing modes are Register, Immediate (for constants), and Displacement, where a constant offset is added to a register to form the memory address. The 80x86 supports those three modes, plus three variations of displacement: no register (absolute), two registers (based indexed with displacement), and two registers where one register is muliplied by the size of the operand in bytes (based with scaled index and displacement). It has more like the last three modes, minus the displacement field, plus register indirect, indexed, and based with scaled index. ARMv8 has the three RISC-V addressing modes plus PC-relative addressing, the sum of two registers, and the sum of two registers where one register is multiplied by the size of the operand in bytes. It also has autoincrement and autodecrement addressing, where the calculated address replaces the contents of one of the registers used in forming the address. | 
| *Types and sizes of operands* | Like most ISAs, 80x86, ARMv8, and RISC-V support operand sizes of 8-bit (ASCII character), 16-bit (Unicode character or half word), 32-bit (integer or word), 64-bit (double word or long integer), and IEEE 754 floating pont in 32-bit (single precision) and 64-bit (double precision). The 80x86 also supports 80-bit floating point (extended double precision).
| *Operations* | The general categories of operations are data transfer, arithmetic, logical, control, and floating point. RISC-V is a simple and easy to pipeline ISA.[^5] The 80x86 has a much richer and larger set of operations.[^6] |
| *Control flow instructions* | Virtually all ISAs, including these three, support conditional branches, unconditional jumps, procedure calls, and returns. All three use PC-relative addressing, where the branch address is specified by an address field that is added to the PC. There are some small differences. RISC-V conditional branches test the contents of registers, and the 80x86 and ARMv8 branches test condition code bits set as side effects of arithmetic/logic operations. The ARMv8 and RISC-V procedure call places the return address in a register, whereas the 80x86 call places the return address on a stack in memory. 
| *Encoding an ISA* | There are two basic choices on encoding: *fixed length* and *variable length*. All ARMv8 and RISC-V instructions are 32 bits long, which simplifies instruction decoding. The 80x86 encoding is variable length, ranging from 1 to 18 bytes. Variable-length instructions can take less space than fixed-length instructions, so a program compiled for the 80x86 is usually smaller than the same program compiled for RISC-V. Note that choices mentioned previously will affect how the instructions are encoded into a binary representation. For example, the number of registers and number of addressing modes both have a significant impact on the size of instructions, because the register field and addressing mode field can appear many times in a single instruction.[^7] |

[^4]: See section [18.2](https://riscv.org/wp-content/uploads/2015/01/riscv-calling.pdf) for more information about RISC-V registers, names, usage, and calling conventions.

[^5]: More [information](https://riscv.org/wp-content/uploads/2017/05/riscv-spec-v2.2.pdf)

[^6]: See [Appendix K](http://acs.pub.ro/~cpop/SMPA/Computer%20Architecture,%20Sixth%20Edition_%20A%20Quantitative%20Approach%20(%20PDFDrive%20).pdf), page 1271.

[^7]: Note that ARMv8 and RISC-V later offered extensions, called Thumb-2 and RV64IC, that provide a mix of 16-bit and 32-bit length instructions, respectively, to reduce program size. Code size for these compact versions of RISC architectures are smaller than that of 80x86.

### Genuine Computer Architecture
The implementation of a computer has two components: organization and hardware. 

The term organization refers to high-level aspects of a computer's design such as the memory system, memory interconnect, and the design of the internal processor or CPU. Ther term *microarchitecture* is also used instead of organization. The switch to multiple processors per microprocessor let to the term *core* also being used for processors. 

Hardware refers to the specifics of a computer, including the detailed logic design and the packaging technology of the computer. Often a line of computers contains computers with identical ISAs and very similar organizations, but they differ in the detailed hardware implementation. 

In this book, the word *architecture* covers ISA, organization or microarchitecture, and hardware.

## 1.4 Trends in Technology
Five implementation technologies, which change at a dramatic pace, are critical to modern implementations:
* *integrated circuit logic technology* - Historically, transistor density increased by about 35% per year, quadrupling somewhat over four years. Increases in die size are less predictable and slower, ranging from 10%-20% per year. The combnied effect was a traditional growth rate in transistor count on a chip of about 40-55% per year, or doubling every 18-24 months. (Popularly known as Moore's Law.) Device speed scales more slowly. Shockingly, Moore's Law is no more. The number of devices per chip is still increasing, but at a decelerating rate. Unlike in the Moore's Law era, we expect the doubling time to be stretched with each new technology generation. 
* *semiconductor DRAM (dynamic random access memory)* - This technology is the foundation of main memory. The growth of DRAM has slowed dramatically, from quadrupling every three years as in the past. The 8 gigabit DRAM was shipping in 2014, but the 16 gigabit DRAM won't reach that state until 2019 [per textbook] and it looks like there will be no 32 gigabit DRAM.[^8]
* *semiconductor flash (electrically erasable programmable read-only memory)* - This nonvolatile semiconductor memory is the standard storage device in PMDs, and its rapidly increasing popularity has fueled its rapid growth rate in capacity. In recent years, the capacity per Flash chip increased by about 50%-60% per year, doubling roughly every 2 years. Currently, Flash memory is 8-10 times cheaper per bit than DRAM.
* *magnetic disk technology* - Prior to 1990, density increased by abuot 30% per year, doubling in three years. It rose to 60% per year thereafter, and increased to 100% per year in 1996. Between 2004-2011 it dropped back to about 40% per year. Recently, disk improvement has sloed to less than 5% per year. One way to increase disk capacity is to add more platters at the same areal density, but there are already seven platters within the one inch depth of the 3.5 inch form factor disks. Ther is room for at most one or two more platters. The last hope for real density increase is to use a small laser on each disk read-write head to heat a 30mm spot to 400°C so that it can be written magnetically before it cools. It is unclear whether Heat Assisted Magnetic Recording can be manufactured economically and reliably, although Seagate announced plans to ship HAMR in limited production in 2018. HAMR is the last chance for continued improvement in areal density of hard disk drives, which are now 8-10 times cheaper per bit than Flash and 200-300 times cheaper per bit than DRAM. This technology is central to server- and warehouse-scale storage. 
* *network technology* - Network performance depends both on the performance of switches and on the performance of the transmission system.

[^8]: Kinam [Kim](https://ieeexplore.ieee.org/document/1609340), 2005