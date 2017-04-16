Multiplexer Specification
=========================

Description:
------------
The MUX element has two data inputs, one select input and one data output. If the select input is 0, the data from the first input is transfered to the output. Otherwise the data from the second input is transfered to the output.


Interface Specification:
------------------------
Inputs: in1, in2, sel;
Outputs: out;


Graphical Representation:
-------------------------
       ____
-in1--|    \
      | MUX |--out-
-in2--|____/
        |
-sel----/


Truth Table:
------------
 sel | in1 | in2 || out
 -----------------------
 0   | 0   | 0   || 0
 0   | 0   | 1   || 0
 0   | 1   | 0   || 1
 0   | 1   | 1   || 1
 1   | 0   | 0   || 0
 1   | 0   | 1   || 1
 1   | 1   | 0   || 0
 1   | 1   | 1   || 1
