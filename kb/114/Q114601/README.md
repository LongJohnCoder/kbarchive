---
layout: page
title: "Q114601: PRB: dmPrintQuality Does Not Affect Text Print Quality"
permalink: /kb/114/Q114601/
---

## Q114601: PRB: dmPrintQuality Does Not Affect Text Print Quality

{% raw %}

	Article: Q114601
	Product(s): Microsoft Windows Software Development Kit
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kb16bitonly kbOSWin310 _IK kbSDKWin16
	Last Modified: 09-JUL-1999
	
	3.00 3.10
	WINDOWS
	kbprg kbprb docerr
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) 3.1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	An application is able to change printer settings such as paper orientation
	without requiring user intervention, but the same method does not work to change
	the print quality of text from Letter Quality (LQ) or Near Letter Quality (NLQ)
	to draft. The ExtDeviceMode() function is used to attempt this change through
	the dmPrintQuality member of the DEVMODE structure.
	
	Please see the MORE INFORMATION section below for details about how the
	dmPrintQuality member of the DEVMODE structure, the DRAFTMODE printer escape,
	and the selection in the Print Quality combobox in the Print Options dialog box,
	affect the "draft" mode or "quality" of printed output.
	
	CAUSE
	=====
	
	This is a limitation of the standard DEVMODE structure. There is no programmable
	way to change the text print quality (from LQ/NLQ to draft or vice versa)
	without user intervention because it is not in the standard DEVMODE structure.
	
	With printer drivers that offer a Letter Quality/Draft option, such as most
	Unidrv-based dot-matrix printer drivers, the user can change the text print
	quality from the Printers applet in Control Panel as follows:
	
	1. select the printer
	
	2. Choose Setup
	
	3. Choose Options
	
	4. Select Letter Quality or Draft from the Print Quality combo box
	
	An application can allow the user to change this in the same manner by using the
	DM_PROMPT (or DM_IN_PROMPT) flag for the fwMode parameter of ExtDeviceMode().
	This will bring up the Print Setup dialog box and the user can then choose
	Options and then select the desired print quality.
	
	An exception to this is the IBM Proprinter Unidrv-based printer drivers. The
	Proprinters are dot-matrix printers but they do not provide a print quality
	choice through the Print Options dialog box.
	
	STATUS
	======
	
	This feature is under consideration for a future release of Microsoft Windows.
	
	MORE INFORMATION
	================
	
	There are three types of "draft" settings that affect the appearance or
	"quality" of printed output. They are not clearly explained in the SDK
	documentation:
	
	dmPrintQuality
	--------------
	
	dmPrintQuality controls the graphics resolution only. If the application sets
	draft mode by setting the dmPrintQuality member of the DEVMODE structure to
	DMRES_DRAFT, it means the driver should print graphics in the lowest possible
	resolution for that device. For example, a laser printer that offers the choice
	of 300, 150, or 75 dpi resolution will be set to 75 dpi. A dot-matrix printer
	that supports 240x144, 120x144, and 120x72 dpi will be set to 120x72 dpi. Text
	is not affected by this setting, unless the text is printed as graphics.
	
	DRAFTMODE
	---------
	
	If the application sets draft mode by calling the DRAFTMODE printer escape, it
	means the driver should print text only. It will not print graphics.
	
	
	Print Quality
	-------------
	
	If the user selects Draft from the Print Quality list in the Print Options dialog
	box as discussed in this article, then the driver will tell the printer to print
	text in draft mode. Graphics are not affected by this setting.
	
	REFERENCES
	==========
	
	For additional information about selecting a draft font with a Proprinter
	driver, please see the following article in the Microsoft Knowledge Base:
	
	  Q86269 PRB: IBM Proprinter Draft Mode Unavailable Under Windows 3.1
	
	For additional information about the proper use of the ExtDeviceMode() function,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q112641 SAMPLE: Using ExtDeviceMode() to Modify Printer Settings
	
	Additional query words: 3.00 3.10 docerr Epson Okidata Deskjet NEC Pinwriter fail fails DM_PRINTQUALITY DM_YRESOLUTION
	
	======================================================================
	Keywords          : kb16bitonly kbOSWin310 _IK kbSDKWin16 
	Technology        : kbAudDeveloper kbWin3xSearch kbSDKSearch kbWinSDKSearch kbWinSDK310
	Version           : WINDOWS:3.1
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
