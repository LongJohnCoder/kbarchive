---
layout: page
title: "Q195665: Error Message: Filename Is Linked to Missing Export Filename.dll"
permalink: /kb/195/Q195665/
---

## Q195665: Error Message: Filename Is Linked to Missing Export Filename.dll

{% raw %}

	Article: Q195665
	Product(s): Microsoft Home Multimedia Titles
	Version(s): 1.0
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbsetup kburl kbimukbfaq
	Last Modified: 26-JUL-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Encarta Encyclopedia Deluxe 2003 
	- Microsoft Encarta Encyclopedia Standard 2003 
	- Microsoft Encarta Encyclopedia 2000 
	- Microsoft Encarta Encyclopedia 99 
	- Microsoft Encarta Interactive World Atlas 2000 
	- Microsoft Encarta Reference Library 2003, version 1.0 
	- Microsoft Encarta Reference Library 2003 - DVD Edition 
	- Microsoft Encarta Reference Suite 2000 
	- Microsoft Encarta Reference Suite 99 
	- Microsoft Encarta Virtual Globe 99 
	- Microsoft Expedia Streets and Trips 2000 
	- Microsoft MapPoint 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to start one of the programs listed earlier in this article,
	you may receive one or more of the following error messages:
	
	   - C:\Program Files\Microsoft Reference\Encarta Encyclopedia 99\Enc99.exe
	
	  A device attached to the system is not functioning.
	
	   - Eeuil12.dll is linked to missing export file Mfc42.dll.
	
	   - Msvcp60.dll is linked to missing export file Msvcrt.dll.
	
	   - Shrl11.dll is linked to missing export file Mfc42.dll.
	
	   - C:\Program Files\Microsoft Encarta\Encarta Encyclopedia 2000\Enc2000.exe
	
	  A device attached to the system is not functioning.
	
	   - C:\Program Files\Microsoft Encarta\Encarta Encyclopedia 2003\Encarta.exe
	
	  A device attached to the system is not functioning.
	
	   - C:\Program Files\Microsoft Encarta\Encarta Interactive World Atlas
	  2000\Msworld5.exe
	
	  A device attached to the system is not functioning.
	
	   - Error Starting Program
	
	  The Shrl30.dll file is linked to missing export Mfc42.dll:6571.
	
	   - Error Starting Program
	
	  The Shrpnl10.dll file is linked to missing export file Mfc42.dll:6467.
	
	CAUSE
	=====
	
	This behavior can occur if the Mfc42.dll or Msvcrt.dll files are missing or
	damaged, or the wrong version of either file is installed.
	
	RESOLUTION
	==========
	
	To resolve this issue, remove the program, clean boot Windows, and then
	reinstall the program. To do this:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Add/Remove Programs.
	
	3. Click the program you want to remove, and then click Add/Remove.
	
	  NOTE: When you remove Encarta Reference Suite 99, you remove all of the
	  programs listed earlier in this article.
	
	4. Follow the instructions on the screen to remove the program. If you are
	  prompted to restart the computer, do so.
	
	5. Repeat steps 1-4 to remove any other programs.
	
	6. Start Windows without loading any terminate-and stay-resident (TSR) programs,
	  other memory-resident programs running in the background, or device drivers
	  (this is called a clean boot). For more information about how to do this, use
	  the appropriate method for your version of Windows in the "More Information"
	  section later in this article.
	
	7. Insert the installation CD-ROM for the program into the CD-ROM drive, and
	  then follow the instructions on the screen to install the program. If you are
	  prompted to restart the computer, do so. Repeat this step for each program
	  you want to reinstall.
	
	  NOTE: When you reinstall Encarta Reference Suite 99, you reinstall all of the
	  programs listed earlier in this article.
	
	If the issue continues to occur, download and install the Windows Libraries
	Update. To do this:
	
	1. Visit the following Microsoft Web site:
	
	  http://www.microsoft.com/downloads/search.asp?
	
	2. In the Search By area, click Keywords.
	
	3. In the Keywords box, type "libraries update" (without the quotation marks).
	
	4. In the Operating System box, click the appropriate operating system, and then
	  click Find It.
	
	5. Click the link that is returned, and then follow the instructions on the
	  screen to install the Microsoft Libraries Update.
	
	The Microsoft Libraries Update resolves an issue that can cause some third-party
	software to behave unexpectedly after the installation of Microsoft Works Suite
	99, Microsoft Encarta Encyclopedia 99 (US only), Microsoft Encarta Virtual Globe
	99, Microsoft Graphics Studio Greetings 99, or other third-party software.
	Impacted programs include America Online (AOL) version 4.0 and HyperTerminal.
	
	For additional information about the Microsoft Libraries Update, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q197298 INFO: Microsoft Libraries Update: What, Where, Why
	
	
	MORE INFORMATION
	================
	
	How to Clean Boot Windows 98
	----------------------------
	
	The System Configuration Utility tool (Msconfig.exe) is a new tool in Windows 98
	that makes a clean boot much easier to perform. To use the System Configuration
	Utility tool to perform a clean boot in Windows 98, follow these steps:
	
	1. Click Start, point to Programs, point to Accessories, point to System Tools,
	  and then click System Information.
	
	2. On the Tools menu, click System Configuration Utility.
	
	3. On the General tab, click Selective Startup, and then click to clear the
	  following check boxes:
	
	   - Process Config.sys File
	   - Process Autoexec.bat File
	   - Process Winstart.bat File (if available)
	   - Process Win.ini File
	   - Load Startup Group Items
	
	4. Click OK, and then restart your computer when you are prompted to do so.
	
	NOTE: To restore your original configuration, click Normal Startup on the General
	tab in the System Configuration Utility tool.
	
	How to Clean Boot Windows 95
	----------------------------
	
	To clean boot Microsoft Windows 95, follow these steps:
	
	1. Restart the computer. When you see the "Starting Windows 95" message, press
	  the F8 key, and then select Command Prompt Only on the Startup menu.
	
	2. At the command prompt, type "win" (without the quotation marks), and then
	  press ENTER. Press and hold down the SHIFT key until the Windows startup
	  process is finished. This prevents any programs from loading automatically
	  when Windows starts.
	
	3. Quit all running programs except Explorer and Systray. To do this, follow
	  these steps:
	
	  a. Press CTRL+ALT+DELETE.
	
	  b. Click the program you want to quit, and then click End Task.
	
	  c. If you receive a message that the program is busy or not responding, click
	     End Task again.
	
	  Repeat this step until you have quit all programs except Explorer and Systray.
	
	4. Disable any anti-virus or disk tool programs installed on the computer. For
	  information about how to disable these programs, see the printed or online
	  documentation for the program.
	
	Additional query words: 1.00 multi multi-media media mm world atlas evg
	
	======================================================================
	Keywords          : kbenv kberrmsg kbsetup kburl kbimu kbfaq
	Technology        : kbHomeProdSearch kbHomeMMsearch kbEncartaSearch kbExpediaSearch kbMapptSearch kbEncartaEncycSearch kbMapPoint2000 kbExpediaStreets2000 kbEncartaEnCyc2000 kbEncartaEnCyc1999 kbEncartaReference99 kbEncartaReference2000 kbEncartaVirtGlobe99 kbEncartaWorldAtlas2000
	Version           : :1.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
