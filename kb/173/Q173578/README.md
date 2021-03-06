---
layout: page
title: "Q173578: HOWTO: Change Local User WinNT 3.51 Profile to a Domain Profile"
permalink: /kb/173/Q173578/
---

## Q173578: HOWTO: Change Local User WinNT 3.51 Profile to a Domain Profile

{% raw %}

	Article: Q173578
	Product(s): Microsoft Windows NT
	Version(s): WinNT:3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Workstation version 3.51 
	- Microsoft Windows NT Server version 3.51 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The purpose of this article is to provide you with the information needed to
	move a Windows NT 3.5x profile from a local user to a domain user.
	
	MORE INFORMATION
	================
	
	If the profile to be edited is on a computer running Windows 3.51 Workstation,
	then the Windows NT Server 3.51 tools will need to installed on the computer
	running Windows NT Workstation in order to get access to the Profile editor
	program. Windows NT Server 3.51 tools are stored on the Windows NT Server 3.51
	CD in the client's directory.
	
	Install the programs from the MS-DOS prompt with the batch file, Setup.bat,
	located in the Clients\Srvtools\Winnt subdirectory. You will need administrative
	privileges on the local computer to complete the task.
	
	To install these programs and move the profile, perform the following steps:
	
	1. Log on to the computer as either a domain administrator or local
	  administrator at the computer running Windows NT Workstation.
	
	2. From the Windows NT Server 3.51 CD, install Server tools (they are located in
	  the Client\Srvtools\Winnt subdirectory) run the Setup.bat program in the
	  WINNT subdirectory. The system will do the rest. (Use this step if the local
	  profile is located on a computer running Windows NT Workstation 3.51
	  otherwise, ignore.)
	
	3. Add the local user to the local administrator group.
	
	4. Log off and log on to the workstation as the local user.
	
	5. Using Windows NT Setup, delete the domain users profile.
	
	6. Using Profile Editor, click Save as user default from the File menu. Ensure
	  that the local users account is listed in the Permitted to Use Profile dialog
	  box.
	
	7. Log off and log on the computer as the domain user.
	
	The domain user's profile should now be the same as the local user profile. At
	this point, you can remove the local user from the local administrators group
	and remove the Windows NT Server tools from the workstation.
	
	Additional query words: poledit roaming
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNT351search kbWinNTW351search kbWinNTW351 kbWinNTSsearch kbWinNTS351 kbWinNTS351search
	Version           : WinNT:3.51
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
