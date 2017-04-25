```
4-Bit Counter Specification
===========================

Description:
------------
The COUNTER4B element is similiar to an REGISTER4B, with two differences.
First: For every clock cycle the load flag is 0, the internal value increments.
Second: It has an additional reset input flag. If it is 1 the internal value has to be set to "0000".

Interface Specification:
------------------------
Inputs: in[4], load, reset;
Outputs: out[4];


Graphical Representation:
-------------------------
         ___________
        |           |
-in[4]--| COUNTER4B |--out[4]-
        |___________|
             | |
-----load----/ |
-----reset-----/

Example:
--------
 in   | load | reset || out
 ---------------------------
 0101 | 0    | 0     || 0000
 1010 | 0    | 1     || 0001
 0101 | 1    | 0     || 0000
 1010 | 0    | 0     || 0101
 0110 | 1    | 1     || 0110
 1110 | 1    | 0     || 0000
 0000 | 0    | 0     || 1110
 0000 | 0    | 0     || 1111
 0000 | 0    | 0     || 0000
 0000 | 0    | 0     || 0001

 ```
