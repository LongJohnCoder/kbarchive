---
layout: page
title: "Q117668: Err Msg: Ring 0 Systems. Virtual 16550 Driver..."
permalink: /kb/117/Q117668/
---

## Q117668: Err Msg: Ring 0 Systems. Virtual 16550 Driver...

{% raw %}

	Article: Q117668
	Product(s): Microsoft Windows 3.x Retail Product
	Version(s): 3.1,3.11
	Operating System(s): 
	Keyword(s): win31
	Last Modified: 08-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows for Workgroups versions 3.1, 3.11 
	- Microsoft Windows versions 3.1, 3.11 
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	You receive the following error message when you start Windows:
	
	  Ring 0 Systems. Virtual 16550 Driver Board was not found in computer. Virtual
	  16550 & communication buffering in the DOS box will not work. It may
	  cause lost bytes during the data transfer and other problems with
	  communication software running under V86 DOS
	
	CAUSE
	=====
	
	This error occurs when you:
	
	- Move your modem to another serial port without reconfiguring the driver.
	
	  -or-
	
	- Remove the modem from the computer but do not remove the corresponding
	  Digicom Systems Incorporated (DSI) device driver (r0dsicom.drv). This device
	  driver replaces COMM.DRV as the Windows serial communications driver and
	  displays the error message noted above when it doesn't find the modem.
	
	The following modems use DSI-written device drivers:
	
	- Boca Sound Expression 14.4 VSP
	
	- Cardinal Technologies MVP144DSP
	
	- DSI Connection Series
	
	- PC Logic FAX144DM
	
	
	WORKAROUND
	==========
	
	- If you move the modem to another serial port, run the DSI.EXE program
	  included with the modem to reconfigure the adapter. Contact DSI for more
	  information and assistance.
	
	- If the modem has been removed, the DSI drivers should be replaced with the
	  default Windows drivers to remove the error message.
	
	  The DSI setup program makes the following changes in the [boot] section of the
	  SYSTEM.INI file:
	
	       COMM.DRV=r0dsicom.drv
	
	  To replace this DSI driver, change this line to read as follows:
	
	       COMM.DRV=COMM.DRV
	
	  The following changes are made to the [386Enh] section of the SYSTEM.INI file
	  by the DSI setup program:
	
	        DEVICE= r0dsivcd.386
	        DEVICE= r0dsibuf.386
	        DEVICE= r0dsimgr.386
	
	
	  Remark out or remove the above three lines and add the following to the
	  [386Enh] section:
	
	        DEVICE=*VCD
	        DEVICE=*combuff
	
	  NOTE: The Connection Series modems require the drivers outlined above for full
	  functionality. You should not replace the DSI drivers listed above unless the
	  DSI modem is removed from the system. Contact DSI for more information.
	
	
	MORE INFORMATION
	================
	
	The products included here are manufactured by vendors independent of Microsoft;
	we make no warranty, implied or otherwise, regarding these products' performance
	or reliability.
	
	Additional query words: ring zero one softmodem cardinal win95 win95x
	
	======================================================================
	Keywords          : win31 
	Technology        : kbAudDeveloper kbWin3xSearch kbWin95search kbWFWSearch kbZNotKeyword3 kbWin310 kbWin311 kbWFW310 kbWFW311
	Version           : :3.1,3.11
	
	=============================================================================
	

{% endraw %}
