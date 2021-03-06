---
layout: page
title: "Q153296: Write Cache on IDE/ATAPI Disks Is Not Flushed on Shut Down"
permalink: /kb/153/Q153296/
---

## Q153296: Write Cache on IDE/ATAPI Disks Is Not Flushed on Shut Down

{% raw %}

	Article: Q153296
	Product(s): Microsoft Windows NT
	Version(s): 3.51,4.0
	Operating System(s): 
	Keyword(s): kberrmsg kbWinNT400sp4fix
	Last Modified: 17-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows NT Workstation versions 3.51, 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If your computer supports the shut down and power down feature, you may
	experience one of the following problems:
	
	- CHKDSK runs as your computer starts and reports a dirty volume.
	
	- A blue screen appears and displays the following message:
	
	  STOP 0x0000007B (parameter, parameter, parameter, parameter)
	  INACCESSIBLE_BOOT_DEVICE
	
	CAUSE
	=====
	
	Recent versions of IDE/ATAPI hard disk drives include a write cache. This cache
	is normally flushed automatically depending on an algorithm by the hard disk
	manufacturer. On computers that support the shut down and power down feature,
	the power may turn off before the write cache is flushed.
	
	RESOLUTION
	==========
	
	Windows NT 4.0
	--------------
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	For your convenience, the English version of this post-SP3 hotfix has been posted
	to the following Internet location. However, Microsoft recommends that you
	install Windows NT 4.0 Service Pack 4 to correct this problem.
	
	  ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/NT40/hotfixes-postSP3/ide-fix
	
	Windows NT 3.51
	---------------
	
	To resolve this, apply the fix mentioned below or wait for the next service
	pack.
	
	This hotfix has been posted to the following Internet location:
	
	  ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/NT351/hotfixes-postSP5/ide-fix
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. A
	supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	MORE INFORMATION
	================
	
	The IDE/ATAPI specification does not define a command to determine if a write
	cache is present or to explicitly flush the cache. The Windows NT file system
	drivers modify the boot sector on startup to indicate a dirty volume. On shut
	down, the last operation is to modify the boot sector again to mark the volume
	clean. This last write is cached in the cache of the disk. If the power is
	removed too early, this sector is not written at all and the volume is still
	marked dirty. If the power disappears during the physical write to the disk, the
	boot sector is corrupt and the blue screen occurs.
	
	
	Additional query words: 3.51 4.00
	
	======================================================================
	Keywords          : kberrmsg kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT400search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbNTTermServ400 kbNTTermServSearch kbWinNTS351search
	Version           : :3.51,4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
