---
layout: page
title: "Q62202: WHEREIS.BAS Problem Under MS-DOS 4.00 and 4.01"
permalink: /kb/062/Q62202/
---

## Q62202: WHEREIS.BAS Problem Under MS-DOS 4.00 and 4.01

{% raw %}

	Article: Q62202
	Product(s): See article
	Version(s): 7.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | B_QuickBas | mspl13_basic
	Last Modified: 25-MAY-1990
	
	The sample program WHEREIS.BAS searches for the location of a specific
	file on disk. WHEREIS uses the BASIC SHELL statement to perform a DOS
	DIR command and redirects the results to a file that WHEREIS.BAS later
	scans for the file it is searching for.
	
	Under MS-DOS versions 4.00 and 4.01, the WHEREIS.BAS program SHELL
	command does not function correctly. The path specification string
	passed to the DOS DIR command from WHEREIS ends with a blackslash
	character, resulting in a DIR command something like the following:
	
	   DIR C:\QB45\x\
	
	This form of the DIR command returns a list of files in the QB45
	directory when used under MS-DOS 3.x and earlier. Under MS-DOS 4.00
	and 4.01, this command fails with the error message "Invalid
	directory." Removing the trailing backslash allows the DIR command to
	operate under MS-DOS 4.00 and 4.01.
	
	To correct WHEREIS.BAS to operate under MS-DOS 4.00 and 4.01, you need
	to add several lines to the ScanDir SUBprogram in WHEREIS.BAS.
	
	In the original version of WHEREIS.BAS, line 12 of the ScanDir SUB
	reads as follows:
	
	   SHELL "DIR " + PathSpec$ + " > " + TempSpec$
	
	To remove the trailing backslash from the string PathSpec$, replace
	the line above with the following:
	
	   StripPath$ = PathSpec$
	
	   IF RIGHT$(StripPath$,1) = "\" AND LEN(StripPath$) > 1 THEN
	     StripPath$ = LEFT$(StripPath$, LEN(StripPath$) - 1)
	   END IF
	
	   SHELL "DIR " + StripPath$ + " > " + TempSpec$

{% endraw %}
