```
Instruction Decoder Specification
=================================

Description:
------------
The DECODER is used in the Microhard CPU for decoding instructions. There are two different kinds of instructions.

First, if instr[16] equals "1", then instr[1:15] have to be interpreted as a constant which has to be loaded into the memory register. In this case the "cToM" and "loadM" output has to be set to "1", while the "loadD", "loadA" and "jmpIfZ" outputs have to be "0". In addition the lower 15 bit of the instruction have to be written into "constant".

Second, if instr[16] equals "0", then the decoder has to interpret the rest of the instruction in a more elaborate way:

bit:                         16 15 14 13 12 11 10  9  8  7  6  5  4  3  2  1
instr[1:16]:                  0  d  d  a  b  b  o  o  o  o  j  c  c  c  c  c
                                 \__/  |  \__/  \________/  |  \___________/
instr[14:15] destination    ------/    |   |        |       |        |
instr[13]    operand1       -----------/   |        |       |        |
instr[11:12] operand2       ---------------/        |       |        |
instr[7:10]  operation code ------------------------/       |        |
instr[6]     jump if zero   --------------------------------/        |
instr[1:5]   constant       -----------------------------------------/

In this case the CPU has to perform the operation specified by "operation code" with the operands decoded by "operand1" and "operand2".

The "operation code", the "operand1", the "operand2" and the "jump if zero" bits of the instruction can be directly transfered to the "opCode", "op1", "op2", "jmpIfZ" outputs of the decoder respectively.

As in the other case the lower 15 bit of the instruction have to be written into "constant". Note however, that in this case the CPU has to feed only the 5 lowest "constant" bits to the ALU when using the constant as an operand.

If "operand1" is "0" then the value of the address register is fed to the ALU as operand. Otherwise the "constant" represented by the bits instr[1:5] is fed as first operand.

The destination specifies where the result of the ALU operation has to be saved. While "op1" and "op2" are decoded by the CPU, the "destination" bits of the instruction have to be decoded by the DECODER in regards to the following decoding rules:

destination = 00 -> set loadA, loadM and loadD to 0
destination = 01 -> set loadA to 1 ; set loadM  and loadD to 0
destination = 10 -> set loadM to 1 ; set loadA  and loadD to 0
destination = 11 -> set loadD to 1 ; set loadA  and loadM to 0

Interface Specification:
------------------------
Inputs: instr[16];
Outputs: cToM, loadA, loadD, loadM, op1, op2[2], opCode[4], jmpIfZ, constant[15];


Graphical Representation:
-------------------------
             _________
            |         |--cToM---------
            |         |--loadA----------
            |         |--loadD----------
            |         |--loadM----------
-instr[16]--| Decoder |--op1----------
            |         |--op2[2]-------
            |         |--opCode[4]----
            |         |--jmpIfZ-------
            |_________|--constant[15]-


Examples:
---------
 instr  || cToM | jmpIfZ | loadA | loadD | loadM | op1 | constant | op2 | opCode
 -------------------------------------------------------------------------------
 0x0000 || 0    | 0      | 0     | 0     | 0     | 0   | 0x0000   | 00  | 0000
 0x8000 || 1    | 0      | 0     | 0     | 1     | 0   | 0x0000   | 00  | 0000
 0xFFFF || 1    | 0      | 0     | 0     | 1     | 1   | 0x7FFF   | 11  | 1111
 0x7FFF || 0    | 1      | 0     | 1     | 0     | 1   | 0x7FFF   | 11  | 1111
 0x7C1F || 0    | 0      | 0     | 1     | 0     | 1   | 0x7C1F   | 11  | 0000
 0x7C0F || 0    | 0      | 0     | 1     | 0     | 1   | 0x7C0F   | 11  | 0000

 ```
