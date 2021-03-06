---
layout: page
title: "Q130141: HOWTO: Install SourceSafe on a Windows Client Workstation"
permalink: /kb/130/Q130141/
---

## Q130141: HOWTO: Install SourceSafe on a Windows Client Workstation

{% raw %}

	Article: Q130141
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:3.1
	Operating System(s): 
	Keyword(s): kbsetup kbusage
	Last Modified: 20-FEB-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SourceSafe for Windows, version 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article demonstrates how to install SourceSafe on a client workstation when
	the data is on a network drive.
	
	MORE INFORMATION
	================
	
	With SourceSafe for Windows installed on a network server, do the following on
	the Windows workstation:
	
	1. Create a directory structure on the local machine that looks like this:
	
	  SS
	  SS\USER
	  SS\TEMP
	
	2. Copy the *.EXE, *.DLL, and *.HLP files from the server's SS directory to the
	  local SS directory.
	
	3. Map the server where SourceSafe is installed to a named drive letter, such as
	  Z:, making sure that the Reconnect at logon box is checked. This can be done
	  using File Manager.
	
	4. In the user's AUTOEXEC.BAT file, add this line:
	
	  SET SSDIR=Z:\<Path to the \SS dir>
	
	5. Edit the USERS.TXT file to change this line:
	
	  USER_NAME=\USERS\USER_NAME\SS.INI
	
	  to this line:
	
	  USER_NAME=<local drive>\SS\USER\SS.INI
	
	6. Copy the SS.INI file from the \SS\USERS\USER_NAME\ to the local \SS\USER
	  directory.
	
	7. Edit the SS\USER\SS.INI file and add the following line:
	
	  TEMP_PATH=<local drive>:\SS\TEMP
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsetup kbusage 
	Technology        : kbSSafeSearch kbAudDeveloper kbZNotKeyword3 kbSSafe310
	Version           : WINDOWS:3.1
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
