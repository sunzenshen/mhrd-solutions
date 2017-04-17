```
4-Way Demultiplexer Specification
=================================

Description:
------------
The DEMUX4W element has one data input, a 2-bit select bus input and four outputs. The value of the select input bus determines the output which the input data is transferred to. The value of all other outputs is zero.
For example: If the select bus has the value "10", the data is transferred to the third output. Check the appendix in the manual for binary notation.


Interface Specification:
------------------------
Inputs: in, sel[2];
Outputs: out1, out2, out3, out4;


Graphical Representation:
-------------------------
        _______
       /       |--out1-
      /        |--out2-
-in--| DEMUX4W |
      \        |--out3-
       \_______|--out4-
           |
--sel[2]---/

Truth Table:
------------
 sel | in || out1 | out2 | out3 | out4
 -------------------------------------
 00  | 0  || 0    | 0    | 0    | 0
 00  | 1  || 1    | 0    | 0    | 0
 01  | 0  || 0    | 0    | 0    | 0
 01  | 1  || 0    | 1    | 0    | 0
 10  | 0  || 0    | 0    | 0    | 0
 10  | 1  || 0    | 0    | 1    | 0
 11  | 0  || 0    | 0    | 0    | 0
 11  | 1  || 0    | 0    | 0    | 1

```
