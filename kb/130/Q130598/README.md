---
layout: page
title: "Q130598: Cannot Create Folder or 8.3 Filename in All Upper Case"
permalink: /kb/130/Q130598/
---

## Q130598: Cannot Create Folder or 8.3 Filename in All Upper Case

{% raw %}

	Article: Q130598
	Product(s): Microsoft Windows 95.x Retail Product
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): kbenv kbui win95
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows 95 
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows 98 
	- Microsoft Windows 98 Second Edition 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A file or folder that you created using all uppercase letters is not displayed
	with all uppercase letters in Windows Explorer, on the desktop, or in
	Windows-based programs.
	
	CAUSE
	=====
	
	For readability purposes, Windows displays the names of files and folders with
	only the first letter capitalized.
	
	RESOLUTION
	==========
	
	To resolve this behavior, use either of the following methods:
	
	Method 1
	--------
	
	To create a file name that will be displayed in all uppercase letters, include an
	extended character (such as a comma or space) in the filename. This creates a
	file name that does not adhere to the 8.3 standard, and causes Windows to
	preserve the capitalization of the filename as you typed it.
	
	For example, if you create a file called FILENAME.EXT, the file name is displayed
	as Filename.ext. However, if you create a file called FILENAM,.EXT, the file
	name is displayed as FILENAM,.EXT. The comma in the file name causes the file
	name to be read as a long filename.
	
	If you create a file name using mixed uppercase and lowercase letters, the case
	of the individual letters is preserved. For example, FileName.Ext is displayed
	as you created it.
	
	Method 2
	--------
	
	1. Click Start, point to Settings, and then click Folders & Icons.
	
	2. Click the View tab.
	
	3. Under Files And Folders, click the Allow All Uppercase Names check box to
	  select it, and then click OK.
	
	If "Allow All Uppdercase Names" is not available on Windows 95 or Windows NT 4.0,
	you may need to install the Windows Desktop Update shell. This components was
	included with Internet Explorer 4. For information on adding the Windows Desktop
	Update, please see the following Microsoft Knowledge Base article:
	
	  Q165659 How to Add or Remove Windows Desktop Update
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	The MS-DOS 8.3 file name standard describes file and folder names that contain a
	maximum of eight characters and an optional extension with a maximum of three
	characters. The MS-DOS 8.3 file name standard does not allow extended characters
	(such as commas or spaces). In Windows, long file names can include up to 250
	characters, and can include extended characters such as commas or spaces.
	
	MS-DOS, by default, converts all the characters in file names and directory names
	to uppercase characters. Because Windows cannot determine whether a file or
	folder was created with a previous operating system or was intentionally created
	with all uppercase characters, it was decided for readability purposes to have
	Windows display all 8.3 file names with only the first letter capitalized.
	
	For example, if you create a file called FILENAME.EXT in MS-DOS, the file name
	appears in MS-DOS and Windows 3.x as FILENAME.EXT. In Windows 95 and Windows NT,
	the same file appears as Filename.ext in Windows Explorer, on the desktop, and
	in Windows-based programs.
	
	Note that when you view files in a Windows 95 or Windows NT MS-DOS session, you
	see two file names for each file. The first file name is an 8.3 alias and the
	second file name is the long file name.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbui win95 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWin95search kbWin98search kbWin98SEsearch kbZNotKeyword3 kbWin98 kbWin98SE
	Version           : :4.0
	
	=============================================================================
	

{% endraw %}
