####
Bochs Cheatsheet
####


Debugger
-----

+---------------------+---------------------------------------------+
| Command             | Description                                 |
+---------------------+---------------------------------------------+
|| c                  |                                             |
|| cont               | continue executing                          |
|| continue           |                                             |
+---------------------+---------------------------------------------+
|| s    [count]       | for SMP simulation, executie count          |
|| step [coutn]       | instruction, default is 1                   |
+---------------------+---------------------------------------------+
|| s    [cpu] [count] | for SMP simulation, executie count          |
|| step [cpu] [coutn] | instruction on cpu, default is 1            |
+---------------------+---------------------------------------------+
|| s    all [count]   | for SMP simulation, executie count          |
|| step all [coutn]   | instruction on all cpu, default is 1        |
+---------------------+---------------------------------------------+
|| Ctrl-C             | | stop execution and return to command line |
|| Ctrl-D             |   prompt                                    |
|                     | | if at empty line on command line,         |
|                     |   exit                                      |
+---------------------+---------------------------------------------+
|| q                  |                                             |
|| quit               | exit debugger and execution                 |
|| exit               |                                             |
+---------------------+---------------------------------------------+
