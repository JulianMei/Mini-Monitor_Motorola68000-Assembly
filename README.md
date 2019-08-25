# Mini-Monitor_Motorola68000-Assembly
Designed an implemented an assembly program that provides self-contained interface and functionalities. The program is written in Motorola MC68000 processor assembly language. The developement and debug is based on EASY68K which is a simulator simulates MC68000 processor environment. <br /><br />

As an assembly program, it defines its own _code and data segment_ and its own _exception handler table_. An exception will be raised for the following two illegal conditions: <br />
1.If the program counter enters a non-code segment address, because it leads to undefined behavior.  <br />
2.If an instruction tries to modify a non-data segment address, because this could corrupt source code stored in the code segment.<br />

The monitor program includes 4 parts:  <br />
*1.	User command interpreter* <br />
*2.	User command handling subroutines* <br />
*3.	Exception handling subroutines* <br />
*4.	Utility subroutines* <br />

The program begins at location $1000. After executing the starting location of the program a prompt ‘441MONITOR>’ will be displayed on the screen and the program will wait for user input. As soon as user input some characters by keyboard, the interpreter program will store the string in a block of memory with starting address labeled by ‘BUF’ (BUF = $3F00). Then interpreter program will compare the first two letters of the string with command names stored in stack one by one to determine which command has been entered. If there is a match then jump to the starting address of subroutines of the matched command. Otherwise an exception is raised 

