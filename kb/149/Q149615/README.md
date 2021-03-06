---
layout: page
title: "Q149615: PRB: C1004 or C1060 Error Generated by Inline _asm Call"
permalink: /kb/149/Q149615/
---

## Q149615: PRB: C1004 or C1060 Error Generated by Inline _asm Call

{% raw %}

	Article: Q149615
	Product(s): Microsoft C Compiler
	Version(s): WINNT:2.0,2.1,2.2,4.0,4.1,5.0;
	Operating System(s): 
	Keyword(s): kbtshoot kbCompiler kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kbVC500 kbVC600
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The C/C++ Compiler (CL.EXE), included with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 5.0 
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	   - *EDITOR Please do not choose this product*Microsoft Visual C++ 32-bit Edition* use 241, 265, 225, versions 2.0, 2.1, 2.2, 4.0, 4.1, on platform(s):
	      - the hardware: Intel x86 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A C1004 (Unexpected End of File) or C1060 (Compiler is out of heap space) error
	may occur when comments are misused within inline assembly code.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Semicolons are used in assembly code to begin source comments. They behave
	exactly the same way as using the C++ comment specifier (//). All text following
	a semicolon is considered to be a comment. Comments terminate at the end of the
	current line.
	
	Sample Code
	-----------
	
	  void main(void)
	  {
	     _asm { int 3; }    // The closing curly brace is ignored because it's
	                        // part of the assembly comment line
	
	     _asm {             // This code works because no valid code follows
	        int 3;          // the semicolon comment specifier
	     }
	
	     _asm { int 3 }     // This also works and is valid code
	  }
	
	Additional query words: 9.00 9.10 9.20 10.00 10.10
	
	======================================================================
	Keywords          : kbtshoot kbCompiler kbVC200 kbVC210 kbVC220 kbVC400 kbVC410 kbVC500 kbVC600 
	Technology        : kbVCsearch kbAudDeveloper kbCVCComp
	Version           : WINNT:2.0,2.1,2.2,4.0,4.1,5.0;
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
