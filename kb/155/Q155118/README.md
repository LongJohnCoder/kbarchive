---
layout: page
title: "Q155118: IDE Controller Marked as SCSI in Boot.ini File"
permalink: /kb/155/Q155118/
---

## Q155118: IDE Controller Marked as SCSI in Boot.ini File

{% raw %}

	Article: Q155118
	Product(s): Microsoft Windows NT
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbenv
	Last Modified: 13-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	After installing Windows NT 4.0 on an IDE hard disk, you may receive the
	following error message:
	
	  Windows NT could not start because of a computer disk hardware configuration
	  problem.
	
	  Could not read from the selected boot disk. Check boot path and disk
	  hardware.
	
	  Please check the Windows NT documentation about hardware disk configuration
	  and your hardware reference manuals for additional information.
	
	CAUSE
	=====
	
	This problem can occur if the IDE hard disk is misdetected as a SCSI drive in
	the Boot.ini file.
	
	RESOLUTION
	==========
	
	To resolve this problem, follow these steps:
	
	1. Edit the Boot.ini file. Replace "scsi" with "multi" (without quotation
	  marks).
	
	2. Delete or rename the Ntbootdd.sys file in the root folder.
	
	MORE INFORMATION
	================
	
	Note that the resolution listed in this article may also resolve the problem if
	you receive the following error message when you reboot your computer after
	installing Windows NT 4.0:
	
	  OSLoader ver 4.00 SCSI0 DISK0 - Windows\System32\NTOSKRNL.EXE Windows NT
	  could not start because the following file is missing or corrupt:
	  Winnt\system32\ntoskrnl.exe
	  Please re-install a copy of the corrupt file
	
	Additional query words: ntoskrnl
	
	======================================================================
	Keywords          : kbenv 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : :4.0
	
	=============================================================================
	

{% endraw %}
