---
layout: page
title: "Q169686: XADM: IMC Shuts Down, Error Connecting to IS"
permalink: /kb/169/Q169686/
---

## Q169686: XADM: IMC Shuts Down, Error Connecting to IS

{% raw %}

	Article: Q169686
	Product(s): Microsoft Exchange
	Version(s): WinNT:4.0,5,0
	Operating System(s): 
	Keyword(s): kbusage
	Last Modified: 16-APR-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, versions 4.0, 5.0 
	-------------------------------------------------------------------------------
	
	
	IMPORTANT: This article contains information about editing the registry.
	Before you edit the registry, make sure you understand how to restore it
	if a problem occurs. For information on how to do this, view the "Restoring
	the Registry" online Help topic in Regedit.exe or the "Restoring a Registry
	Key" online Help topic in Regedt32.exe.
	
	SYMPTOMS
	========
	
	The Internet Mail Service (or Internet Mail Connector, in version 4.0) may shut
	down and the following events may appear in the Event Viewer Application Log:
	
	  4116
	  An error was returned from the messaging software the Internet Mail
	  Service uses to process messages on the Microsoft Exchange Server.  It
	  is possible that the piece of mail being processed at the time will not
	  be delivered. The message that was being processed has been moved to the
	  "BAD" folder.  Use the appropriate utilities found in the SUPPORT
	  directory of your Exchange CD to view and manipulate these messages.
	
	  3039
	  The error 0x80040115 was encountered while trying to communicate with
	  the message store. An attempt to refresh the connection will be made.
	  If not successful, the service will be shut down.
	
	  4117
	  An error was returned from the messaging software the Internet Mail
	  Service uses to process messages on the Microsoft Exchange Server. As a
	  result, the message in spool file 3XDW6BQJ failed to be delivered. The
	  message has been moved to the Imcdata\In\Archive directory.
	
	  4094
	  The error 0x8004011d occurred while trying to refresh network
	  connections to the Information Store. The Internet Mail Service is being
	  shut down.
	
	  4102
	  A serious error has occurred while trying to send mail into the Exchange
	  Information Store. The Internet Mail Service is being shut down.
	
	This series of events repeats itself when you restart the Internet Mail Service
	(IMS) or Internet Mail Connector (IMC).
	
	CAUSE
	=====
	
	The number of threads available to the IMC or IMS from the Information Store
	(IS) may be too low. Check the following registry setting:
	
	  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSExchangeIS
	  \ParametersSystem\Max Threads(Private+Public).
	
	The Max Threads(Private+Public) value defaults to 0x20 when Microsoft Exchange
	Server is installed. However, if you run Performance Optimizer and leave the
	default values, select all Server Type options, or choose a low number of users,
	this registry parameter is decreased to 0x5. This in turn prevents the IMC or
	IMS from connecting to the IS to deliver new mail or retrieve outbound mail.
	
	This registry setting is not visible unless Performance Optimizer has been run or
	you add it manually.
	
	WORKAROUND
	==========
	
	WARNING: Using Registry Editor incorrectly can cause serious problems that may
	require you to reinstall Windows. Microsoft cannot guarantee that problems
	resulting from the incorrect use of Registry Editor can be solved. Use Registry
	Editor at your own risk.
	
	For information about how to edit the registry, view the "Changing Keys And
	Values" online Help topic in Registry Editor (Regedit.exe) or the "Add and
	Delete Information in the Registry" and "Edit Registry Data" online Help topics
	in Regedt32.exe. Note that you should back up the registry before you edit it.
	
	To work around this problem:
	
	- Change the registry setting so that you increase the number of threads
	  available. For instance, changing it to 0x14 will provide a maximum of 20
	  threads.
	
	MORE INFORMATION
	================
	
	Performance Optimizer records all the changes it makes in a log file in the
	Windows NT \system32 directory, called perfopt.log. Every time you run the
	Optimizer, this log file is appended with the latest changes. You can review
	this log file for changes to the Max Threads(Private+Public) registry setting.
	
	Additional query words: exfaq
	
	======================================================================
	Keywords          : kbusage 
	Technology        : kbExchangeSearch kbExchange500 kbExchange400 kbZNotKeyword2
	Version           : WinNT:4.0,5,0
	
	=============================================================================
	

{% endraw %}
