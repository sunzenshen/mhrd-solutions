Demultiplexer Specification
===========================

Description:
------------
The DEMUX element has one data input, one select input and two data outputs. If the select input is 0, the data is transfered to the first output. Otherwise the data is transfered to the second output. The value of the output not taking the data bit value, is always zero.


Interface Specification:
------------------------
Inputs: in, sel;
Outputs: out1, out2;


Graphical Representation:
-------------------------
       ______
      /      |--out1-
-in--| DEMUX |
      \______|--out2-
         |
-sel-----/

Truth Table:
------------
 sel | in || out1 | out2
 -----------------------
 0   | 0  || 0    | 0
 0   | 1  || 1    | 0
 1   | 0  || 0    | 0
 1   | 1  || 0    | 1
