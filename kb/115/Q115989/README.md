---
layout: page
title: "Q115989: Elapsed Time Example Involving Different Days"
permalink: /kb/115/Q115989/
---

## Q115989: Elapsed Time Example Involving Different Days

{% raw %}

	Article: Q115989
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
	
	The function shown below determines the number of seconds that have elapsed
	between two different times. This function will take into account switching to
	the next day.
	
	MORE INFORMATION
	================
	
	     PROCEDURE elaptime
	     PARAMETER m.startdate, m.enddate, m.starttime, m.endtime
	     * pass startdate, an 8-character starttime (HH:MM:SS), an enddate,
	     * and an 8-character endtime
	     * perform parameter type checking: return value of -1 indicates
	     * invalid parameter type
	     * Example of using the function elaptime:
	     * TempVariable=ElapTime({01/01/94},{01/02/94},"00:01:00",00:01:00")
	
	     IF TYPE('m.startdate') # "D" .OR. ;
	         TYPE('m.enddate') # "D" .OR. ;
	         (TYPE('m.starttime') # "C" .AND. LEN(m.starttime) # 8) .OR. ;
	         (TYPE('m.endtime') # "C" .AND. LEN(m.endtime) # 8)
	         RETURN -1
	     ENDIF
	
	     * if startdate > enddate, or same date and starttime > endtime,
	     * return 0
	     IF m.startdate > m.enddate .OR. (m.startdate = m.enddate .AND. ;
	          m.starttime > m.endtime)
	         RETURN 0
	     ENDIF
	
	     #DEFINE secsperday 86400
	
	     * determine whether the endtime is earlier or later than the
	     * starttime
	     IF m.endtime >= m.starttime
	         m.elapsecs = (m.enddate - m.startdate) * secsperday + ;
	             (time2secs(m.endtime) - time2secs(m.starttime))
	     ELSE
	         m.elapsdays = 0
	         IF m.enddate - m.startdate > 0
	             m.elapsdays = m.enddate - m.startdate - 1
	         ENDIF
	         m.elapsecs = (m.elapsdays * secsperday) + ;
	             (secsperday - time2secs(m.starttime)) + ;
	             time2secs(m.endtime)
	     ENDIF
	
	     RETURN m.elapsecs
	
	     FUNCTION time2secs
	     * passed a C8 HH:MM:SS string
	     * returns the number of seconds into the day this is
	     PARAMETER m.passedtime
	
	     m.retsecs = VAL(RIGHT(m.passedtime, 2)) + ;
	         60 * VAL(SUBSTR(m.passedtime, 4, 2)) + ;
	         3600 * VAL(LEFT(m.passedtime, 2))
	     RETURN m.retsecs
	
	Additional query words: VFoxWin FoxWin FoxDos calculate udf
	
	======================================================================
	Keywords          : kbcode 
	Technology        : kbHWMAC kbOSMAC kbVFPsearch kbAudDeveloper kbFoxproSearch kbZNotKeyword3 kbFoxPro250bMac kbFoxPro250cMac kbFoxPro200DOS kbFoxPro250DOS kbFoxPro250aDOS kbFoxPro250bDOS kbFoxPro260DOS kbFoxPro260 kbFoxPro250 kbFoxPro250a kbFoxPro250b kbVFP300
	Version           : MACINTOSH:2.5b,2.5c; MS-DOS:2.0,2.5,2.5a,2.5b,2.6; WINDOWS:2.5,2.5a,2.5b,2.6,3.0
	
	=============================================================================
	

{% endraw %}
