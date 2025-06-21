Explore stack and heap in GDB
https://jvns.ca/blog/2021/05/17/how-to-look-at-the-stack-in-gdb/

DMESG debug tips:
https://serverfault.com/questions/366392/how-to-convert-dmesg-time-format-to-real-time-format


GDB tool - Commands reference link
https://visualgdb.com/gdbreference/commands/
commands i used:

bt - to get back trace

bt full -- to get backtrace with detailed register level info for memory allocated vars and initializer values for few variables

x/s <register address> -- to get data inside that address in string format

x/32xb <register address> -- print 32 byte hex format data. replace 32 with no of bytes needs to be examined

print <variables used in crash code part>  -- prints values for that vars

disassemble <address of function> -- assmebly level operation flow done in that function
