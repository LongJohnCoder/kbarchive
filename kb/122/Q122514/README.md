---
layout: page
title: "Q122514: MS-DOS Window Remains on Screen After Application Is Finished"
permalink: /kb/122/Q122514/
---

## Q122514: MS-DOS Window Remains on Screen After Application Is Finished

{% raw %}

	Article: Q122514
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 95
	Operating System(s): 
	Keyword(s): win95 appscomp kbAppCompatibility
	Last Modified: 28-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you are running an MS-DOS-based application from an icon in Windows 95, the
	MS-DOS window remains open with the text "Finished - <Application Name>"
	appearing on the title bar after the application has finished executing.
	
	CAUSE
	=====
	
	The MS-DOS window remains open so that you can see any messages, such as errors,
	that may be generated by the MS-DOS-based application. This window appears for
	any MS-DOS-based application that generates output.
	
	RESOLUTION
	==========
	
	You can change the program properties for the MS-DOS-based application so that
	it closes on exit. To do this:
	
	1. Use the right (secondary) mouse button to click the icon for the MS-DOS-based
	  application.
	
	2. Click Properties.
	
	3. Click the Program tab.
	
	4. Click Close On Exit to select that option.
	
	5. Click OK to accept the settings.
	
	The MS-DOS-based application window should now close after the application has
	finished executing. You must change this setting for each MS-DOS-based
	application individually--there is no way to set this option globally.
	
	Note, however, that you can set this option globally for all MS-DOS-based
	programs that do not already have their own PIF (program information file). To
	do this, create a default PIF with the setting listed above. For information
	about creating a default PIF, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q131877 How to Create Default PIF for MS-DOS-Based Programs
	
	MORE INFORMATION
	================
	
	If you are running a batch file, you can close the MS-DOS window by adding the
	following lines to the end of the batch file:
	
	  echo off
	  cls
	
	Additional query words: 3rdparty
	
	======================================================================
	Keywords          : win95 appscomp kbAppCompatibility 
	Technology        : kbWin95search kbZNotKeyword3
	Version           : 95
	
	=============================================================================
	

{% endraw %}
