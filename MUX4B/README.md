```
4-Bit Multiplexer Specification
===============================

Description:
------------
The MUX4B element is a bus version of the MUX gate. It transfers the whole data of one of the input busses to the output bus, but otherwise behaves identically.


Interface Specification:
------------------------
Inputs: in1[4], in2[4], sel;
Outputs: out[4];


Graphical Representation:
-------------------------
          ____
-in1[4]--|    \
         | MUX |--out[4]-
-in2[4]--|____/
           |
-sel-------/


Examples:
---------
 sel | in1  | in2  || out
 -------------------------
 0   | 1010 | 0101 || 1010
 1   | 1010 | 0101 || 0101

```
