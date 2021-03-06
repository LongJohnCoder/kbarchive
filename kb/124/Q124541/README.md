---
layout: page
title: "Q124541: Use UPTOMP.EXE to Upgrade Single-Processor to Multiprocessor"
permalink: /kb/124/Q124541/
---

## Q124541: Use UPTOMP.EXE to Upgrade Single-Processor to Multiprocessor

{% raw %}

	Article: Q124541
	Product(s): Microsoft Windows NT
	Version(s): winnt:3.5,3.51,4.0
	Operating System(s): 
	Keyword(s): kbtool
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0 
	- Microsoft Windows NT Server versions 3.5, 3.51, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	To upgrade a single-processor system to a multiprocessor system, use Uptomp.exe.
	Uptomp.exe is included in the Resource Kit for Windows NT version 3.5. This tool
	is located under Performance and System Monitoring Tools in Resource Kit Tools
	Help.
	
	
	MORE INFORMATION
	================
	
	The following list contains the computer models that appear in the Uptomp.exe
	tool and the associated HAL files included in Windows NT.
	
	Note that the latest versions of these files are included in the Windows NT
	Service Packs. If you have installed a Service Pack, you should use the
	appropriate file from the Service Pack.
	
	  halast.dll    = "AST Manhattan SMP"
	  halsp.dll     = "Compaq SystemPro Multiprocessor or 100% Compatible"
	  halcbus.dll   = "Corollary C-bus Architecture"
	  halmca.dll    = "IBM PS/2 or other Micro Channel-based PC"
	  halapic.dll   = "MPS Uniprocessor PC"
	  halmps.dll    = "MPS Multiprocessor PC"
	  halncr.dll    = "NCR System 3000 Model 3360/3450/3550"
	  haloli        = "Olivetti LSX5030/40"
	  hal.dll       = "Standard PC"
	  hal486c.dll   = "Standard PC with C-Step i486"
	  halwyse7.dll  = "Wyse Series 7000i Model 740MP/760MP"
	
	After Uptomp finishes, you see a dialog box informing you that the upgrade was
	successful, the system needs to be restarted for this change to take effect, and
	that you should run Rdisk after the system restarts to update the saved
	configuration. It is very important to click the "Update Repair Info" option in
	Rdisk before you click "Create Repair Disk."
	
	NOTE: If you are changing to or from single or multiple processors and you are
	using Microsoft Proxy 2.0 server on the same computer, you also need to replace
	the Ipfltdrv.sys driver (%systemroot%\system32\drivers). The single-processor
	version is 36 KB and is located on the Proxy 2.0 CD-ROM in the
	Msproxy\I386\Routing\Up folder. The multiple-processor version is 34 KB and is
	located on the Proxy 2.0 CD-ROM in the Msproxy\I386\Routing folder.
	
	
	Additional query words: prodnt
	
	======================================================================
	Keywords          : kbtool 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351search kbWinNT350search kbWinNT400search kbWinNTW350 kbWinNTW350search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : winnt:3.5,3.51,4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
