```
Microhard 4-Bit Algorithmic Logic Unit Specification
====================================================

Description:
------------
The ALU4B element has two data bus inputs and an operation code bus input. The element can perform 16 different operations on the data inputs and writes the result to the data bus output. The operation to perform is determined by the value of the operation code bus. Additionally the ALU has flags to indicate whether the final result is zero or negative
Each bit in the operation code bus has a dedicated function:
opCode[4] -> if 1: negate in1 bitwise
opCode[3] -> if 1: negate in2 bitwise
opCode[2] -> if 0: out = (in1 ADD in2); if 1: out = (in1 NAND in2);
opCode[1] -> if 1: negate out bitwise
Through the negation of the inputs and outputs in combination with the application of the add- and nand-functions, a lot of results can be achieved as can be seen in the examples.


Interface Specification:
------------------------
Inputs: in1[4], in2[4], opCode[4];
Outputs: out[4], negative, zero;


Graphical Representation:
-------------------------
          _____
-in1[4]--|     |--out[4]---
         | ALU |--zero-----
-in2[4]--|_____|--negative-
            |
-opCode[4]--/


Examples:
---------
 opCode | in1  | in2  || out  | zero | negative
 ----------------------------------------------
 0000   | 0011 | 0101 || 1000 | 0    | 1        // in1 + in2
 0000   | 0001 | 1111 || 0000 | 1    | 0        // overflow
 0101   | 0011 | 0101 || 0010 | 0    | 0        // in2 - in1
 1001   | 0011 | 0101 || 1110 | 0    | 1        // in1 - in2
 0010   | 0011 | 0101 || 1110 | 0    | 1        // in1 nand in2
 0011   | 0011 | 0101 || 0001 | 0    | 0        // in1 and in2
 1110   | 0011 | 0101 || 0111 | 0    | 0        // in1 or in2
 0101   | 0011 | 0000 || 1101 | 0    | 1        // -in1
 0001   | 1100 | 0000 || 0011 | 0    | 0        // not in1

 ```
