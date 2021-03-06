---
layout: page
title: "Q173616: Update.exe Does Not Copy All Windows 3.x Client Files"
permalink: /kb/173/Q173616/
---

## Q173616: Update.exe Does Not Copy All Windows 3.x Client Files

{% raw %}

	Article: Q173616
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0 SP1
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, version 3.0 SP1 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The SNA Windows 3.x client Update.exe program included in SNA Server 3.0 Service
	Pack 1 does not overwrite the existing SNA Server client files located in the
	<winroot>\System directory.
	
	The following SNA Server Windows 3.x client files are copied to the
	<winroot>\system directory by the SNA client setup program, but are not
	updated when you applying Service Pack 1:
	
	  Appcstr.dll
	  Bvcli.dll
	  Csvstr.dll
	  Ctl3d.dll
	  Ehnappc.dll
	  Fmistr.dll
	  Ipcli.dll
	  Lmcli.dll
	  Luastr.dll
	  Nbcli.dll
	  Nwcli.dll
	  Snands16.dll
	  Toolhelp.dll
	  Trnsdt.dll
	  Trnsdtj.dll
	  Trnsdtk.dll
	  Trnsdts.dll
	  Trnsdtt.dll
	  Wdmod.dll
	  Winappc.dll
	  Wincpic.dll
	  Wincsv.dll
	  Winmgt.dll
	  Winsli.dll
	  Wintrc.dll
	  Wlogtr.dll
	  Ymgr.dll
	
	Because these files are not updated when Service Pack 1 is applied, problems that
	were resolved in the service pack related to the Windows 3.x may continue to
	occur after the service pack is applied. If this occurs, check the size and
	time/date stamps on these files to verify whether they are the original files
	installed with version 3.0 of the Windows 3.x client.
	
	  SNA Windows 3.x client version 3.0
	  ----------------------------------
	
	  Time Stamp: 3:00 AM
	  Date Stamp: 11/18/96
	
	Note: Taken from the Clients\Win3x\System directory on the SNA Server 3.0 compact
	disc.
	
	  SNA Windows 3.x client version 3.0 Service Pack 1 (SP1)
	  -------------------------------------------------------
	
	  Time Stamp: 3:01 AM
	  Date Stamp: 4/9/97
	
	NOTE: Taken from the Clients\Win3x\System directory on the SNA Server 3.0 SP1
	compact disc.
	
	CAUSE
	=====
	
	The UPDATE.INI file that is read by the UPDATE.EXE program incorrectly specifies
	!overwrite for the client files that are to be copied into the
	<winroot>\system directory. The !overwrite parameter specifies that the
	files should not be overwritten if they already exist.
	
	WORKAROUND
	==========
	
	To work around this problem, do one of the following three workarounds:
	
	- Manually copy the files listed above from the Client\Win3x\System directory
	  on the SP1 compact disc to the <Winroot>\System directory.
	
	  -OR-
	
	1. Copy the Clients\Win3x directories to a hard disk drive and modify the
	  Update.ini file to change !overwrite parameter to overwrite for the files
	  listed above. These files are listed after the following line in the
	  Update.ini file:
	
	  ; Windows System Files
	
	2. Save the changes. To reapply the service pack, run the Update.exe program on
	  each of the clients that use the SNA Windows 3.x Client.
	
	  -OR-
	
	- Install the SNA Windows 3.x client from the SNA Server 3.0 Refresh compact
	  disc that includes Service Pack 1.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the SNA Windows 3.x Client
	version 3.0 Service Pack 1 (SP1). This problem was corrected in the latest SNA
	Server version 3.0 U.S. Service Pack. For information on obtaining this Service
	Pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	Additional query words:
	
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300SP1
	Version           : WINDOWS:3.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
