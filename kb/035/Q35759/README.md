---
layout: page
title: "Q35759: Don't Change Disks during a Critical Error"
permalink: /kb/035/Q35759/
---

## Q35759: Don't Change Disks during a Critical Error

{% raw %}

	Article: Q35759
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:2.x,3.x,4.0,5.x,6.0,6.2,6.21,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 2.11, 3.1, 3.2, 3.21, 3.3, 3.3a, 4.0, 5.0, 5.0a, 6.0, 6.2, 6.21, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	MS-DOS does not reinitialize floppy disks after an interrupt 24h critical error
	(the type of error in which the default MS-DOS action is to issue the "Abort,
	Retry, Ignore, Fail" message). This can cause problems if you change disks at
	this prompt because the application that was working with the first disk has no
	idea that the disk has changed, which can cause unpredictable behavior on the
	second disk. For example, if an application has a file open on the first disk
	and the disk is changed during this critical error prompt, the application will
	continue to write and close this file on the second disk, most likely damaging
	the root directory entry of this second disk, and perhaps the one on the first
	disk as well.
	
	Thus, disks should NEVER be changed when DOS issues a critical error. Instead,
	you should (usually) select the Abort option, then re-execute the command with
	the proper disk in the drive.
	
	NOTE: This problem does not occur under MS-DOS if you load SHARE.EXE (or
	VSHARE.386 under Windows or Windows for Workgroups).
	
	Additional query words: 2.x 3.x 4.00 5.00 5.00a 6.0 6.2 6.00 6.20 6.21 6.22
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS321 kbMSDOS400 kbMSDOS320 kbMSDOS330a kbMSDOS621 kbMSDOS622 kbMSDOS620 kbMSDOS600 kbMSDOS310 kbMSDOS500 kbMSDOS330 kbMSDOS500a kbMSDOS211
	Version           : MS-DOS:2.x,3.x,4.0,5.x,6.0,6.2,6.21,6.22
	
	=============================================================================
	

{% endraw %}
