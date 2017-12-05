Virtual CPU
===========

Created by: Hennok Tadesse & Derek McCreery

 

**Description**
---------------

This virtual CPU is created in C language to perform registry level simulation
of a CPU based on the ARM Cortex M0+ architecture. The CPU’s memory size is
16Kbytes and uses 32-bit registers. The program has a simple user interface that
would allow users to test machine level programs written for the CPU. The CPU
executes various instructions based on the file in memory. The CPU has other
features such as load file, memory dump, memory modify, write file, reset
registers and display registers.

 

**State of the Program**
------------------------

The following functions were implemented to the virtual CPU:

 

### **Load File – LoadFile function**

When the user enters the option ‘L’ or ‘l’, the load file function will execute
and prompt the user to enter a filename they would want to load into memory. The
function will pass a pointer to a buffer and the maximum number of bytes to be
read from the file. The function will also display the number of bytes read from
the file in decimal and in hex.

 

### **Memory Dump – MemDump function**

When the user enters the option ‘D’ or ‘d’, the MemDump function will execute.
The memory dump function is dependent from the load function. The function
receives a pointer which allows it to access the content in memory (the content
that was loaded into memory by the load function). The user will be prompted to
enter the length of bytes to be displayed and as well as the offset to specify
where to start displaying the memory dump.

 

### **Memory Modify – MemMod function**

When the user enters the option ‘M’ or ‘m’, the MemMod function will execute.
The memory modify function prompts the user for an offset in which they would
start to modify from the loaded file. The address of the offset entered will be
displayed along with the respected value. It will then prompt the user to enter
a new value to replace the value at the respected address and then it will
increment the address. If the user enters a “.” The menu will be displayed and
prompts the user to select an option.

 

### **Quit**

When the user enters ‘Q’ or ‘q’ the program will terminate.

 

### **Write file – WriteFile function**

When the user enters ‘W’ or ‘w’ the WriteFile function will execute and it will
prompt the user to enter a file name to be created and then the size to write to
the file.

 

### **Display Registers – displayRegisters function**

This function will display the contents of all the registers and as well as all
of the flags.

 

### **Reset Registers – zeroRegisters function**

This function will reset all of the registers and as well as all of the flags to
0.

 

### **Help**

This function will display the menu of which commands the user may want to do.

 

### **Go​ function**

This function is responsible for executing the CPU instructions such as, load
instruction, stop instruction, add and sub instruction and as well as the
conditional and unconditional branches.

 

**Sample Output**
-----------------

### Memory Dump:

![](Images/pic1.png)

 

### Register Display:

![](Images/pic2.png)

 

### Displayed registers after running through a program:

![](Images/pic3.png)

 

**Testing**
-----------

| **Test**                                                                                                                                                                                                                                       | **Test Step**                                                                                                                                                                                                                                                                                                                                                                                                 | **Actual Results**                                                                                                                                                                                                                 |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| LoadFile Function: This test was performed to ensure that a file would be loaded into memory and display the correct file size.                                                                                                                | \>Pressing ‘L’ or ‘l’ that would execute the function. \>Entering the filename that would be loaded into memory. \>Entering a filename that did not exist.                                                                                                                                                                                                                                                    | \>After entering the filename to be loaded into memory, the file size is displayed in decimal and as well as in hex. \>Entering a filename that did not exist had returned an error message saying “The file does not exist”.      |
| MemDump Function: This test was performed to ensure that specified amount of bytes are being displayed and that the memory dump is displaying at the proper offset as well as entering the length and offset which is greater than the memory. | \>Pressing ‘D’ or ‘d’ that would execute the function. \>Entering the length of bytes to be displayed in hex. \>Entering the offset which specifies the part to be displayed.                                                                                                                                                                                                                                 | \>Entering the length and offset which is greater than the memory will result in an error message saying “out of bounds” \>Entering correct values for the length and offset will display the memory dump at the specified values. |
| MemMod Function: This test was performed to ensure that the existing value will get replaced with the entered hex value and that the function will exit if the user enters “.”.                                                                | \>Pressing ‘M’ or ‘m’ that would execute the function. \>Entering the offset in which to start modifying \>Entering the new hex value to replace the value at the entered offset \>Entering “.” To end the function                                                                                                                                                                                           | \>The existing value at the given offset gets replaced by the new value entered and then increments the address. \>Entering a “.” Terminates the function and brings up the menu.                                                  |
| WriteFile Function: This test was performed to ensure that the file was created correctly with the specified size.                                                                                                                             | \>Pressing ‘W’ or ‘w’ that would execute the function. \>Entering the filename \>Entering the file size                                                                                                                                                                                                                                                                                                       | \>Successfully created the file with the specified filename and file size.                                                                                                                                                         |
| displayRegisters Function: This test was performed to ensure that the registers and flags are displayed according to their current state.                                                                                                      | \>Pressing ‘R’ or ‘r’ that would execute the function.                                                                                                                                                                                                                                                                                                                                                        | \>The registers and flags are displayed successfully according to their current state.                                                                                                                                             |
| zeroRegisters Function: This test was performed to ensure that the registers and flags would reset to 0 when executed.                                                                                                                         | \>Pressing ‘Z’ or ‘z’ that would execute the function.                                                                                                                                                                                                                                                                                                                                                        | \>Cleared all registers and flags                                                                                                                                                                                                  |
| go Function: This test was performed to ensure that the function would go through the instruction file and execute the instructions accordingly.                                                                                               | \>Loading in a file that has the contents of (l 0 100 l 1 100 a s c 21 s u 33 x a x) Which would load 100 to register 0, load 100 to register 1, add register 0 and 1, sub register 0 and 1, conditional branch to location 21, sub register 0 and 1, unconditional branch to 33 and then add register 0 and 1 and finally terminates the go function. \>Pressing ‘G’ or ‘g’ that would execute the function. | \>Successfully executed load instruction, add from register 0 and 1, sub from register 0 and 1, conditional branch to a location and unconditional branch to a location.                                                           |

 

Currently the program can only read in very specifically made programs and that
would be a cause of many errors or even segmentation faults.  Other than this
the program works correctly and I was unable to find any errors.  To test that
each implemented function was working in both the Go and Trace functions, I ran
a program that used all of them.  This file is included in the .zip file and is
named “test.txt”.

 

### **Conclusions**

In conclusion, this project was used to show us and think critically about how a
CPU would work form a logical point of view.  I believe that the assignment was
a good approach to further teach and reinforce the some of the ideas presented
in the course.  From here, to further the project, additional functions should
be added as well as making some of the existing code more flexible, for example
having the inputs more than one character long.
