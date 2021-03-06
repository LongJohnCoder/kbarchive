---
layout: page
title: "Q156271: SMS: Installation Scripts for &quot;Run Command on Workstation&quot;"
permalink: /kb/156/Q156271/
---

## Q156271: SMS: Installation Scripts for &quot;Run Command on Workstation&quot;

{% raw %}

	Article: Q156271
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.0,1.1,1.2
	Operating System(s): 
	Keyword(s): kb3rdparty kbnetwork kbPCM smsappscripts smspcm kbSMSAppScripts
	Last Modified: 31-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 1.0, 1.1, 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	An installation script is required for "Run Command on Workstation" packages, if
	the executable file specified in the Package Command Line terminates after
	calling a second executable file that relies on accessing the package share
	location to continue.
	
	Many applications run a setup program, and the original executable (such as
	Setup.exe) does not keep running throughout the duration of setup. When creating
	a "Run Command on Workstation" package, the executable file to run is specified.
	When the workstation receives that package, and the Package Command Manager
	(PCM) goes to run it, PCM does a NET USE to the package share location. As soon
	as the original executable file is finished running, PCM deletes the share. If
	the executable file spawned another executable file before it closed, the second
	application will fail if it relies on the source share. The error messages that
	may result from this problem vary from application to application. PCM will
	report in the Pcmwin.log file that the package ran successfully.
	
	There may or may not be error messages when the installation fails, depending on
	the setup application. The following are examples of common error messages or
	problems that may be encountered:
	
	  Insert Disk 16 in Drive N:
	
	  Unable to read from Drive N:
	
	  Disk Error Drive/on Device N:
	
	  Error reading Drive N
	
	  Error opening file XXX
	
	  Error in script line 123 - cannot open media script file
	
	Buttons or windows may be blank or not drawn correctly
	
	The system stops responding
	
	WORKAROUND
	==========
	
	To work around this problem, do one of the following:
	
	- If the application to be installed is an MS-DOS-based application, or a
	  Windows-based application on a client computer running Windows NT, it may be
	  possible to create a batch file containing the command for the setup
	  executable file, and then use the batch file as the command line when
	  creating the package.
	
	- If the application is a 16-bit application for a computer running Windows
	  3.1, Windows NT, or Windows 95, use Execute.exe to run a two- phase setup
	  program under the PCM program. Execute.exe is provided with the Systems
	  Management Server 1.2 Resource Kit, and requires a basic understanding of
	  Visual C++.
	
	- Copy the source files to the local hard drive, before launching setup.
	
	MORE INFORMATION
	================
	
	MSTest is not the only option for writing an installation script for "Run
	Command on Workstation" packages. There are other options, such as using
	InstallShield or WINInstall, Visual Basic, C, or even Visual Test (for client
	computers running Windows NT only).
	
	NOTE: If the entire setup program runs from a single executable file (many
	programs do), it is not necessary to write an installation script at all.
	
	The following are some third-party applications that can be used to write an
	installation script:
	
	- MSTest by Microsoft Corporation
	
	- Visual Test by Microsoft Corporation
	
	- InstallShield by Installshield Corporation
	
	- WINInstall by Seagate (formerly OnDemand Software)
	
	- WinBatch by Wilson WindowWare
	
	- LAN Script by ABC Systems
	
	- Wise Solutions, Inc.
	
	The products included here are manufactured by vendors independent of Microsoft;
	we make no warranty, implied or otherwise, regarding these products' performance
	or reliability.
	
	For more information on this subject, see the following articles in the Microsoft
	Knowledge Base:
	
	  Q130373 Obtaining Package ID From Within an Microsoft Test Script
	
	  Q151735 Visual Test 4.0 Not Supported with Windows 95 PCM
	
	  Q153227 PCM Requires Reboot After Executing Package
	
	  Q128612 SMS: Visual Basic Application Setup Fails When Executed by PCM
	
	Additional query words: prodsms WIN Install Shield
	
	======================================================================
	Keywords          : kb3rdparty kbnetwork kbPCM smsappscripts smspcm kbSMSAppScripts 
	Technology        : kbSMSSearch kbSMS100 kbSMS110 kbSMS120
	Version           : winnt:1.0,1.1,1.2
	
	=============================================================================
	

{% endraw %}
