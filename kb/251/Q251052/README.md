---
layout: page
title: "Q251052: XADM: Move Server Wizard Stops After Information Store Fix"
permalink: /kb/251/Q251052/
---

## Q251052: XADM: Move Server Wizard Stops After Information Store Fix

{% raw %}

	Article: Q251052
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5 SP3
	Operating System(s): 
	Keyword(s): exc55sp3 kbgraphxlinkcritical
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	If you run the Exchange Server Move Server Wizard on an Exchange Server version
	5.5 Service Pack 3 computer to which a Store.exe fix version 5.5.2651.32 or
	later has been applied, the following error message may be displayed when the
	wizard tries to upgrade the private information store database:
	
	  Microsoft Exchange Move Server Wizard
	  An unexpected error has occurred while updating the Microsoft Exchange
	  Private Information Store
	  ID no: c1070451
	  <OK>
	
	CAUSE
	=====
	
	This error message can occur if you upgrade the database by using a Store.exe
	program version 5.5.2651.32 or later. Earlier versions of the Move Server Wizard
	cannot process the extra data in the information store.
	
	If the Store.exe program is version 5.5.2651.32 or later, and the Mvstore.dll
	file is not version 5.5.2651.73 or later, the Move Server Wizard stops
	responding.
	
	RESOLUTION
	==========
	
	If the error message in the "Symptoms" section of this article is displayed, you
	must install the latest information store fix after you restore the system from
	a tape backup and before you run the Move Server Wizard again.
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Exchange Server version 5.5 service pack that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information about support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	NOTE: In special cases, charges that are normally incurred for support calls may
	be canceled, if a Microsoft Support Professional determines that a specific
	update will resolve your problem. Normal support costs will apply to additional
	support questions and issues that do not qualify for the specific update in
	question.
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Move Server Wizard
	
	+---------------------------+
	| File name   | Version     | 
	+---------------------------+
	| Mvstore.dll | 5.5.2651.73 | 
	+---------------------------+
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5 Service Pack 3.
	
	MORE INFORMATION
	================
	
	The fix described in this article will only update the Mvstore.dll if Move
	Server Wizard has been installed.
	
	The new Store.exe fixes are available for download from the Microsoft Download
	Center.
	
	NOTE: One of the files is for the x86 platform and the other is for the Alpha
	platform; you only need both if you have both platforms.
	
	The following files are available for download from the Microsoft Download
	Center:
	
	For x86:
	
	  DownloadDownload Q248838engi.exe now
	
	For Alpha:
	
	  DownloadDownload Q248838enga.exe now
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. After it is posted, the file is housed on
	secure servers that prevent any unauthorized changes to the file.
	
	NOTE: When you start this version of the information store, the information store
	databases are automatically upgraded to a new format. After you upgrade the
	databases, you can restore an earlier version of the Store.exe file on the
	server, but only if it is version 5.5.2651.32 or later. If you restore a
	Store.exe file earlier than version 5.5.2651.32 after you upgrade the database,
	you are no longer able to start the information store. For additional
	information, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q244976 XADM: Event ID 1197 and 1005 When Starting the Information Store
	
	Additional query words: Q248838
	
	======================================================================
	Keywords          : exc55sp3 kbgraphxlinkcritical 
	Technology        : kbExchangeSearch kbZNotKeyword2 kbExchange550SP3
	Version           : winnt:5.5 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
