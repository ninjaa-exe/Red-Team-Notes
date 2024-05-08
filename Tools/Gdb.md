## Cheat Sheet

| **Command**                                       | **Usage**                                         |
| ------------------------------------------------- | ------------------------------------------------- |
| gdb -q ./program                                  | <br>Open the program in gdb                       |
| r                                                 | run the program                                   |
| run < file                                        | executes an output file in the program            |
| run < < (python -c 'print "A" * number + address) | Send an exit command to the program               |
| info functions                                    | Shows the program functions                       |
| disas function                                    | Shows the disassembly of a function               |
| i r                                               | Shows how the registers are                       |
| set disassembly-flavor intel                      | Change the program syntax                         |
| x/16xw $register                                  | Shows how the register is at the end of execution |
| b * address                                       | Set a breakpoint on the address                   |
| d                                                 | Deletes breakpoint                                |
| c                                                 | Continue the program after the breakpoint         |
| set $register = address                           | Change the value of a register                    |
