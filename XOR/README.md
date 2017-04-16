X-Or Specification
==================

Description:
------------
The XOR gate (short for Exclusive-Or) has two inputs and one output. If _exactly_ one input is 1, the output is 1. Otherwise the output is 0.


Interface Specification:
------------------------
Inputs: in1, in2;
Outputs: out;


Graphical Representation:
-------------------------
       _____
-in1--|     |
      | XOR |--out-
-in2--|_____|


Truth Table:
------------
 in1 | in2 || out
 ----------------
 0   | 0   || 0
 0   | 1   || 1
 1   | 0   || 1
 1   | 1   || 0
