# Mini-Monitor_Motorola68000-Assembly
Designed an implemented an assembly program that provides self-contained interface and functionalities. The program is written in **Motorola MC68000 processor assembly language**. The developement and debug is based on EASY68K which is a **simulator** simulates MC68000 processor environment. <br /><br />

As an assembly program, it defines its own **code segment, data segment and exception table**. It also defines a group of routines that handles different user commands such as *move a block of memory*, *Display CPU register values (pc, sp, status, etc.)*, *jump to a line and execute the instruction*, etc. <br /><br />

The monitor program includes 4 parts:  <br />
*1.	User command interpreter* <br />
*2.	User command handling subroutines* <br />
*3.	Exception handling subroutines* <br />
*4.	Utility subroutines* <br /><br />

The program begins at location $1000. After executing the starting location of the program a prompt ‘441MONITOR>’ will be displayed on the screen and the program will wait for user input. As soon as user input some characters from keyboard, the interpreter will store them in a block of memory with starting address labeled by ‘BUF’ (BUF = $3F00). Then it will compare the stored characters with command names predefined on the program's stack. <br />
If there is a matching command then jump to the starting address of that command's subroutines. Otherwise, raise an exception and jump to the exception handle routine, which is also predefined in the program. <br />
After a command is successfully handled, the program returns to the wait state waiting for the next user command. The program will exit only when the user input the "EXIT" command. <br /><br />

Note that an exception will be raised for the following two illegal conditions: <br />
1.If the program counter enters a non-code segment address, because it leads to undefined behavior.  <br />
2.If an instruction tries to modify a non-data segment address, because this could corrupt source code stored in the code segment.<br />
