---
layout: page
title: "Q171618: Unattended Install of WinNT SP May Leave System Unbootable"
permalink: /kb/171/Q171618/
---

## Q171618: Unattended Install of WinNT SP May Leave System Unbootable

{% raw %}

	Article: Q171618
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.5,3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51 
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you install Service Pack 5 in a mass deployment for Windows NT 3.51 on
	IDE-based systems, using the following command may render you system
	unbootable:
	
	  Update.exe -u
	
	This service pack switch performs an automated installation. When the -u switch
	is used with Update.exe, it will automatically close all applications and
	restart the system after the service pack is applied.
	
	You may see one of the following behaviors:
	
	- Computer gets to the boot loader (Boot.ini) file but will stop responding
	  (hang) on Ntdetect.com (most common symptom)
	
	- Computer stops responding at the end of the POST at a black screen without
	  displaying the Windows NT Boot menu options.
	
	CAUSE
	=====
	
	This problem is caused by the IDE Drives buffers (cache) not being flushed
	properly before the computer is reset.
	
	
	RESOLUTION
	==========
	
	To recover the system after the service pack installation, follow these steps:
	
	1. Create a Windows NT boot floppy disk. For additional information, please see
	  the following article in the Microsoft Knowledge Base:
	
	  Q119467 Creating a Boot Disk for an NTFS or FAT Partition
	
	2. When booted to Windows NT, run a chkdsk /f on the system drive.
	
	  NOTE: Because this is the system partition, you will need to keep the boot
	  floppy disk in drive A so the computer can reboot and run chkdsk.
	
	3. The system should now be recovered. Verify by doing a reboot without the
	  Windows NT boot floppy disk in drive A.
	
	MORE INFORMATION
	================
	
	Prevention
	----------
	
	To keep this problem from happening with future installations of Service Pack 5,
	perform the following steps:
	
	1. Create a batch file that will call the Update.exe and Shutdown.exe (Shutdown
	  is a Windows NT Resource kit utility that will shut down the system).
	
	  For example:
	
	     SPUpdate.bat
	
	     %path%\update -u
	     %path%\shutdown /L /R /T:60 /Y /C
	
	  The above shutdown command forces a local shutdown (/L), reboots when shutdown
	  (/R), waits 60 seconds before beginning shutdown (/T:60), Answers 'yes' to
	  all prompts (/Y), and forces a close of all apps (/C). For more information
	  on the shutdown command, please see the Windows NT 3.51 Resource Kit.
	
	2. Modify the Update.inf in SP5 so that it does not automatically reboot when
	  the -u switch is used. Below is a sample of code that should be commented out
	  using a semi-colon (;) to stop the automatic reboot.
	
	          Rebootend =+
	        ;********* bypass reboot**************
	            ;exit
	            ;set Reboot = YES
	            ;ifstr(i) $(Unattended) != TRUE
	           ;install Install-Shutdown
	            ;else
	           ;ifstr(i) $(ForceClose) != TRUE
	               ;set ForceAppsClosed = NO
	           ;else
	               ;set ForceAppsClosed = YES
	           ;endif
	           ;install Install-Shutdown2
	            ;endif
	        ;**********ends here********************
	
	Additional query words: SP5 Hangs Unattended
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNT350search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : WinNT:3.5,3.51
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
