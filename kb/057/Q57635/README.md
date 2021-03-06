---
layout: page
title: "Q57635: Windows DeskJet Soft Font Support"
permalink: /kb/057/Q57635/
---

## Q57635: Windows DeskJet Soft Font Support

{% raw %}

	Article: Q57635
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): WINDOWS:3.0,3.0a,3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows versions 3.0, 3.0a, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Microsoft Windows version 3.0 driver for the Hewlett-Packard (HP) DeskJet
	and DeskJet Plus printers supports the use of soft fonts. However, the driver
	does not download the soft fonts to the printer; the soft fonts must be
	downloaded prior to printing by using the standard downloading procedure (that
	is, using an MS-DOS batch file). Normally, the instruction to download the fonts
	is placed in the AUTOEXEC.BAT file.
	
	MORE INFORMATION
	================
	
	The fonts must be downloaded as "permanent" to work properly with the Windows
	3.0 DeskJet driver, because the driver resets the printer prior to each print
	job. If the fonts are not downloaded as permanent, they are erased when the
	printer is reset.
	
	When upgrading to the Microsoft Windows version 3.1 over Windows 3.0, soft fonts
	that are installed for the Hewlett-Packard (HP) DeskJet printers are not
	retained.
	
	To use the soft fonts for the HP DeskJet printers, re-install them through the
	Control Panel under Windows 3.1.
	
	Additional query words: 3.00 3.00a 3.10 win30 win31 Windrvr KBPrint hewlett packard hp upgrade setup
	
	======================================================================
	Keywords          :  
	Technology        : kbWin3xSearch kbZNotKeyword3 kbWin300 kbWin300a kbWin310
	Version           : WINDOWS:3.0,3.0a,3.1
	
	=============================================================================
	

{% endraw %}
