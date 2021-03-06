---
layout: page
title: "Q159440: FP: Early Versions of Web Publishing Wizard Damage Extensions"
permalink: /kb/159/Q159440/
---

## Q159440: FP: Early Versions of Web Publishing Wizard Damage Extensions

{% raw %}

	Article: Q159440
	Product(s): Word Front Page
	Version(s): windows:1.1,97
	Operating System(s): 
	Keyword(s): kbusage kbdta
	Last Modified: 04-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows with Bonus Pack 
	- Microsoft FrontPage for Windows 1.1 
	- Microsoft Web Publishing Wizard, versions 1.0, 1.0a 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 98 version of this article, see Q194260.
	
	SYMPTOMS
	========
	
	If you use version 1.0 or 1.0a of the Microsoft Web Publishing Wizard to post
	files from a FrontPage Web to a FrontPage extended Web server, the FrontPage
	Server Extensions on the Web server may become damaged.
	
	CAUSE
	=====
	
	This problem occurs with Microsoft Web Publishing Wizard versions 1.0 and 1.0a.
	These versions of the wizard may overwrite the server extensions on the
	destination server.
	
	RESOLUTION
	==========
	
	If a FrontPage Web has been posted to a FrontPage Web server using a version of
	the Microsoft Web Publishing Wizard earlier than version 1.1, you must uninstall
	and then re-install the FrontPage Server Extensions on the server.
	
	Once you have reinstalled the extensions on the server, use either of the
	following methods to post a FrontPage Web to a FrontPage server.
	
	Method 1: Use Microsoft Web Publishing Wizard Version 1.1
	---------------------------------------------------------
	
	This version of the wizard includes a driver that allows the Web Publishing
	Wizard to connect to and safely transfer data using the HTTP protocol.
	
	You can determine if you have version 1.1 of the Web Publishing Wizard by
	checking the modification date and file size of the following files:
	
	  File name:   Wpwiz.exe
	  Modified date: Wednesday, November 12, 1996 5:28:27 PM
	  File size:   10,114 KB
	
	  File name:   Fpwpp.dll
	  Modified date: Monday, October 07, 1996 7:38:42 AM
	  Size:     106,496 KB
	
	
	The unexpanded version of the 1.1 Microsoft Web Publishing Wizard is named
	Webpost.exe and it is version 4.71.0121.0.
	
	Method 2: If You Must Use an Earlier Version of the Wizard
	----------------------------------------------------------
	
	If you must use an earlier version of the Microsoft Web Publishing Wizard without
	FrontPage to transport files to a server with FrontPage Server Extensions, use
	the following guidelines:
	
	- Copy only individual files.
	- Do not transfer any file from a directory if the file name begins with the
	  "_vti_" prefix.
	- After you publish the files, follow these steps:
	
	  1. From FrontPage Explorer, open the Web on the destination server.
	
	  2. On the Tools menu, click Recalculate Hyperlinks.
	
	MORE INFORMATION
	================
	
	FrontPage Server Extensions are created and compiled for specific Web servers on
	a particular operating system. The Microsoft Web Publishing Wizard is a
	stand-alone program that can post files to any Web server with which the client
	has either an FTP or a Windows file sharing network connection.
	
	The Microsoft Web Publishing Wizard version 1.1 is a component of the FrontPage
	97 bonus pack. When the Publishing Wizard is installed, FrontPage starts it
	automatically when you attempt to publish a FrontPage Web to a destination
	server that does not have the FrontPage Server Extensions installed.
	
	The recommended way to publish any FrontPage Web is to click Publish FrontPage
	Web on the File menu in FrontPage Explorer. If you use FrontPage to publish to a
	Web server that does not have the FrontPage Server Extensions installed,
	FrontPage automatically starts the Microsoft Web Publishing Wizard (if it is
	installed) and passes it the list of files to post by creating a directory
	called "upload" (for example, c:\program files\Microsoft FrontPage\temp\upload).
	This directory contains only the files that should be posted (for example, you
	can specify to post only files that have been changed since the last time you
	posted the Web).
	
	For more information about the Microsoft Web Publishing Wizard, see the Microsoft
	Web site at:
	
	  http://corporate.windowsupdate.microsoft.com/
	
	Additional query words: 97
	
	======================================================================
	Keywords          : kbusage kbdta 
	Technology        : kbFrontPageSearch kbFrontPage1xSearch kbFrontPage97Search kbZNotKeyword3 kbWebPubWizardSearch kbFrontPage110
	Version           : windows:1.1,97
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
