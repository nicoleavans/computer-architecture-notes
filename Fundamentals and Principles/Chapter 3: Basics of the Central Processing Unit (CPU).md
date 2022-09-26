# Chapter 3: Basics of the Central Processing Unit
A typical CPU has three major parts: 
* ALU (arithmetic/logic unit) - performs calculations
* internal registers - provide temporary storage for data to be used
* control unit - directs and sequences all operations of the ALU and registers, and the rest of the machine

<p align="center">
<img src="https://i.imgur.com/bkdlAW3.png" width="500">
</p>

The control unit is responsible for carrying out sequential execution of the stored program in memory, a hallmark of the von Neumann architecture, by using the registers and the arithmetic and logical circuits together known as the *datapath*. 

## 3.1 The Instruction Set
The instruction set architecture (ISA) determines how all software must be structured at the machine level. The CPU executes machine language instructions, though most software is now developed in high-level languages. 

### 3.1.1 Machine Language Instructions
Regardless of the high-level language used, in the end a computer program is a sequence of binary machine language instructions to be performed in order. Each machine language instruction is a collection of bits that are decoded by logic inside the processor's control unit. Each combination of bits has a unique meaning to the control unit, telling it to:
* perform an operation on some data
* move data from one place to another
* input or output data to or from a device
* alter the flow of program execution
* or any other task the hardware is capable of doing

Machine language instructions may be fixed or variable in length and are normally divided into 'fields', or groups of bits, each of which is decoded to tell the control unit about a particular aspect of the instruction.
> A simple machine might have 16-bit instructions divided into five fields. This example is taken from the instruction set of DEC's PDP-11 minicomputer of the early 1970s:

<p align="center">
<img src="https://i.imgur.com/ZGHYM3n.png" width="600">
</p>

The first set of bits comprise the *operation code* (*op code*). They define the operation to be carried out. In this case, because there are four op code bits, the computer can have at most
$2^4 = 16$
instructions, assuming this is the only instruction format. The control unit would use a 
$4$
to 
$16$ 
decoder to uniquely identify which operation to perform based on the op code for a particular instruction.

The remaining 12 bits specify two operands to be used with the instruction. Each operand is identified by two 3-bit fields: one to specify a register and one to specify an *addressing mode*. An addressing mode is the way of determining the operand's location given the contents of the register in question. Having three bits to specify a register means that the CPU is limited to having only 
$2^3 = 8$ 
internal registers. (Or, at least, that only eight can be used for the purpose of addressing operands.) Likewise, allocating three bits to identify an addressing mode means there can be no more than eight such modes. 
> One of them might be register direct, meaning the operand is in the specified register. Another might be register indirect, meaning the register contains a pointer to the operand in memory. 

Each of these 3-bit fields will be interpreted by a 
$3$
to
$8$
decoder, the outputs of which will be used by the the control unit in determining the locations of the operands so they can be accesssed. Thus, within the 16 bits of the instruction, the CPU finds all the information it needs. 

A machine may have one or several formats for machine language instructions. Each format may have different-sized bit fields and have different meanings for the fields. Here is an example of an architecture with fixed-length, 32-bit instructions with three formats:

<p align="center">
<img src="https://i.imgur.com/vldBtWE.png" width="600">
</p>

Notice how the two leftmost bits are used to identify the format of the remaining 30 bits. This would correspond to a two-level decoding scheme in which the outputs of a
$2$
to
$4$
decoder driven by the two format bits would determine which set of secondary decoders would be used to interpret the remaining bits. This type of arrangement makes the contorl unit more complex but allows the machine to have a greater variety of instructions.

Because the types of instructions and number of operands for each sometimes varies, it is often more space efficient to encode some types of instructions in fewer bits while others take up more bits. Having instructions of variable lengths complicates the process of fetching and decoding instructions, but may be justified if keeping the executable code size small is important. Here is an example of an instruction set with some 16-bit instructions and some 32-bit instructions: 

<p align="center">
<img src="https://i.imgur.com/zD0SNEy.png" width="600">
</p>

One particular op code (111111)from the shorter format is used to tell the CPU that the next 16 bits are to be interpreted as the second part of the current instruction rather than the next instruction.

### 3.1.2 Functional Categories of Instructions
Instruction set architecture tends to fall into, or between, two categories:
* reduced instruction set computers (RISCs)
* complex instruction set computers (CISCs)

While computer ISAs vary widely, there is much commonality between the instruction sets of almost every Princeton or Harvard architecture machine. The major classifications are:

| Classification | Description | Assembly Language Mneumonics |
| -------------- | ----------- | ----------- |
| *data transfer instructions* | The most common instructions found in computer programs. To help operations proceed quickly, we like to work with operands in the processor's internal registers.[^1] There are limited registers available, so programs spend much of their time moving data to get values where they are needed and store them back in memory when they are no longer needed. Instructions of this type include transfers from one internal register to another, from main memory to a register, or from a register to a memory location. | MOVE, LOAD, STORE, XCHG, PUSH, POP, etc. |
| *computational instructions* | Usually the second most numerous type in a program. These are instructions that perform manipluations (arithmetic, logical, shift, etc.) of data. All of these instructions, reglardless of the specific operation, involve passing binary data through the processor's functional hardware (usually called the ALU) and using some combination of logic gates to operate on it to produce a result. In most cases, a set of condition codes or flags that indicate the nature of the result are also produced, such as positive/negative, zero/nonzero, overflow/no overflow, etc. | ADD, SUB, MUL, AND, OR, NOT, SHL, SHR, etc. |
| *control transfer instructions* | Usually the third most frequent type. These are the instructions that allow the normally sequential flow of execution to be altered, either unconditionally or conditionally. When a transfer of control occurs, the processor goes to a new location in memory (specified as an absolute binary address or relative to the location of the current instruction) and continues executing code at that location. Control transfer instructions allow programs to be logically organized in small blocks of code (procedures, functions, methods, etc.) that can call or be called by other blocks of code. This makes programs easier to understand and modify than if they were written as huge blocks. Conditional control transfer instructions allow programs to make decisions based on input and the results of prior calculations. They enable high-level control structures like if/else statements, loops, etc., to be implemented at machine level. | JMP, BNZ, BGT, JSR, CALL, RET, etc. |

There are other, less commonly used instruction types such as *input/output system* and *miscellaneous instructions*. Not all architectures have a distinct category of I/O instructions; they are only present on machines that employ *separate I/O* rather than *memory-mapped I/O*. Machines with memory-mapped I/O use regular memory data transfer intructions to move data to or from I/O ports. 

System instructions are special operations involving management of the processor and its operating environment. As such, they are often *priviledged* instructions that can only be executed when the system is in 'supervisor' or 'system' mode (in which the OS runs). Attempts by user code to execute such instructions would then result in an *exception* alerting the OS of the privilege violation. System instructions include functions such as:
* virtual memory management
* enabling and freezing the cache
* masking and unmasking interrupts
* halting the system

Such tasks need to be done in many systems, but not all programs should be allowed to do them.

Most systems have a few instructions that cannot be easily categorized. This may be because they perform some special function unique to a given architecture or because they perform no function at all. These are miscellaneous instructions. Perhaps the most ubiquitous of these instructions is NOP, or no operation, which is used to kill time while the processor waits for other hardware or a human user. 

What differs considerably from one architecture to another is how many, and which, instructions of each type are provided. Some architectures have very rich instruction sets with specific machine instructions for just about every task a programmer would want to accomplish, and others have a minimalist instruction set with complex operations left to be accomplished in software by combining several machine instructions.
> The Motorola 68000 has machine instructions to perform signed and unsigned integer multiplication and division. The original SPARC architecture provided only basic building blocks, such as addition, subtraction, and shifting operations. This left multiplication and division to be implemented as library subroutines.[^2]

Hardware and software are equivalent and interchangeable. The only machine instructions that are required to do all computations are:
* either a NAND or NOR[^3]
* some method for transferring data from one place to another
* some way of performing a conditional transfer of control (the condition can be forced to true to allow unconditional transfers)

One or two shift instructions would be nice, but we could probably get by without them if we had to. Once these most basic, required hardware capabilities are in place, the amount of additional functionality that is provided by hardware vs. software is up to the designer.

### 3.1.3 Instruction Addressing Modes
Machine instructions often need to access operands. These operands may reside in CPU registers or main memory locations. In order to perform the desired operation, the processor must be able to locate the operands. The way that a machine instruction specifies the location of an operand is referred to as an *addressing mode*. 

*Immediate addressing* embeds an operand into the machine language instruction itself:

<p align="center">
<img src="https://i.imgur.com/rIR5arY.png" width="600">
</p>

In other words, one of the bit fields of the instruction contains the binary value to be operated upon. The operand is available immediately because the operand fetch phase of the instruction execution is done concurrently with the first phase, instruction fetch. 

This type of addressing is good for quick access to constants that are known when the program is written. It is not useful for access to variables. It's also costly in terms of instruction set design because the constant takes up bits in the machine language instruction format that could be used for other things. The size of the instruction may have to be increased to accomodate a reasonable range of immediate constants, or the range of values that may be encoded must be restricted to fit within the constraints imposed by instruction size and the need to have bit fields for other purposes. Still, almost all computer ISAs include some form of immediate addressing.

*Direct addressing* (or, *absolute addressing*) refers to a mode where the location of the operand (specifically, its address in main memory) is given explicitly in the instruction.

<p align="center">
<img src="https://i.imgur.com/TLriOTe.png" width="600">
</p>

Operand access using direct addressing is slower than using immediate addressing because the information obtained by fetching the instruction does not include the operand itself, only its address. An additional memory access must be made to read or write the operand. 
> Because the operand resides in memory rather than in the instruction itself, it is not read-only, as is normally the case with immediate addressing.

Direct addressing has some of the same limitations as immediate addressing. The memory address embedded in the instruction takes up some number of bits, quite a few if the machine has a large addressing range. This requires the instruction format to be large or limits the range of locations that can be accessed using this mode. Direct addressing is useful for referencing scalar variables but has limited utility for strings, arrays, and other data structures that take up multiple memory locations.

*Register addressing* (or register direct addressing), where the operand resides in a CPU register, is logically equivalent to direct addressing because it also explicitly specifies the operand's location. The principle advantage of register addressing is quick access to the operand as there is no need to read or write memory. However, the number of registers accessible to the program is limited. One common optimization is placing the most frequently accessed variables in registers, while those that are referenced less often reside in memory. 

*Indirect addressing* is one logical step further from specifying the operand. Rather than the instruction containing the operand itself or the operand address, it contains the specification of a pointer to the operand. The pointer to the operand can be found in a specified register, or in some architectures, in a specified memory location. 

The principle advantages of indirect addressing are:
* the value of the operand can be changed ar run time (making it a variable rather than constant)
* because it resides in a modifiable register or memory location, the address of the operand can be modified on the fly. 

This means that indirect addressing readily lends itself to the processing of arrays, strings, or any type of data structure stored in contiguous memory locations. By incrementing or decrementing the pointer by the size of an individual element, one can readily access the next or previous element in the structure. This coding structure can be placed inside a loop for convenient processing of the entire data structure.

The only major drawback of indirect addressing is that determining the operand's address takes time. The CPU must locate the pointer, obtain its contents, and then use those contents as the addres for reading or writing the operand. If the pointer is in a memory location, then the memory must be accessed at least three times:
1. read the instruction
2. read the pointer
3. read or write the data

If the operand is both a source of data and the destination of the result, a fourth access would be needed. This is slow and tends to complicate the design of the control unit. For this reason, many architetures implement indirect addressing only as register indirect, requiring pointers to be loaded into registers before use. 

*Indexed addressing*, also known as displacement addressing, works similarly to register indirect addressing but has the additional feature of a second, constant value embedded in the instruction that is added to the contents of the pointer register to form the effective address of the operand in memory.

<p align="center">
<img src="https://i.imgur.com/UNfOSps.png" width="600">
</p>

> One common use of this mode involves encoding the starting address of an array as the constant displacement and using the register to hold the array index or offset of the particular element being processed. [^4]

Most computer architectures provide at least a basic form of indexed addressing. Some also have more complex implementations in which the operand address is calculated as the sum of the contents of two or more registers, possibly in addition to a constant displacement.
> One example is the *based index* addressing mode built into the Intel x86 architecture.

Such a mode, if provided, complicates the design of the processor somewhat but provides a way for the assembly language programmer or compiler to easily access elements of two-dimensional arrays or matrices stored in memory. 

*Program counter relative addressing* is used in many computer architectures for handling control transfers, such as conditional branches and subroutine calls. The idea is that an offset (usually signed to allow forward or backward branching) is added to the current program counter (PC) value to form the destination address. This value is copied back to the PC, effectively transferring control to that address.

<p align="center">
<img src="https://i.imgur.com/87Z3ld8.png" width="600">
</p>

The advantage of using PC relative addressing, rather than specifying an absolute address as a destination, is that the resulting code is position independent. It can be loaded anywhere in memory and still execute properly. The absolute address of a called routine or branch target may have changed, but it is still in the same place relative to the instruction that transfers control to it. For this reason, most computer architectures provide at least some subset of control transfer instructions that operate this way. 
> Some architectures such as the Motorola 680x0 family also implement PC relative addressing for instructions that access memory for operands. In this way, blocks of data can be relocated along with code in memory and still appear to the program logic to be in the same place.

*Stack addressing* involves references to a last-in, first-out (LIFO) data structure in memory. Nearly all architectures have 'push' and 'pop' instructions that facilitate storing and retrieving items on and off a stack in memory. These instructions use a given register as a stack pointer to identify the current 'top of stack' location in memory, automatically decrementing or incrementing the pointer as items are pushed or popped. Most architectures only use stack addressing for data transfers, but some machines have computational instructios that retrieve an operand(s) and store a result on a memory stack. This approach has the same problems of complexity and the sluggishness that are inherent to any manipulation of data in memory, but it does reduce the need for CPU registers to hold operands.

### 3.1.4 Number of Operands per Instruction
One of the most significant choices made in the development of a computer architecture is the determination of how many operands each instruction will take. This decision is important because it balances ease of programming against the size of machine instructions. Simply put, the more operands an instruction accesses, the more bits are required to specify the locations of those operands.

From a programming POV, the ideal number of operands per instruction is probably three. Most arithmetic and logical operations (including addition, subtraction, multiplication, logical AND, OR, NAND, NOR, XOR, etc.) take two source operands and produce one result (or destination operand). For complete flexibility, one would like to be able to independently specify the locations (in registers or memory) of both source operands and the destination. Many architectures do not implement *three-operand instructions* due to the complexity of instructions (especially if some or all of the operands can be in memory locations) and the need ofr larger machine language instructions to have enough bits to locate all the operands. 

Many architectures have adopted the compromise of *two-operand instructions* This maintains a reasonable degree of flexibility while keeping the instructions somewhat shorter than they would be with three operands. The rationale is that many frequently used operations (such as negation of a signed number, logical NOT, etc.) require only two operands anyway. When two source operands are needed, one of them can double as a destination operand, being overwritten by the result of the operation. In many cases, at least one of the operands is only an intermediate result and may be safely discarded. If it is necesssary to preserve its value, one extra data transfer instruction will be required prior to the operation. If the architects determine that na occasional extra data transfer is worth the savings in cost and complexity from having only two operands per instruction, then this is a reasonable approach.

*One-operand instructions* were once fairly common but are not seen in many contemporary architectures. In order for a single operand specification to be workable for operations that require two source operands, the other operand must reside in a known location. This is typically a special register in the CPU called the *accumulator*. The accumulator normally provides one of the operands for every arithmetic and logical operation while also receiving the result. Thus, the only operand that must be located is the second source operand. This is a simple model that was popular when processors could have few internal registers. Because a single register is involved in every computational instruction, the program must spend a lot of time moving operands into, and results out of, that register. The resulting 'accumulator bottleneck' tends to limit performance. Accumulator-based architectures are rarely found outside of embedded control processors where simplicity and low cost are more important than speed.

*Zero-operand instructions* could be used in a machine with *stack architecture*. A limited number of architectures have used this approach, which keeps machine instructions as simple and short as possible (only the op code). Compiler design is also simplified because a stack architecture dispenses with the issue of register allocation. However, stack architectures are slower because operands must be feteched from and stored back to memory for each computation. Thus, stack architectures are even less common than accumulator architectures.

### 3.1.5 Memory-Register vs. Load-Store Architectures
Most modern CPUs are designed around a set of several (8, 16, 32, +) general-purpose internal registers due to the limitations of stack and accumulator-based architectures. This allows at least some operands used in computations to be available without the need for a memory accesss. An important question to be answered by the designer of an instruction set is:
> Do we merely want to *allow* the programmer (or compiler) to use register operands in computations, or will we *require* all computations to use register operands only?

#### 3.1.3.1 Memory-Register

* A *memory-register* architecture is one in which many, if not all, computations may be performed using data in memory and in registers. (Ex. Intel x86 and Motorola 680x0)

* A *memory-memory* architecture allows all of an instruction's operands to be in memory location. 

The advantages of these architectures are:
* assembly language coding is simplified
* all of the machine's addressing modes are available to identify an operand for any instruction
* computational instructions such as ADD behave just like data transfer instructions like MOV. 
* the assembly language programmer and high-level language compiler have a lot of flexibility in how they perform tasks
* executable code size tends to be smaller[^5]

The disadvantages of a memory-register architecture (further exacerbated with memory-memory architecture):
* makes control unit design more complex
  * any instruction may need to access memory one, two, three, or even four times before it is completed
  * this complexity can be handled by a *microprogrammed* design, for a speed penalty
  * instructions with a variable number of memory operands must either be variable in length (complicating the fetch/decode process) or all must be the size of the longest instruction (wasting bits and making programs take up more memory) because the number of bits required to specify a memory location is generally much greater than the number required to specify a register.
  * the more memory accesses an instruction requires, the more clock cycles it will take to execute. Ideally, we would like instructions to take as few clock cycles as possible and all of them to execute in the same number of clock cycles, if possible. 

Variability in the number of clock cycles per instruction makes it more difficult to *pipeline* instruction execution, critical for CPU performance. 

#### 3.1.3.2 Load-Store 
The alternative is known as a *load-store* architecture. (Ex. MIPS and SPARC). In a load-store architecture, only the data transfer instructions (typically named 'load' for reading data from memory and 'store for writing data to memory) are able to access variables in memory. **All arithmetic and logic instructions operate only on data in registers**; leaving results in registers. 

Advantages:
* instructions can be smaller and consistent in size because register addressing require smaller bit fields
* three-operand instructions are practical
* control logic is less complex and can be implemented in *hardwired* fashion which may result in a shorter CPU clock cycle. This simplicity is due to computational instructions requiring one data access and data transfer instructions requiring two data accesses. 
* arithmetic and logic instructions are simple to pipeline; because data memory accesses are done independently of computations, they do not interfere with pipelining as much as they otherwise might.

Disdvantages: 
* assembly language programming more complex
* programs tend to require more machine instructions to perform (since all data instructions are separate)
* more registers must be provided because all operands must be in registers. more registers are more difficult to manage an dmore time-consuming to save and restore when necessary.

Load-store architectures are becoming increasingly popular.

### 3.1.6 CISC and RISC Instruction Sets
CISC architectures were dominant in the 1960s and 1970s; some have survived well into today (Intel x86). 

CISCs tended to have machine language instruction sets reminiscent of high-level languages. They generally had many different machine instructions, and individual instructions often carried out relatively complex tasks. CISC machines usually had a wide variety of addressing modes to specify operands in memory or registers. To support many different types of instructions while keeping code size small (an important consideration given price of memory at that time), CISC architectures often had variable-length instructions. This complicated control unit design, but by using microcode, designers were able to implement complex control logic without overly extending the time and effort required to design a processor. 
> The philosophy underlying CISC was to support high-level language by 'bridging the semantic gap', or, by making the assembly and machine language look as much like a high-level language as possible. 

RISC architectures gained favor in the 1980s and 1990s as it became more difficult to extract increased performance from complicated CISC processors. The big, slow microprogrammed control units characteristic of CISC machines limited CPU clock speeds, and thus performance. CISCs had instructions that could do a lot, but took time. The RISC approach was not only to have fewer distinct machine language instructions but for each instruction to do less work.

Instruction sets were designed around the load-store philosophy, with all instruction formats kept to the same length to simplify the fetching and decoding process. Only instructions and addressing modes that contributed to overall performance were included; all extraneous logic was stripped away to make the control unit lighter and faster. 

The most meaningful performance metric was the overall time taken to run one's specific program of interest. The less time it takes a system to execute the code to perform that task, the better. We can break down the time it takes to run a given program (in the absence of interrupts) as:

$$
\frac{\mathrm{time}}{\mathrm{program}} = \frac{\mathrm{instructions}}{\mathrm{program}} \times \frac{\mathrm{clock \ cycles}}{\mathrm{instruction}} \times \frac{\mathrm{seconds}}{\mathrm{clock \ cycle}}
$$

In order to reduce the overall time taken to execute a given piece of code, we need to make at least one of the three terms on the right side of the equation smaller, and do so without causing a greater increase in any of the others. CISC machines address this performance equation by trying to minimize the first term in the equation: the number of machine instructions required to carry out a given task. By providing more functionality per instruction, programs are kept smaller. All else being equal, they should thus execute faster. 

The very techniques used to cram more functionality into each machine instruction hindered designer's ability to do anything about the remaining terms in the equation. Complex instructions generally took several clock cycles to execute, and because of the long propagation delays through the control unit and datapath, it proved difficult to increase CPU clock frequencies. (The rightmost term in the equation is the reciprocal of clock frequency.)

With CISC performance stagnating, RISC architects adoted a very different approach. Making individual instructions simpler meant it would take more of them to do the same amount of work, and programs would be larger. However, if this allows the resulting implementation to be streamlined (preferably pipelined), then it may be possible for us to minimize both the number of clock cycles per instruction and the clock cycle time. Gradually RISC processors showed they could outperform their CISC counterparts. 

The main impetus for RISC came from studies of high-level language code compiled for CISC machines. Researchers found that the 80/20 rule was in effect: Roughly 20% of the instructions were doing 80% or more of the work. Many machine instructions were too complex for compilers to find a way to use them, so they never appeared in compiled programs at all. Expert assembly language programmers loved to use such instructions to optimize their code, but the RISC pioneers recognized that in the future, assembly language would be used less and less for serious program development. Their real concern was optimizing system performance while running applications compiled from high-level code. Compilers were not taking full advantage of feature-rich CISC instruction sets, even as these instructions slowed down everything else. [^6]

Thus, RISC designers opted to keep only 20% of instructions. The few remaining needed operations could be synthesized by combining multiple RISC instructions to do the work of one seldom-used CISC instruction. RISC architectures required more effort to develop good, efficient, optimizing compilers, and the compiling process itself generally took longer. But a compiler must only be written once, and a given program must only be compiled one time once it is written and debugged, though it will likely run on a given CPU many times. Trading off incrased compiler complexity for reduced CPU complexity seemed like a good idea.

Two other factors in the rise of RISC:
* VLSI techniques
* development of programming languages for hardware design

With the availability of more standardized VLSI logic design elements, such as programmable logic arrays, computer engineers could avoid the haphazard, time-consuming, and error-prone process of designing chips with random logic. This made hard-wired control much more feasible than it had been previously. *Hardware description languages* (HDLs) were devised to allow a software development methodology to be used to design hardware. This negated one of the major advantages previously enjoyed by microprogrammed control unit design.

The reduced number and function of available machine instructions, along with the absence of variable-length instructions, meant RISC programs required more instructions and took up more memory for program code than would a similar CISC program. However, if the simplicity of the control unit and arithmetic hardware were such that the processor's clock speed could be significantly higher and if instructions could be completed in fewer clock cycles, the end result could be a net increase in performance. This benefit, coupled with falling prices for memory over the years, has made RISC architectures more attractive, especially for high-performance machines. Many of the latest architectures borrow features from both RISC and CISC machines.

## 3.2 The Datapath
The *datapath* is the hardware that is used to carry out the instructions. Regardless of the number or type of instructions provided or the philosophy underlying the instruction set design, any CPU needs circuitry to store binary numbers and perform arithmetic and logical operations on them. 

### 3.2.1 The Register Set
A machine's programmer-visible *register set* is the most obvious feature of its datapath because the register set is intertwined with the ISA. The visible register set is an architectural feature, and the particulars of the rest of the datapath are merely implementation details. 
> One machine may have two 64-bit ALUs and another may have a single 32-bit ALU that requires two passes to perform 64-bit operations, but if their register sets (and instruction sets) are the same, they will appear architecturally identical. The only difference will be in observed performance. 

Registers do very litter other than serve as temporary storage for data and addresses. [^7] The fact that registers are explicitly referred to by program instructions that operate on data makes the register set one of the most important architectural features of a given machine.

The most signifiant attributes of a machine's register set are:
* size (number of registers and width in bits of each)
* logical organization

Assembly programmers like to have many registers, the more the better. Compilers were once inefficient at using a large register set but have become better at this over the years. However, for both compilers and programmers, there is a diminishing returns effect beyond some optimal number of registers. The number and size of CPU registers was once limited by power consumption and silicon 'real estate'. Now, the determining factors of the number of registers provided are more likely to be:
* the desired instruction length (more registers means bigger operand fields)
* the overhead required to save and restore registers on an interrupt or context switch
* the desire to maintain compatibility with other machines
* the compiler's ability to make efficient use of the registers

The size of individual registers depends on the numerical precision required and the word width of the computational hardware. 
> It makes little sense to store 128-bit numbers if the ALU is only 32 bits wide, of if the machine's intended applications do not require 128-bit precision.

Because most architectures allow some form of register-indirect or indexed addressing, register size also depends on the amount of memory the architects want to make addressable by a program. 
> For example, 16-bit registers allow only 64KB of address space (without resorting to trickery such as the segment registers in the Intel 8086, which allowed 20-bit addresses to be formed from two 16-bit values); 32-bit registers allow for 4GB of addressable space, which used to be considered plenty but has proven insufficient. The next logical step, addressing with 64-bit registers, allows 
> $2^{64}$
> bytes of virtual and perhaps one day physical space to be addressed. 

Most contemporary machines could have more (and larger) registers than they do, but designers have found other, more profitable ways to use the available chip area.

Whatever the size of the register set, logical organization is significant. Designers have taken different approaches to allocating registers for different uses. 
> Some architectures, such as Intel 8086, had special-purpose register sets in which specific registers wre used for specific functions. Multiplication results were always left in the AX and DX registers, and CX was always used to count loop iterations. Others, like Motorola 68000, divide the working registers into two categories of data registers and address registers. All data registers are equal, with the ability to provide operands for and receive results from any of the arithmetic and logical instructions. Address registers only have the capability for simple pointer arithmetic, but any of them can be used with any of the available addressing modes. Some architectures, like VAX and MIPS, make few if any distinctions in terms of functionality and allow any CPU register to be used equally in any operation. SPARC processor's general purpose registers may be used interchangeably for data or addresses, but are logically grouped by scope based on whether they represent:
> * global variables
> * local variables within a given procedure
> * inputs passed to it from a caller
> * outputs from it to a called subprogram

Whatever the design of a machine's register set, compilers must be designed to be aware of its features and limitations in order to exploit the full performance potential. This is particularly true of RISCs or any machine with a load-store ISA. 

### 3.2.2 Integer Arithmetic Hardware

An elementary ALU (arithmetic/logic unit) can perform addition and subtraction on binary operands as well as some subset of standard, bitwise logic functions (such as AND, OR, NOT, NAND, NOR, XOR, etc.) It may also proide the ability to do bit shifting operations. See a block diagram of a typical ALU:

<p align="center">
<img src="https://i.imgur.com/kcgdauQ.png" width="600">
</p>

The control inputs are used to select which arithmetic or logical function the ALU and shifter perform at any given time. One of the ALU functions may be to simply transfer one of the operand inputs to the output without modifications; allowing the shifter to operate directly on register contents and provides for simple register-to-register transfers via the datapath.

The shifter can pass bits through unchanged, or move them left or right. In the case of a barrel shifter, it can move them many positions left or right. 

The ALU typically develops 'condition codes', or status bits that indicate the nature of the result produced (positive/negative, zero/nonzero, overflow or carry). The bitwise logical functions of the ALU are trivial to implement, requiring only a single gate of each desired type per operand bit. Shifting is not much more complex. The complexity of the datapath is in the circuitry that performs arithmetic caluclations.

#### 3.2.2.1 Addition and Subtraction
Addition and subtraction are the most frequently performed operation in most applications. Thus, it is worthwhile to consider implementations that improve performance at a cost. The *half adder* and *full adder* circuits are the building blocks for performing addition of binary numbers in computers.

<font color="aquamarine">
Half Adder:
</font>

<p></p>

<p align="center">
<img src="https://i.imgur.com/oErgOE9.png" width="450">
</p>

<font color="aquamarine">
Full Adder:
</font>

<p></p>

<p align="center">
<img src="https://i.imgur.com/QM1TFrj.png" width="550">
</p>

The half adder is normally useful only for adding the least significant bits 
$a_0$
and
$b_0$
of two binary numbers, as it has no carry in. It adds two one bit numbers (
$a_0$
and
$b_0$
) and produces a sum bit
$s_0$
and a carry out bit
$c_1$
. 

The full adder circuit is useful for adding the bits (in any position) of two binary numbers. The corresponding bits of the two numbers
$a_i$
and
$b_i$ are added to an input carry 
$c_i$
to form a sum bit 
$s_i$
and a carry out bit 
$c_{i+1}$
. Any number of full adders can be cascaded together by connecting the carry out of each less significant position to the carry in of the next more significant position to create the classic *ripple carry adder*:

<p align="center">
<img src="https://i.imgur.com/Q6akUET.png" width="550">
</p>

The operation of this circuit is like adding binary numbers by hand. However, because carries must propagate through the entire chain of adders before the final result is obtained, this structure may be intolerably slow for adding large binary numbers.

It is possible to design half and full subtractor circuits in a similar manner, and those can be cascaded in the same fashion to form a *ripple borrow subtractor*. In practice, separate circuits are rarely built to implement subtraction. Instead, signed arithmetic is used, with subtraction being replaced b the addition of the complement of the subtrahend[^8] to the minuend[^9]. The adder can perform as both adder and subtractor.

<font color="aquamarine">
Combination Adder Subtractor:
</font>

<p></p>

<p align="center">
<img src="https://i.imgur.com/FBnDuY9.png" width="650">
</p>

| Input | Carry In | XNOR output | produces |
| ----- | -------- | ---- | ---- |
| $S=0$ | $C_n=0$ | corresponding bit of $B$ | $A+B$ |
| $S=1$ | $C_n=1$ | complement of the corresponding bit of $B$ | $A+(-B)$ |

The *carry lookahead adder* is faster in terms of computation speed than a ripple carry adder. The concept here is that the bits of the operands (available at the start of computation) contain all the information required to determine all the carries at once. There is no need to wait for carries to ripple through the less significant stages, they can be generated directly from inputs. 

<font color="aquamarine">
Carry Lookahead Adder:
</font>

<p></p>

<p align="center">
<img src="https://i.imgur.com/0aw7QPW.png" width="650">
</p>

The carry logic of this circuit is based on the fact that when we add two binary numbers, there are always two ways that a carry from one position to the next can be caused. 

> First, if either of the operand bits 
$a_i$
or
$b_i$
are 
$1$
and its carry in bit
$c_i$ is also 

| if | and | then |
| -- | --- | ---- | 
| $a_i$ or $b_i =1$ | 

[^1]: Some architectures, particularly RISCs, require this.

[^2]: The more recent UltraSPARC, or SPARC v9, architecture does provide for built-in multiply and divide instructions.

[^3]: These two are the only universal logic functions from which all other Boolean functions can be derived. 

[^4]: Hence the name, indexed addressing. 

[^5]: A given program can contain fewer instructions because the need to move values from memory into registers before performing computations is reduced (or eliminated if both operands can reside in memory).

[^6]: The CPU clock is limited by the slowest logical pat that must be traversed in a cycle.

[^7]: It is possible to implement the programmer's working registers as shift registers rather than as basic storage registers, but for speed and simplicity, the shifting capability is usually located further down the datapath either as part of or following the ALU.

[^8]: subtrahend: a quantity or number to be subtracted from another

[^9]: minuend: a quantity or number from which another is subtracted
