```
1-Bit Register Specification
============================

Description:
------------
Like the DFF element the REGISTER element has an internal state, an input and an output. The internal state of the REGISTER however is only set to the value of the input in case the input load flag is 1.
Check the DFF specification and the manual for sequential logic.

Interface Specification:
------------------------
Inputs: in, load;
Outputs: out;


Graphical Representation:
-------------------------
      _____
     |     |
-in--| REG |--out-
     |_____|
        |
--load--/


Example:
--------
 in  | load || out
 -----------------
 0   | 0    || 0
 1   | 0    || 0
 1   | 1    || 0
 0   | 0    || 1
 0   | 1    || 1
 0   | 0    || 0

 ```
