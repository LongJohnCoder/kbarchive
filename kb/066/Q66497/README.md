---
layout: page
title: "Q66497: C and c Are Illegal Symbols in MASM 5.10 and 5.10a"
permalink: /kb/066/Q66497/
---

## Q66497: C and c Are Illegal Symbols in MASM 5.10 and 5.10a

{% raw %}

	Article: Q66497
	Product(s): See article
	Version(s): 5.10 5.10a | 5.10 5.10a
	Operating System(s): MS-DOS | OS/2
	Keyword(s): ENDUSER | | mspl13_masm
	Last Modified: 12-NOV-1990
	
	If you assemble the code below with the Microsoft Macro Assembler
	version 5.10 or 5.10a, the following error is generated:
	
	   error A2009: Symbol not defined:
	
	This error occurs because "c" or "C" can be used in your .MODEL
	statement to identify that you are doing mixed-language programming
	with C. This process makes C a reserved symbol, and therefore it
	cannot be used in your program.
	
	This behavior is by design and is not considered a problem with the
	Microsoft Macro Assembler.
	
	Code Example
	------------
	
	public c
	
	c PROC FAR
	c ENDP
	
	end
	
	Workaround
	----------
	
	Change "c" or "C" to something else.

{% endraw %}
