---
layout: page
title: "Q119635: PRB: APPEND FROM ARRAY Creates Only One Record"
permalink: /kb/119/Q119635/
---

## Q119635: PRB: APPEND FROM ARRAY Creates Only One Record

{% raw %}

	Article: Q119635
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5x,2.6a; MS-DOS:2.0,2.5x,2.6,2.6a; UNIX:2.6; WINDOWS:2.5x,2.6,2.6a,3.0,3.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	- Microsoft FoxPro for Windows, versions 2.5x, 2.6, 2.6a 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5x, 2.6, 2.6a 
	- Microsoft FoxPro for Macintosh, versions 2.5x, 2.6a 
	- Microsoft FoxPro for UNIX, version 2.6 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The APPEND FROM ARRAY command should create one record in the currently selected
	database for each row in an array. Occasionally, only a single record will be
	created with the data from the first element of the array.
	
	CAUSE
	=====
	
	The array has been created as a one-dimensional array, as shown in the following
	example:
	
	     DIMENSION myarray(40)
	
	RESOLUTION
	==========
	
	The array must be created as a two-dimensional array, as shown in the following
	example:
	
	     DIMENSION myarray(40,1)
	
	The ",1" causes the array to be created as 40 rows by 1 column. The APPEND FROM
	ARRAY command will now function as expected.
	
	Additional query words: FoxUnix FoxMac FoxDos FoxWin 2.50 2.50a 2.50b kbvfp300 kbvfp300b kbvfp500 kbvfp500a kbvfp600 2.50c
	
	======================================================================
	Keywords          :  
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro260aMac kbFoxPro200DOS kbFoxPro260DOS kbFoxPro260aDOS kbFoxPro260UNIX kbFoxPro260 kbFoxPro260a kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : MACINTOSH:2.5x,2.6a; MS-DOS:2.0,2.5x,2.6,2.6a; UNIX:2.6; WINDOWS:2.5x,2.6,2.6a,3.0,3.0b,5.0,5.0a,6.0
	
	=============================================================================
	

{% endraw %}
