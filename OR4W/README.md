4-Way Or Specification
======================

Description:
------------
The OR4W element is a bus version of the OR gate. If at least one of the bits in the bus is 1, the output is 1. Otherwise the output is 0.


Interface Specification:
------------------------
Inputs: in[4];
Outputs: out;


Graphical Representation:
-------------------------
         ______
        |      |
-in[4]--| OR4W |--out-
        |______|


Examples:
---------
 in   || out
 ------------
 0000 || 0
 1111 || 1
 0101 || 1
 1010 || 1
 0110 || 1
 1001 || 1
