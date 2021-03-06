---
layout: page
title: "Q136690: Firing Sequence of Visual FoxPro Events"
permalink: /kb/136/Q136690/
---

## Q136690: Firing Sequence of Visual FoxPro Events

{% raw %}

	Article: Q136690
	Product(s): Microsoft FoxPro
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-AUG-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article shows the general firing sequence of Visual FoxPro events. For more
	information, please search for the "Visual FoxPro Event Sequence" topic in the
	Visual FoxPro Help file.
	
	There can be an infinite number of potential user interaction scenarios that will
	generate specific event sequences. An easy way to observe the order is to
	include the following lines of code in the events you are interested in:
	
	     ACTIVATE SCREEN
	     ? PROGRAM()
	
	MORE INFORMATION
	================
	
	For a description of event sequences in a simple user interaction scenario,
	please see Chapter 4 of the Visual FoxPro "Developer's Guide." For a detailed
	look at Visual FoxPro event sequences, run Controls.app from the
	Vfp\Samples\Controls directory, select "See Event Firing Sequences" in the
	Examples list, and choose Run Example.
	
	The data environment's AutoOpenTables property is assumed to be set to true
	(.T.). Other events can occur based on user interaction and system response.
	
	Object                            Events
	--------------------------------------------------
	
	Data environment                  BeforeOpenTables
	Form set                          Load
	Form                              Load
	Data environment cursor(s)        Init
	Data environment                  Init
	Objects  (1)                      Init
	Form set                          Activate
	Form                              Activate
	Object1  (2)                      When
	Form                              GotFocus
	Object1                           GotFocus
	Object1                           Message
	Object1                           Valid  (3)
	Object1                           LostFocus
	Object2  (4)                      When
	Object2                           GotFocus
	Object2                           Message
	Object2                           Valid  (3)
	Object2                           LostFocus
	Form                              QueryUnload
	Object  (5)                       Destroy
	Form                              Unload
	Form set                          Unload
	Data environment                  AfterCloseTables
	Data environment                  Destroy
	Data environment cursor(s)        Destroy
	
	(1) For each object, from innermost object to outermost container
	(2) First object in the tab order
	(3) As the object loses focus
	(4) Next object to get focus
	(5) For each object, from outermost container to innermost object
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300
	
	=============================================================================
	

{% endraw %}
