---
layout: page
title: "Q32816: PRB: Causes of R6000 &quot;Stack Overflow&quot; Error"
permalink: /kb/032/Q32816/
---

## Q32816: PRB: Causes of R6000 &quot;Stack Overflow&quot; Error

{% raw %}

	Article: Q32816
	Product(s): Microsoft C Compiler
	Version(s): winnt:
	Operating System(s): 
	Keyword(s): kb16bitonly kbprb
	Last Modified: 22-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C Run-Time (CRT), included with:
	   - Microsoft C for MS-DOS, versions 5.1, 6.0, 6.0a, 6.0ax 
	   - Microsoft C for OS/2, versions 5.1, 6.0, 6.0a 
	   - Microsoft C/C++ for MS-DOS, version 7.0 
	   - Microsoft Visual C++, versions 1.0, 1.5, 1.51, 1.52 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An attempt to run an application fails and the run-time library generates the
	following message:
	
	  R6000 Stack Overflow
	
	CAUSE
	=====
	
	There are two causes for this error:
	
	- The stack overflows because your program does not allocate enough stack space
	  to hold the data the application uses during execution. This often affects
	  applications that implement recursive algorithms or contain functions that
	  declare large amounts of stack-based "local" or "automatic" data.
	
	- The stack overflows because the C startup (initialization) code fails in its
	  attempt to allocate stack space.
	
	RESOLUTION
	==========
	
	To address the first cause above, perform one or more of the following:
	
	- Specify the /STACK linker option to specify a larger stack allocation
	
	- Modify the source code to use less recursion
	
	- Modify the source code to allocate less stack-based data
	
	To address the second cause above, reduce the size of the stack or reduce the
	amount of near data your application stores in the DGROUP segment.
	
	Please refer below for more information about the causes of this error, methods
	to address the problem, and a method to determine which of the causes above is
	relevant to a given situation.
	
	MORE INFORMATION
	================
	
	Case 1: R6000 Occurs While Application Running
	----------------------------------------------
	
	The stack overflows because the application attempts to push too much data
	(either function-return addresses or local data) on the stack. Each time a
	function call is made, the caller pushes the return address on the stack with
	any parameters. The called function may also allocate stack-based data for its
	own use. Each process requires stack space.
	
	To address the R6000 error, perform one of the following:
	
	- Decrease the amount of stack-based data. If you declare a variable with the
	  keyword "static," it is not pushed on the stack each time the function is
	  called.
	
	- Increase the size of the stack by specifying the /F <x> compiler option
	  switch, where <x> is a hexadecimal number that specifies the desired
	  stack size.
	
	- Change the stack size by specifying the /STACK:<x> linker option switch
	  (where <x> is a decimal number that specifies the desired stack size)
	  or by using the EXEMOD utility. Note that if you increase the stack size too
	  far, you can cause an R6000 error as described in case 2 below.
	
	Case 2: R6000 Occurs at Startup
	-------------------------------
	
	The startup code allocates stack space in the DGROUP segment. If DGROUP does not
	contain enough free space for the stack (by default, 2K), the startup code fails
	and generates the R6000 error.
	
	To address this situation, either reduce the size of the stack or reduce the
	amount of data stored in DGROUP. To reduce the stack size, compile with the /F
	<x> option, link with the /STACK:<x> option, or use the EXEMOD
	utility, as described above. To reduce the amount of data stored in DGROUP,
	compile the code in a large-data memory model (compact, large, or huge memory
	model) instead of a small-data memory model (small or medium memory model). If
	you are already using a large- data memory model, specify the /Gt compiler
	option switch to move data from DGROUP into far data segments.
	
	To use the /Gt option, specify /Gt<x>, where <x> is a decimal number
	of bytes. Data items larger than <x> bytes are placed into a separate data
	segment which creates room in DGROUP for the stack.
	
	Determining the Cause of the R6000 Error
	----------------------------------------
	
	The CodeView debugger provides an excellent method to determine the cause of the
	problem. After starting CodeView and specifying your application, execute to the
	beginning of the main() function by doing one of the following:
	
	- Manually single-step using the F8 key or T.
	
	- Enter "g main" (without the quotation marks) at the CodeView command prompt.
	
	Once execution passes the opening curly-brace ({) of main(), the C startup code
	has allocated space for the stack and data. An R6000 error at this time
	indicates cause 2 above (a stack overflow at startup). Otherwise, cause 1 is
	indicated.
	
	Additional query words: 1.00 1.50 6.00 6.00a 6.00ax 7.00
	
	======================================================================
	Keywords          : kb16bitonly kbprb 
	Technology        : kbVCsearch kbAudDeveloper kbCRT
	Version           : winnt:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
