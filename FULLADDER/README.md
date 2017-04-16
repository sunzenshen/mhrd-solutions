```
Full Adder Specification
========================

Description:
------------
The FULLADDER is only different to the HALFADDER in that it has an additional input called "carry in". The resulting sum is the sum of all three input bits. In contrast to the HALFADDER, chaining multiple FULLADDERS enables you to sum up numbers bigger than 1 bit.
Check the appendix in the manual for binary notation of numbers and binary arithmetics.


Interface Specification:
------------------------
Inputs: carryIn, in1, in2;
Outputs: out, carryOut;


Graphical Representation:
-------------------------
-carryIn--\
         _|__
---in1--|    |
        | FA |--out----
---in2--|____|
           |
           \--carryOut-


Truth Table:
------------
 carryIn | in1 | in2 || out | carryOut
 -------------------------------------
 0       | 0   | 0   || 0   | 0
 0       | 0   | 1   || 1   | 0
 0       | 1   | 0   || 1   | 0
 0       | 1   | 1   || 0   | 1
 1       | 0   | 0   || 1   | 0
 1       | 0   | 1   || 0   | 1
 1       | 1   | 0   || 0   | 1
 1       | 1   | 1   || 1   | 1

```
