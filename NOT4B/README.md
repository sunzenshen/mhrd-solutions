4-Bit Not Specification
=======================

Description:
------------
The NOT4B element is a bus version of the NOT gate. It applies the Not-operation to every bit in the bus.  


Interface Specification:
------------------------
Inputs: in[4];
Outputs: out[4];


Graphical Representation:
-------------------------
         _______
        |       |
-in[4]--| NOT4B |--out[4]-
        |_______|


Examples:
---------
 in   || out
 ------------
 0000 || 1111
 1111 || 0000
 0101 || 1010
 1010 || 0101
 0110 || 1001
 1001 || 0110
