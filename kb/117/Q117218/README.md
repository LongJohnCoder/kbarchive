---
layout: page
title: "Q117218: How to Return the Maximum Value in a Database Field"
permalink: /kb/117/Q117218/
---

## Q117218: How to Return the Maximum Value in a Database Field

{% raw %}

	Article: Q117218
	Product(s): Microsoft FoxPro
	Version(s): MACINTOSH:2.5b,2.5c; MS-DOS:2.0,2.5,2.5a,2.5b,2.6; WINDOWS:2.5,2.5a,2.5b,2.6,3.0
	Operating System(s): 
	Keyword(s): kbcode
	Last Modified: 10-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, version 3.0 
	- Microsoft FoxPro for MS-DOS, versions 2.0, 2.5, 2.5a, 2.5b, 2.6 
	- Microsoft FoxPro for Windows, versions 2.5, 2.5a, 2.5b, 2.6 
	- Microsoft FoxPro for Macintosh, versions 2.5b, 2.5c 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	FoxPro does not provide a function for returning the maximum value stored in a
	field in a database. However, FoxPro does provide the command verb CALCULATE
	expr list> MAX() TO memvar. Although this command is useful, you may need to
	call a function that will find and return the maximum value in a field for a
	given condition. To do this, you can use the sample code shown below, which
	returns the maximum value in a field in any specified table for any given
	condition.
	
	NOTE: There are several ways of writing this function; this is only one example
	of how to write it.
	
	MORE INFORMATION
	================
	
	     **************************************************************
	     *                                                            *
	     *  Function:     DBMAX()                                     *
	     *  Parameters:                                               *
	     *      fieldname   C   Required                              *
	     *      workarea    N/C Optional                              *
	     *      condition   C   Optional                              *
	     *                                                            *
	     *                                                            *
	     *  Purpose: Returns the highest value of any field in the    *
	     *           current or specified work area for any logical   *
	     *           condition.                                       *
	     *                                                            *
	     *  NOTE: When you are finding the maximum of a field that is *
	     *  not in the current work area, the alias must be supplied  *
	     *  in the first parameter.                                   *
	     **************************************************************
	
	     PARAMETERS fieldname, workarea, condition
	
	     **************************************************************
	     * Store parameter count and current work area to memory
	     * variables.
	     **************************************************************
	
	     STORE PARAMETERS() TO parms
	     STORE SELECT() TO currselect
	
	     **************************************************************
	     * Store current record and total records to memory variables.
	     * Initialize m.max memory variable.
	     **************************************************************
	
	     reccount = RECCOUNT(IIF(parms>1,workarea,currselect))
	     currecord = RECNO(IIF(parms>1,workarea,currselect))
	     m.max = 0
	
	     **************************************************************
	     * Select the correct work area if not current work area.
	     **************************************************************
	
	     IF parms > 1
	        SELECT (workarea)
	     ENDIF
	
	     **************************************************************
	     * Position cursor at top of file. Begin maximum loop.
	     **************************************************************
	
	     GO TOP
	     SCAN FOR IIF(parms > 2,EVALUATE(condition),.T.)
	     **************************************************************
	     * Use a SCAN loop to move through the database and evaluate
	     * the previous record with the current record and return the
	     * greater value.
	     **************************************************************
	        SKIP -1
	        STORE EVALUATE(fieldname) TO m.oldmax
	        m.max = MAX(EVALUATE(fieldname),m.max,m.oldmax)
	        SKIP 1
	        SET MESSAGE TO ALLTRIM(STR(m.max,10,2))
	     ENDSCAN
	
	     **************************************************************
	     * NOTE: The SCAN loop above could be replaced by the following
	     * code:
	     *
	     *    CALCULATE FOR IIF(parms > 2,EVALUATE(condition),.T.)
	     **************************************************************
	
	     **************************************************************
	     * Reset record pointer.
	     **************************************************************
	
	     DO CASE
	        CASE currecord > reccount
	           GO BOTTOM
	           SKIP 1
	        CASE currecord < reccount
	           GO TOP
	           SKIP -1
	        OTHERWISE
	           GO currecord
	     ENDCASE
	
	     **************************************************************
	     * Select the original work area if necessary.
	     **************************************************************
	
	     IF parms > 1
	        SELECT (currselect)
	     ENDIF
	
	     SET MESSAGE TO
	     RETURN m.max
	     ENDIF
	
	  The following is an example of how to use this function:
	
	     USE customer IN 1
	     SELECT 0
	     ? dbmax("customer.ytdpurch",1,"state = 'NC'")
	
	Additional query words: VFoxWin FoxWin FoxDos math user- defined function UDF
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250bMac kbFoxPro250cMac kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbVFP300
	Version           : MACINTOSH:2.5b,2.5c; MS-DOS:2.0,2.5,2.5a,2.5b,2.6; WINDOWS:2.5,2.5a,2.5b,2.6,3.0
	
	=============================================================================
	

{% endraw %}
