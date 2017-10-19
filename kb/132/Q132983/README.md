---
layout: page
title: "Q132983: Registry Editor Error Message: Access Code Is Invalid"
permalink: /kb/132/Q132983/
---

## Q132983: Registry Editor Error Message: Access Code Is Invalid

	Article: Q132983
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): kberrmsg kbtool win95
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about the registry. Before
	you edit the registry, you should first make a backup copy of the registry
	files (System.dat and User.dat). Both are hidden files in the Windows
	folder.
	
	SYMPTOMS
	========
	
	When you try to start Registry Editor (Regedit.exe), you may receive the
	following error message:
	
	  Access code is invalid
	
	CAUSE
	=====
	
	This error can occur if either of the following conditions is true:
	
	- There is an older version of Regedit.exe on the hard disk.
	
	- You are using user profiles and have disabled the ability to edit registry
	  settings.
	
	RESOLUTION
	==========
	
	To correct the problem, use either of the following methods:
	
	- Check for multiple copies of the Regedit.exe file on the hard disk. If you
	  find multiple copies, remove all but the latest version of the file. The
	  Regedit.exe file should be located in the Windows folder with a size of
	  120,320 bytes and a date of 07-11-95 9:50 AM.
	
	- Temporarily disable user profiles. To do so, follow these steps:
	
	  1. Click the Start button, point to Settings, then click Control Panel.
	
	  2. Double-click the Passwords icon.
	
	  3. On the User Profiles tab, click the "All users of this computer use the
	     same preferences and desktop settings" option button.
	
	  4. Click OK.
	
	MORE INFORMATION
	================
	
	You may find that you need to extract the Regedit.exe file from the original
	Windows 95 disks. For information about extracting files, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q129605 How to Extract Original Compressed Windows Files
	
	======================================================================
	Keywords          : kberrmsg kbtool win95 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	