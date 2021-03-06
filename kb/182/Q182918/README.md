---
layout: page
title: "Q182918: Account Lockout Event Also Stored in Security Event Log on DC"
permalink: /kb/182/Q182918/
---

## Q182918: Account Lockout Event Also Stored in Security Event Log on DC

{% raw %}

	Article: Q182918
	Product(s): Microsoft Windows NT
	Version(s): winnt:4.0
	Operating System(s): 
	Keyword(s): kbFEA kbWinNT400sp4fix kbWinNT400sp4fea
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server version 4.0 
	- Microsoft Windows NT Server, Enterprise Edition version 4.0 
	- Microsoft BackOffice Small Business Server version 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it if
	a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	When users enter a series of incorrect passwords in an attempt to log on to
	Windows NT using domain accounts and the Bad Logon Attempts limit for the
	account is reached, the account is locked out at the domain controller.
	
	Windows NT generates an account lockout event (Event ID: 539) on the workstation
	where the failed logon attempts occurred if the audit policy on that workstation
	enables auditing of failed logon/logoff events. However, no event is logged at
	the domain controller. Administrators must search the event logs of all client
	systems to locate the computer where the bad password attempts originated.
	
	RESOLUTION
	==========
	
	Before You Apply The Hotfix
	---------------------------
	
	Because this hotfix makes a modification to the on-disk storage of the LSA data
	information, Microsoft does not recommend that it be uninstalled. Perform the
	following steps to ease the transition back to a pre-LSA2-fix configuration in
	case you experience problems with the hotfix:
	
	1. Perform a Full System Backup.
	
	2. Run Rdisk /s. Using the /s command-line switch with Rdisk.exe causes the
	  Sam._ and Security._ databases to be copied to the %Systemroot%\Repair
	  folder.
	
	3. Create a temporary folder under the %Systemroot% folder called Lsabackout.
	
	4. Copy the following files from the %Systemroot\System32 folder to the
	  %Systemroot%\Lsabackout folder as they are updated by LSA2-fix:
	
	  Eventlog.dll
	  Lsasrv.dll
	  Msaudite.dll
	  Msv1_0.dll
	  Netcfg.dll
	  Samlib.dll
	  Samsrv.dll
	  Services.exe
	  Srvmgr.exe
	  Xactsrv.dll
	
	5. Create an updated Emergency Repair Disk (ERD) which updates the on-disk SAM
	  and Registry information in the %Systemroot%\System32\Config folder.
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	NOTE: This hotfix supersedes the fix referred to in the following articles in the
	Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q154087
	  TITLE : Access Violation in LSASS.EXE Due to Incorrect Buffer Size
	
	  ARTICLE-ID: Q174205
	  TITLE : LSASS May Use a Large Amount of Memory on a Domain Controller
	
	  ARTICLE-ID: Q129457
	  TITLE : Anonymous Connections May Be Able to Obtain the Password Policy
	
	This hotfix has been posted as Lsa2fixi.exe (x86) and Lsa2fixa.exe (Alpha). For
	your convenience, the English version of this post-SP3 hotfix has been posted to
	the following Internet location. However, Microsoft recommends that you install
	Windows NT 4.0 Service Pack 4 to correct this problem.
	
	NOTE: An updated version of this hotfix was posted on July 20, 1998 and provides
	an additional security level to systems running Windows NT 4.0 Service Pack 3.
	
	ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/NT40/hotfixes-postSP3/lsa2-fix/
	
	If you run Systems Management Server on systems where this hotfix is applied, the
	SNMP Event Log Extension Agent (Snmpelea) generates the following Event ID 3007
	error:
	
	  Error opening event log file Security.
	  Log will not be processed.
	  Return code from OpenEventLog is 1314.
	
	The SNMP Event Log Extension Agent requires an update to manage the security
	event log. To resolve the SNMP Event Log Extension Agent problem, please see the
	following article in the Microsoft Knowledge Base:
	
	  ARTICLE-ID: Q183770
	  TITLE : SMS: Snmpelea Unable to Open Security Event Log
	
	
	MORE INFORMATION
	================
	
	Microsoft provides a hotfix to change this behavior. After the hotfix is applied
	on all domain controllers, bad logon attempts that cause a user's account to be
	locked out generate an audit event in the security event log on the primary
	domain controller and on the domain controller that handles the logon request. A
	new security event (Event ID: 644 - User Account Locked Out) is generated at the
	primary domain controller to indicate the user account was automatically locked
	out because of bad logon attempts. The security event is generated if the audit
	policy for the domain enables Success for the User and Group Management audit
	category.
	
	If the client workstation is a computer running Windows NT or Windows 95, the
	account lockout event includes the client workstation name to identify the
	computer where the bad passwords are entered.
	
	If you experience problems with this hotfix, perform the following steps to
	restore the system to its original configuration before applying the hotfix:
	
	1. Perform a full system backup including the registry. This backup set should
	  only be necessary if the following steps fail.
	
	2. Rename the following files the %Systemroot%\System32 folder that were
	  replaced by the hotfix:
	
	  Eventlog.dll
	  Lsasrv.dll
	  Msaudite.dll
	  Msv1_0.dll
	  Netcfg.dll
	  Samlib.dll
	  Samsrv.dll
	  Services.exe
	  Srvmgr.exe
	  Xactsrv.dll
	
	3. Copy the original versions of these system files from the
	  \%Systemroot%\Lsabackout folder to the %Systemroot%\System32 folder.
	
	4. Restart the computer using the installation disks and select the option to
	  repair the system.
	
	5. Deselect all options except Inspect Registry Files and then continue.
	
	6. Press the ESC key to indicate you wish to use the on-disk repair information.
	
	7. Press ENTER to repair.
	
	8. Click only Security (security policy) and SAM (user accounts database).
	
	  WARNING: Using Registry Editor incorrectly can cause serious problems that may
	  require you to reinstall your operating system. Microsoft cannot guarantee
	  that problems resulting from the incorrect use of Registry Editor can be
	  solved. Use Registry Editor at your own risk.
	
	  For information about how to edit the registry, view the "Changing Keys And
	  Values" Help topic in Registry Editor (Regedit.exe) or the "Add and Delete
	  Information in the Registry" and "Edit Registry Data" Help topics in
	  Regedt32.exe. Note that you should back up the registry before you edit it.
	
	9. Start Registry Editor (Regedt32.exe) and delete the Q184017 key from:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT
	  \CurrentVersion\Hotfix
	
	  NOTE: The above registry key is one path; it has been wrapped for readability.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	Additional query words: 4.00 bad password lockout after
	
	======================================================================
	Keywords          : kbFEA kbWinNT400sp4fix kbWinNT400sp4fea 
	Technology        : kbWinNTsearch kbWinNT400search kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400 kbWinNTS400search kbWinNTS400 kbNTTermServ400 kbNTTermServSearch kbAudDeveloper kbSBServSearch kbSBServ400
	Version           : winnt:4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
