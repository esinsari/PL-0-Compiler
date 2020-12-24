# PL-0-Compiler

 Compile in Eustis:
	In the same directory (needed):
		lex.c
		parser.c
		codegen.c
		vm.c
		hw4compiler.c
		headers.h
		<filename>.txt
	 
	To run the compiler, use the following in command line of Eustis:

		gcc -o compile lex.c vm.c parser.c codegen.c compiler.c
		./compile <filename>.txt <-l> <-a> <-v>

 Input/Output: 
	Lexical Analyzer - <filename>.txt
			   Contains source code written in PL/0 programming language
			   
			   lexAnayzerOutput.txt 
			   Contains: Source Program, Lexeme Table, Lexeme List
				
			   tokens.txt
			   Contains: Lexeme List	
	
	Parser - tokens.txt
		 Output from Lexical Analyzer
		    
		 parserOutput.txt
	         Contains: Generated errors if any; otherwise no errors, program is syntactically correct!
 		      		 
	Codegen - tokens.txt
		  Output from Lexical Analyzer
		
                  ICGOutput.txt
	          Contains: Assembly Code to be used in vm

	Vitual Machine - ICGOutput.txt
			 Output from Codegen
			
			 vmOutput.txt
			 Contains: Program in interpreted assembly language with line numbers
                                   The execution of program in the virtual machine, showing the stack, pc, bp, and sp
		    
 Purpose:
	Implementing compiler for tiny PL/O machine
        --> Lexical Anayzer 
	--> Recursice Descent Parser
	--> Intermediate Code Generator
	--> Virtual Machine
	--> Compiler Driver

 Lexical Analyzer:
	--> Capable to read in a source program written in PL/0
	--> Identify some errors; variable number does not start with a letter, number/name too long, and invalid symbols
	--> Produce, as output, the source program, the source program lexeme table, and a list of lexemes

 Recursive Descent Parser:
	--> Read inputs from Scanner (HW2) and parses the lexemes
       	--> Symbol Table is created
	--> Outputs generated error messages if not syntactically correct
 
 Intermediate Code Generator:
	--> If error is not generated by the Parser, then the execution of the compiler driver continues with icg  
        --> Generates the assembly language <op, l, m> using tokens from Scanners (HW2)     
        --> Outputs assembly language for Virtual Machine (HW1)
 
 Virtual Machine:
 	--> Stack Machine with two memory stores; stack and data area
	--> The Insturction Set Architectur with 23 instructions
	--> Requires two steps Fetch&Execute
	--> Outputs interpreted assembly language and execution of program showing the stack, pc, bp, and sp

 Compiler Driver & Directives: 
	Combine all of the compiler parts into one single program.
	--> -l Lexical Analyzer Output
	--> -a Parser/Codegen Output 
	--> -v Virtual Machine Output 
