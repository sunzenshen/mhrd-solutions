4-Bit And Specification
=======================

Description:
------------
The AND4B element is a bus version of the AND gate. It applies the And-operation to each pair of bits from both inputs.  


Interface Specification:
------------------------
Inputs: in1[4], in2[4];
Outputs: out[4];


Graphical Representation:
-------------------------
          _______
-in1[4]--|       |
         | AND4B |--out[4]-
-in2[4]--|_______|


Examples:
---------
 in1  | in2  || out
 -------------------
 0000 | 0000 || 0000
 0000 | 0101 || 0000
 0000 | 1010 || 0000
 0000 | 1111 || 0000
 0101 | 0101 || 0101
 0101 | 1010 || 0000
 0101 | 1111 || 0101
 1010 | 1010 || 1010
 1010 | 1111 || 1010
 1111 | 1111 || 1111
