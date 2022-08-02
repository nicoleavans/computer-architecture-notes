# Chapter 3 Review Questions
1. Does an architecture that has fixed-length instructions necessarily have only one instruction format? if multiple formats are possible given a single instruction size in bits, explain how they could be implemented; if not, explain why this is not possible.
2. The instruction set architecture for a simple computer must support access to a 64 KB of byte-addressible memory space and eight 16-bit general-purpose CPU registers.
   1. If the computer has three-operand machine language instructions that operate on the contents of two different CPU registers to produce a result that is stored in a third register, how many bits are required in the instruction format for addressing registers?
   2. If all instructions are set to be 16 bits long, how many op codes are available for the three-operand, register operation instructions described above (neglecting, for the moment, any other types of instructions that might be required)?
   3. Now assume (given the same 16-bit instruction size limitation) that, in addition to the instructIons described in (2.1), there are a number of additional two-operand instructions to be implemented, for which one operand must be in a CPU register while the second operand may reside in a main memory location or a register. If possible, detail a scheme that allows for at least register-only instructions of the type described in (2.1) plus at least 10 of these two-operand instructions. (Show how you would lay out the bit fields fo each of the machine language instruction formats.) If this is not possible, explain in detail why not and describe what would have to be done to make it possible to implement the required number and types of machine language instructions.
3. What are the advantages and disadvantages of an instruction set architecture with variable-length instructions?
4. Name and describe the three most common general types (from the standpoint of functionality) of machine instructions found in executable programs for most computer architectures.
5. Given that we wish to specify the location of an operand in memory, how does indirect addressing differ from direct addressing? What are the advantages of indirect addressing, and in what circumstances is it clearly preferable to direct addressing? Are there any disadvantages of using indirect addressing? How is register-indirect addressing different from memory-indirect addressing, and what are the relative advantages and disadvantages of each?
6. Various computer architectures have featured machine instructions that allow the specifiation of three, two, one, ore even zero operands. Explain the trade-offs inherent to the choice of the number of operands per machine instruction. Pick a current or historical computer architecture, find out how many operands it typically specifies per instruction, and explain why you think its architects implemented the instructions the way they did. 
7. Why have load-store architectuers increased in popularity in recent years? (How do their advantages go well with modern architectural design and implementation technologies?) What are some of their less desirable trade-offs compared with memory-register architectures, and why are these not as important as they once were?
8. Discuss the two historically dominant architectural philosphies of CPU design:
   1. Define the acronyms CISC and RISC; and explain the fundamental differences between the two philosophies. 
   2. Name one commercial computer architecture that exemplifies the CISC architectural approach and one other that exemplifies RISC characteristics.
   3. For each of the two architectures you named in (8.2), describe one distinguishing characteristic not present in the other architecture that clearly shows why one is considered a RISC and the other a CISC.
   4. Name and explain one significant advantage of RISC over CISC and one significant advantage of CISC over RISC.
9. Discuss the similarities and differences between the programmer-visible register sets of the 8086, 68000, MIPS, and SPARC architectures. In your opinion, which of these CPU register organizations has the moste desirable qualities and which is least desirable? Give reasons to explain your choices.
10. A circuit is to be built to add two 10-bit numbers x and y plus a carry in. (Bit 9 of each number is the most significant bit \[MSB\], and bit 0 is the least significant bit \{LSB\] }. $c_0$ is the carry in to the LSB position.) The propagation delay of any individual AND or OR gate is 0.4 ns, and the carry and sum functions of each full adder are implemented in sum of products form.
    1.  If the circuit is implemented as a ripple carry adder, how much time will it take to produce a result?
    2.  Given that the carry generate and propagate functions for bit position $i$ are given by $g_i = x_i y_i$ and $p_i = x_i + y_i$, and that each required carry bit $(c_1 ... c_{10})$ is devloped from the least significant carry in 
    $c_0$
    and the approprite 
    $g_i$ 
    and 
    $p_i$
    functions using AND-OR logic, how much time will a carry lookahead adder circuit take to produce a result? (Assume AND gates have a maximum fan-in of 8 and OR gates have a maximum fan-in of 12.)
11. Under what circumstances are carry save adders more efficient than normal binary adders tht take two operands and produce one result? Where, in a typical general purpose CPU, would one be most likely to find carry save adders? 
12. Given two 5-bit, signed, twos complement numbers $x = -6 = 11010_2$ and $y = +5 = 00101_2$, show how their 10-bit product would be computed using Booth's algorithm (you may wish to refer to Figures 3.26, 3.27, and 3.28).
13. Discuss the similarities and differences between scientific notation (used for manual calculations in base 10) and floating-point representations for real numbers used in digital computers.
14. Why was IEEE 754-1985 a significant development in the history of computing, especiallyl in the fields of scientific and engineering applications?
15. In 2008, the IEEE modified standard 754 to allow for "half-precision" 16-bit floating-point numbers. These numbers are stored in similar fashion to the single precision 32-bit numbers but with smaller bit fields. In this case, there is 1 bit for the sign, followed by 5 bits for the exponent (in excess 15 format), and the remaining 10 bits are used for the fractional part of the normalized mantissa. Show how the decimal value +17.875 would be represented in this format.
16. Show how the decimal value -267.5265 would be represented in IEEE 754 single and double precision formats.
17. Consider a simple von Neumann architecture computer like the one discussed in Section 3.3.1 and depicted in Figure 3.34. One of its machine language instructions is an ANDM insturction that reads the contents of a memory location (specified by direct addressing), bitwise ANDs this data with the contents of a specified CPU egister, then stores the result back in that same register. List and describe the sequence of steps that woul dhave to be carried out under the supervision of the processor's control unit in order to implement this instruction.
18. What are the two principal design approaches for the control unit of a CPU? Describe each of them and discuss their advantages and disadvantages. If you were designing a family of high-performance digital signal procesors, which approach would you use, and why? 
19. In a machine with a microprogrammed control unit, why is it important to be able to do branching within the microcode?
20. Given the horizontal control word depicted in Figure 3.41 for our fetch and execute the ANDM instruction using the steps you outlined in question 17.
21. Repeat question 20 using the vertical control word depcted in Figure 3.42.
22. Fill in the blanks with the most appropriate term or concept discussed in this chapter:

________ The portion (bit field) of a machine language instruction that specifies the operation to be done by the CPU.
________ A type of instruction that modifies the machine’s program counter (other than by simply incrementing it).

________ A way of specifying the location of an operand in memory by adding a constant embedded in the instruction 
to the contents of a “pointer” register inside the CPU.

________ These would be characteristic of a stack-based instruction set.

________ This type of architecture typically has instructions that explicitly specify only one operand.

________ A feature of some computer architectures in which 
operate instructions do not have memory operands; 
their operands are found in CPU registers.

________ Machines belonging to this architectural class try to 
bridge the semantic gap by having machine language 
instructions that approximate the functionality of 
high-level language statements.

________ This part of a CPU includes the registers that store 
operands as well as the circuitry that performs 
computations.

________ This type of addition circuit develops all carries in 
logic directly from the inputs rather than waiting for 
them to propagate from less significant bit positions.

________ A structure composed of multiple levels of carry save 
adders, which can be used to efficiently implement 
multiplication.

________ This type of notation stores signed numbers as though 
they were unsigned; it is used to represent exponents 
in some floating-point formats.

________ In IEEE 754 floating-point numbers, a normalized 
mantissa with the leading 1 omitted is called this.
This is the result when the operation 1.0/0.0 is performed on a system with IEEE 754 floating-point 
arithmetic.

________ This holds the currently executing machine language 
instruction so its bits can be decoded and interpreted 
by the control unit.

________ A sequence of microinstructions that fetches or 
executes a machine language instruction, initiates 
exception processing, or carries out some other basic 
machine-level task.

________ A technique used in microprogrammed control unit 
design in which mutually exclusive control signals are 
not encoded into bit fields, thus eliminating the need 
for decoding microinstructions.
This keeps track of the location of the next microword 
to be retrieved from microcode storage.
