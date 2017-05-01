```
4-Bit Register Specification
============================

Description:
------------
The REGISTER4B is a bus version of the REGISTER element.

Interface Specification:
------------------------
Inputs: in[4], load;
Outputs: out[4];


Graphical Representation:
-------------------------
         _______
        |       |
-in[4]--| REG4B |--out[4]-
        |_______|
            |
-----load---/


Example:
--------
 in   | load || out
 -------------------
 0101 | 0    || 0000
 1010 | 0    || 0000
 0101 | 1    || 0000
 1010 | 0    || 0101
 1111 | 1    || 0101
 0000 | 0    || 1111

```
