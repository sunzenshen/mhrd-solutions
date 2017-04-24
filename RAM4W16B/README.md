```
4-Register 16-Bit RAM Specification
===================================

Description:
------------
The RAM4W16B is a random access memory with 4 addressable registers and 16-bit bus width. In addition to a regular register, the RAM4W16B can save and retrieve 4 different values, which can be addressed via the address input bus.

Interface Specification:
------------------------
Inputs: in[16], load, address[2];
Outputs: out[16];


Graphical Representation:
-------------------------
          __________
         |          |
-in[16]--| RAM4W16B |--out[16]-
         |__________|
            | |
-----load---/ |
-address[2]---/

Example:
--------
 in     | address | load || out
 -------------------------------------
 0x5555 | 00      | 1    || 0x0000
 0x0000 | 00      | 0    || 0x5555
 0x0000 | 01      | 0    || 0x0000
 0xFFFF | 01      | 1    || 0x0000
 0x0000 | 01      | 0    || 0xFFFF
 0xAAAA | 10      | 1    || 0x0000
 0x0FF0 | 11      | 1    || 0x0000
 0x0000 | 00      | 0    || 0x5555
 0x0000 | 01      | 0    || 0xFFFF
 0x0000 | 10      | 0    || 0xAAAA
 0x0000 | 11      | 0    || 0x0FF0

 ```
