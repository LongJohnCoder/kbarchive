---
layout: page
title: "Q117709: PRB: BROWSE FIELDS Results Inconsistent in 1-to-Many Relation"
permalink: /kb/117/Q117709/
---

## Q117709: PRB: BROWSE FIELDS Results Inconsistent in 1-to-Many Relation

	Article: Q117709
	Product(s): Microsoft FoxPro
	Version(s): MS-DOS:2.0,2.5x,2.6,2.6a; WINDOWS:2.5x,2.6,2.6a,3.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for Windows, versions 2.5x, 2.6, 2.6a 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5x, 2.6, 2.6a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The records in the child table of a one-to-many relationship do not update
	properly under certain conditions.
	
	RESOLUTION
	==========
	
	Issue a GO RECNO() command after returning to the parent table. This forces
	FoxPro to refresh the one-to-many relationship, and allows the update of the
	BROWSE results.
	
	STATUS
	======
	
	This behavior is by design. FoxPro cannot know what the developer is attempting
	to do, and allows the child table data to be read from wherever the record
	pointer has moved. By refreshing the relationship between the two tables with
	the GO RECNO() command, the developer is given the option to determine which
	data should be returned from the child, the old information or the updated
	information.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create two physical tables as described below:
	
	     PARENT.DBF                      CHILD.DBF
	     -----------------------------------------------------------
	
	     IDNO(C,5)   NAMES(C,10)         IDNO(C,5)      CITIES(C,10)
	     111         Sam                 114            Fairbanks
	     112         Mary                113            Houston
	     113         Beth                115            Phoenix
	     114         Larry               111            Dover
	     115         Pat                 112            Buffalo
	                                     111            Dallas
	                                     112            Portland
	
	2. Run the following code in a program. The name of the program does not
	  matter.
	
	        *Open up the tables, and set up the one-to-many relationship
	        USE Parent IN 1
	        USE Child IN 2
	        SELECT Parent
	        INDEX ON IDNO TAG IDNO
	        SET ORDER TO IDNO
	        SELECT Child
	        INDEX ON IDNO TAG IDNO
	        SET ORDER TO IDNO
	        SELECT Parent
	        SET RELATION TO idno INTO Child
	        SET SKIP TO Child
	        SELECT Parent
	
	        *Information window, and the first BROWSE FIELDS command displays
	        *correctly
	        WAIT WINDOW "Please note how the tables line up appropriately." ;
	           +CHR(13)+"Hit ESC to continue" NOWAIT
	        BROWSE FIELDS parent.idno, parent.names, child.idno, child.cities
	
	        *Select another record in the child for testing purposes, often a
	        *SEEK() might be performed here in an actual meaningful program
	        SELECT child
	        GO BOTTOM
	
	        *Reselect Parent table
	        SELECT parent
	
	        *Information window, and the incorrect results from the BROWSE
	        *FIELDS command
	        WAIT WINDOW "Now they don't appear right!!" + CHR(13)+ ;
	           "Hit ESC to continue" NOWAIT
	        BROWSE FIELDS parent.idno, parent.names, child.idno, child.cities
	
	        *The resolution, an information window, and the corrected results
	        *from the BROWSE FIELDS command
	        GO RECNO()
	        WAIT WINDOW "That fixed it !!" + CHR(13) + "Hit ESC to continue" ;
	        NOWAIT
	        BROWSE FIELDS parent.idno, parent.names, child.idno, child.cities
	
	Additional query words: VFoxWin FoxDos FoxWin 2.50 2.50a 2.50b refresh database
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro200DOS kbFoxPro260DOS kbFoxPro260aDOS kbFoxPro260 kbFoxPro260a kbVFP300
	Version           : MS-DOS:2.0,2.5x,2.6,2.6a; WINDOWS:2.5x,2.6,2.6a,3.0
	
	=============================================================================
	