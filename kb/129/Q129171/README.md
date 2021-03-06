---
layout: page
title: "Q129171: INFO: The Difference Among Visual FoxPro Numeric Data Types"
permalink: /kb/129/Q129171/
---

## Q129171: INFO: The Difference Among Visual FoxPro Numeric Data Types

{% raw %}

	Article: Q129171
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,5.0,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 18-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	With the addition of Double, Integer, and Currency data types, Visual FoxPro
	version 3.0 now has five numeric data type possibilities. This article describes
	the difference among the five numeric data types, explaining the circumstances
	under which each should be used.
	
	MORE INFORMATION
	================
	
	Currency
	--------
	
	The Currency data type is new to Visual FoxPro version 3.0. Use it to store
	monetary amounts. Currency requires 8 bytes in memory and 8 bytes on disk.
	
	With the Currency data type, data is limited to 4 decimal positions of precision.
	The numeric precision of Currency fields is:
	
	  -92233720368477.5807 to 922337203685477.5807
	
	Double
	------
	
	The Double data type is new to Visual FoxPro version 3.0. The double is a
	floating point numeric stored to disk as an 8-byte binary value. Use the double
	data type when the numeric precision of numeric, float, or integer fields is
	insufficient. The numeric precision of double fields is:
	
	  -4.94065648541247E-324 to 1.79769313486232E+308
	
	Integer
	-------
	
	The Integer data type is new to Visual FoxPro. Use the integer data type to store
	integers (numeric values without decimal positions). Integers require 4 bytes on
	disk and in memory. The numeric precision of integer fields is:
	
	  -2147483647 to 2147483646
	
	Numeric and Float
	-----------------
	
	The numeric and float data types each existed in FoxPro versions 2.5 and 2.6. In
	Visual FoxPro, the two data types are identical (float is provided for
	compatibility reasons only). Use them to store integers or numbers with decimal
	positions. Numeric and float data types are stored in memory as 6 bytes and are
	stored on disk from between 1 and 20 bytes. They are stored in a table on disk.
	The numeric precision of numeric and float fields is:
	
	  .9999999999E+20 to - .9999999999E+19
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP500 kbVFP600
	Version           : WINDOWS:3.0,5.0,6.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
