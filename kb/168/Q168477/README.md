---
layout: page
title: "Q168477: &quot;Cannot Access This Folder. Path Is Too Long&quot; Error"
permalink: /kb/168/Q168477/
---

## Q168477: &quot;Cannot Access This Folder. Path Is Too Long&quot; Error

{% raw %}

	Article: Q168477
	Product(s): Microsoft Windows NT
	Version(s): WinNT:4.0
	Operating System(s): 
	Keyword(s): kbnetwork
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 4.0 
	- Microsoft Windows NT Server version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to log on to a computer running Windows NT 4.0, you receive the
	following error:
	
	  Cannot access this folder. Path is too long.
	
	CAUSE
	=====
	
	This problem may occur if the system administrator uses System Policy Editor to
	create a policy that sets the Hide Network Neighborhood Icon option and
	specifies that Custom Shared Folders or Custom Folders use an UNC connection to
	connect to a share on a central server. The above error message occurs because
	the Hide Network Neighborhood Icon option removes the ability to use UNC names
	for connection.
	
	RESOLUTION
	==========
	
	One solution is to map the drive through a login script and change the
	specification in the Custom Shared Folders, or the Custom Folders location, to
	reference this drive letter.
	
	For example, D:\CUSTOM\Programs.
	
	To get the mapped drive to work correctly, you might have to check the box for
	"Run logon scripts synchronously" under "Windows NT System" in the policy. This
	will allow the logon script to execute before the shell is loaded.
	
	Another solution is to allow users to have the Network Neighborhood Icon on the
	desktop. Clear the check box to allow the user's policy to not hide the Network
	Neighborhood icon.
	
	Other causes of this error message include file permissions.
	
	See article Q148437 to set the NTFS permissions for the %SystemRoot% directory
	back to the system defaults.
	
	Additional query words: Policy login logon log on
	======================================================================
	Keywords          : kbnetwork 
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400
	Version           : WinNT:4.0
	
	=============================================================================
	

{% endraw %}
