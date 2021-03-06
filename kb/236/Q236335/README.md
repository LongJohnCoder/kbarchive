---
layout: page
title: "Q236335: XFOR: To Field Empty if User Sends Mail w/AT Command from OV/VM"
permalink: /kb/236/Q236335/
---

## Q236335: XFOR: To Field Empty if User Sends Mail w/AT Command from OV/VM

{% raw %}

	Article: Q236335
	Product(s): Microsoft Exchange
	Version(s): winnt:5.5
	Operating System(s): 
	Keyword(s): exc55 EXC55SP3Fix
	Last Modified: 30-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Exchange Server, version 5.5 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When an OV/VM user sends a message with the AT or CT command in the message body
	to an Exchange Server recipient by means of the Microsoft PROFS Connector, the
	message has an empty To field if the AT command is used and an empty Cc field if
	the CT command is used.
	
	CAUSE
	=====
	
	The display name used with the AT and CT commands does not have a valid PROFS
	address; this causes the Microsoft PROFS Connector to discard the display name.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Exchange Server
	version 5.5. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q191014 XGEN: How to Obtain the Latest Exchange Server 5.5 Service Pack
	
	The English version of this fix should have the following file attributes or
	later:
	
	Component: Microsoft PROFS Connector
	
	+---------------------------+
	| File name    | Version    | 
	+---------------------------+
	| Lsvmhc.dll   | 5.5.2630.0 | 
	+---------------------------+
	| Lsdiamex.exe | 5.5.2630.0 | 
	+---------------------------+
	| Lsvmdia.exe  | 5.5.2630.0 | 
	+---------------------------+
	| Lsdiavm.exe  | 5.5.2630.0 | 
	+---------------------------+
	| Xfmload.exe  | 5.5.2630.0 | 
	+---------------------------+
	
	And add the following entry in the [LME-PROFS] section of the Exchconn.ini file:
	
	PROFS_DummyAddr = Node(Addr)
	
	The Node and Addr need to comply the PROFS address format, that is no more than
	eight characters.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Microsoft Exchange Server
	version 5.5. This problem was first corrected in Exchange Server 5.5 Service
	Pack 3.
	
	Additional query words:
	
	======================================================================
	Keywords          : exc55 EXC55SP3Fix 
	Technology        : kbExchangeSearch kbExchange550 kbZNotKeyword2
	Version           : winnt:5.5
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
