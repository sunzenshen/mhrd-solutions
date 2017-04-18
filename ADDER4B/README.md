```
4-Bit Adder Specification
=========================

Description:
------------
The ADDER4B is a 4-bit bus version of the FULLADDER. It has therefore two 4-bit input busses and one 4-bit output bus while the carry in and out bits are kept.
Check the appendix in the manual for binary notation of numbers and binary arithmetics.


Interface Specification:
------------------------
Inputs: carryIn, in1[4], in2[4];
Outputs: out[4], carryOut;


Graphical Representation:
-------------------------
-carryIn----\
          __|____
-in1[4]--|       |
         | ADD4B |--out[4]-
-in2[4]--|_______|
              |
              \--carryOut--

Examples:
---------
 carryIn | in1  | in2  || out  | carryOut
 ----------------------------------------
 0       | 0000 | 0000 || 0000 | 0
 0       | 0101 | 0101 || 1010 | 0
 0       | 1010 | 1010 || 0100 | 1
 0       | 1111 | 1111 || 1110 | 1
 1       | 0000 | 0000 || 0001 | 0
 1       | 0101 | 0101 || 1011 | 0
 1       | 1010 | 1010 || 0101 | 1
 1       | 1111 | 1111 || 1111 | 1

```
