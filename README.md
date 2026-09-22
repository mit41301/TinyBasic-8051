Tiny Basic For 8051
Dave LeBlanc ported Tiny Basic to run under PAULMON2 on the 8051 development board. Here is his announcement:
Well, here's a cut at a Basic interpreter for the 8051 board. It seems to work per the limited testing I did of it. This is public domain, and I make no claims for the bit of editing I did to adapt the program for your board. Feel free to put it on your website etc. if you want to. (With some bit of additional testing and adaptation to PaulMon's I/O, this would be a nice candidate for a (r)un program on the distributed board too! :) .)

A few notes:

Org'd at 0x8000 and takes < 4kb of flash.
Data org'd at 2000 and takes whatever it takes beyond that - might be limited to 4kb. First 52 bytes are the variables A-Z. They are signed 16 bit ints - dunno how it deals with strings.
The enclosed zip contains the tb51 asm file, the tb51 doc file and the funky macro assembler. Amazing as it might be for a circa 1990 program, the assembler is hardcoded to find it's module and target (.asm) files on the A drive! You can work around this by hard-coding paths into the .asm files for the cpu module declaration, but I chose not to. The zip is of the contents of the floppy in A: that I used to build this version.
The program has been modified to co-exist (roughly!) with PaulMon. The usual strategy of removing or commenting out interrupt vector initializations and baud/serial port settings has been employed. Also, the location of the on-chip interpreter working variables has been re-arranged to minimize use of the register banks and bit-addressable storage. Stack has been relocated to only use the 8052's indirect on-chip ram, so this version will ONLY WORK ON AN 8052!
Information in the doc about locations of RAM and ROM etc. are not correct for this version of the program. Refer to the top of the asm/lst file for that information.
You can return to PaulMon by "CALL 0" (zero) followed by two cr's, with the second cr being PaulMon's autobaud training cr.
I've included the original tb51 file, as adapted for the Metalink assembler, so that people can see the changes that have been made.
