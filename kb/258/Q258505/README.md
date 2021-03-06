---
layout: page
title: "Q258505: XADM: Information Store Receives Access Violation W. UTF-8 and 7"
permalink: /kb/258/Q258505/
---

## Q258505: XADM: Information Store Receives Access Violation W. UTF-8 and 7

{% raw %}

	Article: Q258505
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55 kbExchange550preSP4fix kbExchange550sp4Fix kbgraphxlinkcritical
	Last Modified: 01-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	If RichWin, which changes the internal language of a workstation to UTF-8 or
	UTF-7, is installed on your computer and you use Microsoft Outlook to log on to
	an Exchange Server computer, the Exchange Server information store may stop
	unexpectedly with a stack dump that is similar to the following:
	
	  FramePtr RetAddr Param1 Param2 Param3 Function Name
	  14e5f544 0057218a 011c3d88 ffffffff 14e5f590 STORE!EcMakeSortKey+0x1a3
	  14e5f56c 0057263e 00000000 14e5f590 14e5f598 STORE!EcMakeSortKey+0x83
	  14e5f598 005728f5 003784b0 00000409 14e5f65c
	  STORE!TWIR__EcStreamSubstringUnicode+0x45
	  14e5f5bc 004f8055 00378ffb 00000409 14e5f65c
	  STORE!TWIR__EcRestrictContent+0x46
	  14e5f5dc 004f7fd8 15d9b5b8 00000409 14e5f65c 0x004f8055
	  14e5f5fc 004f7f86 00000003 00000409 14e5f65c STORE!TWIR__EcRestrictHier+0x4e
	  14e5f61c 004bbb90 16d8d080 ffffffff 00000000 STORE!TWIR__EcFindRow+0xc6
	  14e5f740 0040567a 00000000 16d8d080 00000000 STORE!VMSG__EcSlowFindRow+0x23a
	  14e5f768 004a0421 00000000 16d8d080 00000000 0x0040567a
	  14e5f794 004f8b6f 00000000 16d8d080 00000000 STORE!EcFindRowOp+0xdc
	  14e5fa18 0040f397 00000003 0000084a 23648120 STORE!EcFindRow+0x12d
	  15ed4268 15ed4268 00030001 00000f67 00000000 STORE!@EcRpc@16+0x807
	
	CAUSE
	=====
	
	This issue can occur because any query that a client submits needs to be
	converted first to Unicode by the information store using the software
	development kit (SDK) function MultiByteToWideChar(). The flag of the conversion
	is always set as MB_PRECOMPOSED. In this case, the properties in the query are
	converted from UTF-8 or UTF-7 to Unicode, which does not allow the
	MB_PRECOMPOSED flag to be used. Then the conversion stops with returned value as
	0. The later reference to the string causes an access violation.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server 5.5.
	For additional information, click the following article number to view the
	article in the Microsoft Knowledge Base:
	
	  Q191914 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  x86: DownloadDownload Q248838engi.exe now
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=25443)
	  Alpha: DownloadDownload Q248838enga.exe now
	  (http://www.microsoft.com/downloads/release.asp?ReleaseID=25444)
	
	For additional information about how to download Microsoft Support files, click
	the following article number to view the article in the Microsoft Knowledge
	Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft scanned this file for viruses. Microsoft used the most current
	virus-detection software that was available on the date that the file was
	posted. The file is stored on secure servers that prevent any unauthorized
	changes to the file.
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 4.
	
	MORE INFORMATION
	================
	
	For additional information about conversion between UTF-8 or UTF-7 and UNICODE,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q175392 INFO: UTF8 Support
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 kbExchange550preSP4fix kbExchange550sp4Fix kbgraphxlinkcritical 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
