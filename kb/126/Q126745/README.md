---
layout: page
title: "Q126745: Explorapedia: ErrMsg: Error 8## (or 4##) When Starting"
permalink: /kb/126/Q126745/
---

## Q126745: Explorapedia: ErrMsg: Error 8## (or 4##) When Starting

{% raw %}

	Article: Q126745
	Product(s): Microsoft Home Kids Products
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 29-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Explorapedia series: World of Nature for Windows, version 1.0 
	- Microsoft Explorapedia series: World of People for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start Explorapedia, you may receive an error message similar
	to the following:
	
	  Explorapedia error 80048212-0
	  An error occurred while starting Explorapedia. Restart Windows and try again.
	  If that fails to correct the problem, run Setup from the Explorapedia CD-ROM
	  again.
	
	All Explorapedia error messages that start with Explorapedia error 80... or 48...
	refer specifically to sound problems.
	
	CAUSE
	=====
	
	This error message occurs when an incompatible sound driver is installed on your
	computer. Sound drivers that may cause this error message are the DSOUND
	Multimedia Wave driver and the PC Speaker driver.
	
	
	If you have moved the product and/or its components after installation, you may
	receive a similar error message. For more information on how to resolve that
	problem, see the "More Information" section later in this article.
	
	RESOLUTION
	==========
	
	If you have an incompatible sound card driver, you may be able to resolve this
	problem by removing the driver.
	
	Use the following steps to remove the DSOUND Multimedia Wave driver or the PC
	Speaker driver:
	
	Windows 95/98
	-------------
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Multimedia.
	
	3. Click the Advanced or Devices tab.
	
	4. Double-click Audio Devices to expand the branch.
	
	5. Click any of the following drivers, and then click Properties:
	   - DSOUND Multimedia Wave Driver
	
	   - Audio for Internal Speaker Wave Driver
	
	   - Audio for Sound Driver for PC-Speaker
	
	6. Click Remove. Repeat step 5 for each driver listed in step 5.
	
	7. Shut down, and then restart the computer.
	
	
	Windows 3.1
	-----------
	
	1. Double-click the Control Panel icon. (Control Panel is usually located in the
	  Main program group in Program Manager.)
	
	2. Double-click the Drivers icon.
	
	3. In the Drivers control panel, locate the DSOUND Multimedia Wave Driver or PC
	  Speaker Driver on the list of Installed Drivers.
	
	4. Click the driver(s) and then click Remove, which removes the driver from the
	  list.
	
	5. Restart Windows.
	
	You should now be able to run Explorapedia successfully.
	
	NOTE: You may receive a similar error message when you start Explorapedia using
	the Ensoniq Soundscape Sound Card drivers. For additional information about the
	Ensoniq Sound Card problem, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q124812 Kids: Hangs with Ensoniq Sound Card
	
	  Q124546 Multimedia: Compressed Audio and the Ensoniq Soundscape Card
	
	The third-party products discussed here are manufactured by vendors independent
	of Microsoft; we make no warranty, implied or otherwise, regarding these
	products' performance or reliability.
	
	MORE INFORMATION
	================
	
	You can also receive a similar error message, "Explorapedia Error
	80030002-0...," if the wrong folder is specified on the "mdf1=" line in the
	[media] section of the following file(s):
	
	- World of Nature: Nature.ini located in Mskids\Explora
	
	- World of People: People.ini in Mskids\Explora\People
	
	To correct the problem, edit the Nature.ini or People.ini file to specify the
	correct folder, shown above. This problem occurs only if you have moved the
	program and/or its associated files from the original installation folder.
	
	
	Additional query words: ensonic error 800 Explorapedia startup tad errmsg xplora world nature people errors 480
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeMMsearch kbZNotKeyword2 kbExplorapediaNature100 kbExplorapediaPeople100
	Version           : WINDOWS:1.0
	
	=============================================================================
	

{% endraw %}
