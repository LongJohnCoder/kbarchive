---
layout: page
title: "Q108651: Flight Simulator: &quot;Disk Error&quot; or &quot;Fatal Error Has Occurred&quot;"
permalink: /kb/108/Q108651/
---

## Q108651: Flight Simulator: &quot;Disk Error&quot; or &quot;Fatal Error Has Occurred&quot;

{% raw %}

	Article: Q108651
	Product(s): Microsoft Home Games
	Version(s): MS-DOS:5.0
	Operating System(s): 
	Keyword(s): kberrmsg kbsetup
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Flight Simulator for MS-DOS, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start Flight Simulator 5.0, you may receive the following
	error message:
	
	  Disk error has occurred!
	  Filename: FS5.INI
	  ERROR CODE: 0002
	
	
	This error message indicates that the FS5.ini is missing or damaged.
	
	RESOLUTION
	==========
	
	Reinstalling Flight Simulator may not be necessary. Change to the Flight
	Simulator 5.0 directory (FLTSIM5 by default) and run Setup.exe. The Setup
	program may rebuild the FS5.ini.
	
	MORE INFORMATION
	================
	
	In some cases, Setup.exe may be damaged and you may be unable to run the Setup
	program. Copy a new copy of Setup.exe from disk 1.
	
	Flight Simulator 5.0 runs on a minimal FS5.ini consisting of 14 lines.
	
	  G2D=VGB.GRA
	  G3D=FSOG3D.FSO
	  KBD=KBD2.FSO
	  MOUSE=ON
	  SETUP=OFF
	  SITUATION=SITUATION\FS5.STN
	  STARTUP_DEMO=VIDEOS\FS5.VID
	  INCLUDE=FSO001.FSO
	  INCLUDE=UTIL.FSO
	  INCLUDE=APL001.FSO
	  INCLUDE=WEATHER.FSO
	  INCLUDE=BGLFE.FSO
	  INCLUDE=LESSONS.FSO
	  INCLUDE=U2D.FSO
	
	NOTE: There is an "O" (as in Oscar) in the line INCLUDE=FSO001.FSO (that is,
	F,S,O,zero,zero,1.F,S,O).
	
	With these entries, the Cessna will be on the runway at Meigs field.
	
	If you receive the following error message:
	
	  FATAL error has occurred!
	  Filename: FORN-000.FRN
	  ERROR CODE: 8027
	
	one or more of the above lines is missing from the FS5.ini file. With the above
	lines in the FS5.ini, the Setup program will fill in the missing lines and
	produce a new and complete FS5.ini with full functionality.
	
	NOTE: The above FORN-000.FRN error occurs if you have an overdrive chip installed
	on your system. There is no known resolution.
	
	For more information about the FORN-0000.FRN error message, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q126235 Flight Simulator: Fatal Error on DX/4 and OverDrive Processors
	
	Additional query words: 5.00 flightsim fltsim dos Fatal error has occured fs5
	
	======================================================================
	Keywords          : kberrmsg kbsetup 
	Technology        : kbGamesSearch kbFlightSimSearch kbFlightSim500DOS kbSimSearch
	Version           : MS-DOS:5.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
