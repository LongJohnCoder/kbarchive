---
layout: page
title: "Q126957: Composer Titles: Older Sound Blaster CSPMAN.DLL Causes Errors"
permalink: /kb/126/Q126957/
---

## Q126957: Composer Titles: Older Sound Blaster CSPMAN.DLL Causes Errors

{% raw %}

	Article: Q126957
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Multimedia Beethoven for Windows, versions 1.0, 1.1 
	- Microsoft Multimedia Mozart for Windows, version 1.0 
	- Microsoft Multimedia Stravinsky for Windows, version 1.0 
	- Microsoft Multimedia Strauss for Windows, version 1.0 
	- Microsoft Multimedia Schubert for Windows, version 1.0 
	- Microsoft Dangerous Creatures for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start any of the applications listed at the top of this
	article, you may receive one of the following error messages
	
	  <Title> has caused an error in CSPMAN.DLL
	
	where <Title> is the name of the application. The error message includes
	the Ignore and Cancel button. Choosing Ignore has no effect. If you choose
	Cancel, one of the following error messages may appear and/or the system may
	stop responding (hang):
	
	- <Title> has caused an error in MSGBLAST.VBX
	
	- <Title> has caused an error in VBRUN300.DLL
	
	- the computer may stop responding (hang)
	
	CAUSE
	=====
	
	This behavior can occur if version 3.0 or a previous version of the Cspman.dll
	file is installed on the computer. This file is a component of the drivers for
	Creative Labs Sound Blaster sound cards.
	
	RESOLUTION
	==========
	
	If the symptoms occur only when you start one of the products listed at the
	beginning of this article, update the Cspman.dll file to version 3.01 or
	greater. To do so, contact your hardware manufacturer to obtain the most recent
	version of the driver for your sound card.
	
	If the computer stops responding when Windows starts, follow these steps to
	resolve the issue:
	
	1. Restart F8 to Command Prompt Only.
	
	2. Type the following line, and then press ENTER
	
	     cd <windows>\system
	
	  where <windows> is the folder in which Windows is installed.
	
	3. Type the following line, and then press ENTER:
	
	     ren cspman.dll cspman.bad
	
	4. Press CTRL+ALT+DELETE to restart the computer.
	
	5. Contact your hardware manufacturer to obtain the most recent version of the
	  driver for your sound card.
	
	MORE INFORMATION
	================
	
	According to Creative Labs, the latest Cspman.dll file is version 3.04 as of
	January, 1995. For additional information about Creative Labs drivers, contact
	Creative Labs technical support at (405) 742-6622, or connect to the Creative
	Labs Web site at the following address:
	
	  http://www.soundblaster.com/
	
	The third-party contact information included in this article is provided to help
	you find the technical support you need. This contact information is subject to
	change without notice. Microsoft in no way guarantees the accuracy of this
	third-party contact information.
	
	The third-party products discussed here are manufactured by a vendor independent
	of Microsoft; we make no warranty, implied or otherwise, regarding this
	product's performance or reliability.
	
	Additional query words: multi media multimedia multi-media mmtitles SoundBlaster technologies ltd guide explorapedia explorer kids mskids homekids
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeProdSearch kbHomeMMsearch kbZNotKeyword kbMMStrauss kbMMSchubert kbMMStravinsky kbMMMozart100 kbMMBeethoven100 kbMMBeethoven110 kbDangerousCreatures
	
	=============================================================================
	

{% endraw %}
