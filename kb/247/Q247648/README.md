---
layout: page
title: "Q247648: FS 2000: Sounds in the Program Are Cut Off or Break Up"
permalink: /kb/247/Q247648/
---

## Q247648: FS 2000: Sounds in the Program Are Cut Off or Break Up

{% raw %}

	Article: Q247648
	Product(s): Microsoft Home Games
	Version(s): WINDOWS:
	Operating System(s): 
	Keyword(s): kbsound kbimu msgame
	Last Modified: 07-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Flight Simulator 2000 
	- Microsoft Flight Simulator 2000 Professional Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you run Microsoft Flight Simulator 2000, sounds in the program may be cut
	off, break up, or be played inconsistently.
	
	CAUSE
	=====
	
	This behavior can occur if a Creative Labs Sound Blaster PCI 64 sound card is
	installed in your computer.
	
	RESOLUTION
	==========
	
	To resolve this issue, download and install the latest version of the sound
	driver for your sound card from the following Creative Labs Web site:
	
	  http://www.creative.com
	
	To work around this issue in Microsoft Windows 98, reduce the audio hardware
	acceleration setting:
	
	1. Click Start, and then click Run.
	
	2. In the Open box, type "dxdiag" (without the quotation marks), and then click
	  OK.
	
	3. Click the Sound tab.
	
	4. Under DirectX Features, move the Hardware Sound Acceleration Level slider all
	  the way to the left (the "No acceleration" setting).
	
	5. Click Exit.
	
	NOTE: These steps require that Microsoft DirectX 7.0 or later is installed on the
	computer.
	
	Additional query words: flightsim fsim fs fs2k fs2000 msgame sb
	
	======================================================================
	Keywords          : kbsound kbimu msgame 
	Technology        : kbGamesSearch kbFlightSimSearch kbFlightSim2000 kbSimSearch
	Version           : WINDOWS:
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
