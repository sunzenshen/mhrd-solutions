```
Microhard Central Processing Unit Specification
===============================================

Description:
------------
On a high level the Microhard CPU is able to perform a wide variety of instructions similar to the Microhard ALU. However while the ALU is only capable of executing single arithmetic instructions, the CPU is able to execute complex programs composed of many instructions by managing the program execution flow.


Interface Specification:
------------------------
Inputs: instr[16], data[16], reset;
Outputs: write, dataAddr[16], instrAddr[16], result[16];


Graphical Representation:
-------------------------
             _____
-instr[16]--|     |--instrAddr[16]-
            |     |
--data[16]--| CPU |--dataAddr[16]--
            |     |--result[16]----
            |_____|--write---------
               |
-------reset---/


User Instructions:
------------------
To execute a program the CPU needs to be connected to a RAM element containing the instructions of the program and a second RAM element containing all data which should be processed.

The program RAM element has to be connected to the CPU via the "instr" and "instrAddr" busses. The "in" bus and the "load" input of the RAM is supposed to be disconnected.

The data RAM element has to be connected to the CPU via the "data" and "dataAddr" busses. The "in" bus of the RAM has to be connected to the "result" output of the CPU and the "load" input of the RAM has to be connected to the "write" output of the CPU.

To start the program, the reset pin has to be supplied with the value "1" for a single clock cycle to make sure the program is executed from the beginning.


Implementation Details:
-----------------------
The CPU contains (among other elements) two registers, one counter and one ALU:
- the Arithmetic-Register (AR) is used to temporarily store computation results
- the Memory-Register (MR) is used to reference addresses in the connected data
  RAM
- the Program-Counter (PC) is used to reference addresses in the connected
  instruction RAM
- the ALU is used to perform arithmetic operations

This specification will refer to the elements as AR, MR, PC and ALU.


Behavioral Specification:
-------------------------
After the instruction has been decoded by the DECODER (see the DECODER specification for details), the CPU uses the DECODER outputs to ensure following behavior:

- If the "cToM" and "loadM" output of the decoder is "1", the "constant" output
  has to be loaded into the MR.
- If "loadM" is "1" and "cToM" is "0", the result of the ALU operation has to be
  loaded into the MR.
- If "loadA" is "1", the result of the ALU operation has to be loaded into the
  AR.
- The "write" output of the CPU has to have the same value as the "loadD" output
  of the DECODER.
- The "opCode" output of the DECODER has to be directly fed into the ALU.
- If the "op1" output of the DECODER is "1", the "constant" has to be fed in to
  the ALU as the first operand. Otherwise the AR has to be fed into the ALU.
- For the "op2" output of the DECODER:
  "00" -> feed "constant" as second operator into the ALU
  "01" -> feed AR as second operator into the ALU
  "10" -> feed MR as second operator into the ALU
  "11" -> feed data bus as second operator into the ALU
- When feeding "constant" as an operand to the ALU, only the lowest 5 bits of "constant" are used. This 5 bit value is padded to 16 bit in accordance to the sign of the value.
- If "jmpIfZ" and the "zero" flag of the ALU is "1", load the value of the MR
  into the PC.
- Write the ALU output on the "result" bus.
- Write the MR value on the "dataAddr" bus.
- Write the PC value on the "instrAddr" bus.
- Set the PC to "0" if the "reset" input is set.


Examples:
---------
 instr  | data   | reset || instrAddr | dataAddr | result  | write
 -----------------------------------------------------------------
 // result = const + AR = ? (unknown register states):
 0x0000 | 0x0000 | 0     || x         | x        | x       | 0
 // reset program counter:
 0x0000 | 0x0000 | 1     || x         | x        | x       | 0
 // load 0x00FF into MR:
 0x80FF | 0x0000 | 0     || 0x0000    | x        | x       | 0
 // AR = const + data = 1 + 0 = 1:
 0x3C01 | 0x0000 | 0     || 0x0001    | 0x00FF   | 0x0001  | 0
 // result = AR + const = 1:
 0x0000 | 0x0000 | 0     || 0x0002    | 0x00FF   | 0x0001  | 0
 // MR = AR + const = 1:
 0x4000 | 0x0000 | 0     || 0x0003    | 0x00FF   | 0x0001  | 0
 // data = const + MR = 1:
 0x7800 | 0x0000 | 0     || 0x0004    | 0x0001   | 0x0001  | 1
 // load MR into PC:
 0x1020 | 0x0001 | 0     || 0x0005    | 0x0001   | 0x0000  | 0
 // no operation:
 0x1000 | 0x0001 | 0     || 0x0001    | 0x0001   | 0x0000  | 0
 // no operation:
 0x1000 | 0x0001 | 0     || 0x0002    | 0x0001   | 0x0000  | 0

 ```
