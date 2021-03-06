---
layout: page
title: "Q67709: System Bitmaps Available Through LoadBitmap() Data"
permalink: /kb/067/Q67709/
---

## Q67709: System Bitmaps Available Through LoadBitmap() Data

{% raw %}

	Article: Q67709
	Product(s): Microsoft Windows Software Development Kit
	Version(s): 
	Operating System(s): 
	Keyword(s): kbfile kbsample kb16bitonly kbOSWin310 kbDSupport kbOSWin300 kbSDKWin16
	Last Modified: 09-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows Software Development Kit (SDK) for Windows 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	All Windows version 3.0 and 3.1 display drivers are required to contain certain
	bitmaps. These bitmaps are used to paint various windows, controls, and menus.
	Handles to these bitmaps can be retrieved with the LoadBitmap() function. Below
	is an explanation of the OBM values listed in the Windows include file
	WINDOWS.H.
	
	These values are parsed by the C Compiler only if OEMRESOURCE is defined prior to
	including WINDOWS.H.
	
	MORE INFORMATION
	================
	
	The following file is available for download from the Microsoft Download
	Center:
	
	  Sysbit.exe
	  (http://download.microsoft.com/download/platformsdk/file71/3.1/W31/EN-US/SYSBIT.EXE)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	Because Windows buttons have two states, normal and depressed (the mouse pointer
	is over the icon and the mouse button is down), the first seven shapes (bitmaps)
	have two forms, the normal image and the depressed image. Both images are used
	to create the illusion of three dimensions on the screen when a button is
	pressed. The names of depressed images end with the letter "D"; the other images
	do not.
	
	The last eleven bitmaps are no longer used by Windows, but must be supplied for
	compatibility with applications that expect them to be available.
	
	Windows 3.1 Bitmaps
	-------------------
	
	The following four bitmaps are new for Windows 3.1:
	
	  NOTE: The SYSBIT sample does not display these bitmaps, but they are
	  illustrated in the documentation (as are the rest of the bitmaps listed
	  below) for the LoadBitmap() function in the Windows SDK.
	
	  Resource Name     Purpose
	  ---------------------------------------------------------------------
	  OBM_DNARROWI      A disabled down-pointing arrow for scroll bars.
	  OBM_LFARROWI      A disabled left-pointing arrow for scroll bars.
	  OBM_RGARROWI      A disabled right-pointing arrow for scroll bars.
	  OBM_UPARROWI      A disabled up-pointing arrow for scroll bars.
	
	Windows 3.00 Bitmaps
	--------------------
	
	  Resource Name       Purpose
	  -------------       -------
	
	  OBM_RESTORE         Images used as the restore button on the title
	  OBM_RESTORED        bar. This is the button with both an up and
	                      down arrow which is only shown when a window is
	                      maximized.
	
	  OBM_REDUCE          Images used as the minimize button on the title
	  OBM_REDUCED         bar.
	
	  OBM_ZOOM            Images used as the maximize button on the title
	  OBM_ZOOMD           bar.
	
	  OBM_RGARROW         A right-pointing arrow for scroll bars.
	  OBM_RGARROWD
	
	  OBM_LFARROW         A left-pointing arrow for scroll bars.
	  OBM_LFARROWD
	
	  OBM_UPARROW         An up-pointing arrow for scroll bars.
	  OBM_UPARROWD
	
	  OBM_DNARROW         A down-pointing arrow for scroll bars.
	  OBM_DNARROWD
	
	  OBM_CLOSE           A double-wide image that contains system menu
	
	                      box shapes for both main windows and MDI child
	                      windows.
	
	  OBM_CHECK           A check mark used to check menu items.
	
	  OBM_CHECKBOXES      Ten images that are used to show different
	
	                      states of check boxes and radio buttons. The
	                      images are organized in three rows of four
	                      columns:
	
	     Row 1
	     -----
	
	     Column 1:  Unchecked check box when the mouse is not pressed
	                over it.
	
	     Column 2:  Checked check box when the mouse is not pressed over
	                it.
	
	     Column 3:  Unchecked check box when the mouse is pressed over
	                it.
	
	     Column 4:  Checked check box when the mouse is pressed over it.
	
	     Row 2
	     -----
	
	     Column 1:  Unchecked radio button when the mouse is not pressed
	                over it.
	
	     Column 2:  Checked radio button when the mouse is not pressed
	                over it.
	
	     Column 3:  Unchecked radio button when the mouse is pressed over
	                it.
	
	     Column 4:  Checked radio button when the mouse is pressed over
	                it.
	
	     Row 3:
	     -----
	
	     Column 1:  Unused
	
	     Column 2:  Grayed check box when the mouse is not pressed over
	                it.
	
	     Column 3:  Unused
	
	     Column 4:  Grayed check box when the mouse is pressed over it.
	
	  OBM_COMBO           An arrow used for the push button in combo
	                      boxes.
	
	  OBM_MNARROW         An arrow used to designate cascaded menu items.
	
	Windows 1.x/2.x Bitmaps
	-----------------------
	
	  Resource Name       Purpose
	  -------------       -------
	
	  OBM_SIZE            A size box formerly used on tiled windows.
	
	  OBM_BTSIZE          A size box formerly used at the intersection of
	                      vertical and horizontal scroll bars.
	
	  OBM_OLD_RESTORE     Image used for the Windows 2.x restore button
	                      on a windows title bar.
	
	  OBM_OLD_REDUCE      Image used for the Windows 2.x minimize button
	                      on a windows title bar.
	
	  OBM_OLD_ZOOM        Image used for the Windows 2.x maximize button
	                      on a windows title bar.
	
	  OBM_OLD_RGARROW     A right-arrow bitmap used for Windows 2.x
	                      scroll bars.
	
	  OBM_OLD_LFARROW     A left-arrow bitmap used for Windows 2.x scroll
	                      bars.
	
	  OBM_OLD_UPARROW     An up-arrow bitmap used for Windows 2.x scroll
	                      bars.
	
	  OBM_OLD_DNARROW     A down-arrow bitmap used for Windows 2.x scroll
	                      bars.
	
	  OBM_OLD_CLOSE       The system menu bitmaps used for Windows 2.x.
	
	  OBM_BTNCORNERS      Small circles that Windows 2.x used to draw
	                      rounded corners on button controls.
	
	Additional query words: softlib SYSBIT
	
	======================================================================
	Keywords          : kbfile kbsample kb16bitonly kbOSWin310 kbDSupport kbOSWin300 kbSDKWin16 
	Technology        : kbAudDeveloper kbSDKSearch kbWinSDKSearch
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
