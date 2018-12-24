====
GDB Cheatsheet
====

Command
-------

+----------------+--------------------------------------------------------------------------+
| Command        |  Description                                                             |
+----------------+--------------------------------------------------------------------------+
| (b)reak        | | Set breakpoint at specified location.                                  |
|                | | e.g. ``break m4_changequote``                                          |
+----------------+--------------------------------------------------------------------------+
| (r)un          | | Running the program under GDB control.                                 |
|                | | e.g. ``run``                                                           |
+----------------+--------------------------------------------------------------------------+
| (n)ext         | | Advance execution to the next line,                                    |
|                | | But it would not jump to the subroutine.                               |
|                | | e.g. ``next``                                                          |
+----------------+--------------------------------------------------------------------------+
| (s)tep         | | Go to the next line to be execution in *any* subroutine.               |
|                | | e.g. ``step``                                                          |
+----------------+--------------------------------------------------------------------------+
| (bt)backtrace  | | To see where we are in the stack as a whole: the ``backtrace``         |
|                | | command display a stack frame for each active subroutine.              |
|                | | e.g. ``backtrace`` or  ``bt``                                          |
+----------------+--------------------------------------------------------------------------+
| (p)rint        | | To display the value of a variable.                                    |
|                | | e.g. ``p lquote``                                                      |
|                | | We also can set the value to the variable use print command.           |
|                | | e.g. ``p len_lquote=strlen(lquote)``                                   |
|                | |                                                                        |
|                | | - print/d to display the value in decimal                              |
|                | | - print/t to display the value in binary                               |
|                | | - print/x to display the value in hexadecimal                          |
|                | |                                                                        |
|                | | e.g. ``print/x $ebx``                                                  |
+----------------+--------------------------------------------------------------------------+
| (c)ontinue     | | Allow the program to continue executing.                               |
|                | | e.g. ``continue`` or ``c``                                             |
+----------------+--------------------------------------------------------------------------+
| Ctrl-d         | | Exit the program by giving it an EOF.                                  |
+----------------+--------------------------------------------------------------------------+
| info register  | | Display the value in all register.                                     |
+----------------+--------------------------------------------------------------------------+
|                | | Display the content of specific memory location.                       |
| x/nyz          | | n: the number of the field to display                                  |
|                | | y: the format of the output, and can be:                               |
|                | |                                                                        |
|                | | - c for character                                                      |
|                | | - d for decimal                                                        |
|                | | - x for hexadecimal                                                    |
|                | | - o for octal                                                          |
|                | | - t for binary                                                         |
|                | | - f for float                                                          |
|                | | - gf for double                                                        |
|                | | - a for address                                                        |
|                | | - s for string                                                         |
|                | | - i for instruction                                                    |
|                | |                                                                        |
|                | | z: the size of the field to display:                                   |
|                | |                                                                        |
|                | | - b for byte                                                           |
|                | | - h for 16-bit word(half-word)                                         |
|                | | - w for 32-bit word                                                    |
|                | | - g for 64-bit giant word                                              |
|                | |                                                                        |
|                | | e.g. ``x/42cb &output``                                                |
+----------------+--------------------------------------------------------------------------+

References
-----
https://sourceware.org/gdb/current/onlinedocs/gdb/
