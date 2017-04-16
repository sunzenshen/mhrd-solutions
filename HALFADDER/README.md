Half Adder Specification
========================

Description:
------------
The HALFADDER takes two bits as inputs and adds them up. The sum is given as output as well as a carry bit.
Check the appendix in the manual for binary notation of numbers and binary arithmetics.


Interface Specification:
------------------------
Inputs: in1, in2;
Outputs: out, carry;


Graphical Representation:
-------------------------
       ____
-in1--|    |
      | HA |--out-
-in2--|____|
         |
         \--carry-


Truth Table:
------------
 in1 | in2 || out | carry
 ------------------------
 0   | 0   || 0   | 0
 0   | 1   || 1   | 0
 1   | 0   || 1   | 0
 1   | 1   || 0   | 1
