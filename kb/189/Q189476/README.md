---
layout: page
title: "Q189476: SNA Server Error 0352 - Unable To Open Configuration File,rc=618"
permalink: /kb/189/Q189476/
---

## Q189476: SNA Server Error 0352 - Unable To Open Configuration File,rc=618

{% raw %}

	Article: Q189476
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0,3.0SP1,3.0SP2,3.0SP3,4.0,4.0SP1
	Operating System(s): 
	Keyword(s): kbfixlist
	Last Modified: 10-JUL-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0, 3.0SP1, 3.0SP2, 3.0SP3, 4.0, 4.0SP1 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you boot or start the SNA Server computer, you may encounter the following
	error:
	
	  SNA Server Error #0352, Unable to open the configuration file, rc=618.
	
	CAUSE
	=====
	
	This is caused when the SnaNetMn Service is set to automatic startup in Control
	Panel Services. SNA Server automatically starts this service if NetView
	connectivity is configured on an SNA Server connection.
	
	RESOLUTION
	==========
	
	SNA Server 3.0
	--------------
	
	To resolve this problem, obtain the latest service pack for SNA Server version
	3.0. For additional information, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q184307 How to Obtain the Latest SNA Server Version 3.0 Service Pack
	
	
	
	SNA Server 4.0
	--------------
	
	This problem was corrected in the latest SNA Server version 4.0 U.S. Service
	Pack. For information on obtaining this Service Pack, query on the following
	word in the Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	WORKAROUND
	==========
	
	Set this service for manual startup in Control Panel Services.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 3.0, 3.0
	SP1, 3.0 SP2, 3.0 SP3, 4.0, and 4.0 SP1. This problem was first corrected in SNA
	Server 3.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	For more information on what SNA Server services can be configured for automatic
	startup, please refer to the following Knowledge Base article:
	
	  Q110390 Automatically Starting SNA Server Through Control Panel
	
	Additional query words:
	
	======================================================================
	Keywords          :  kbfixlist
	Technology        : kbAudDeveloper kbSNAServSearch kbSNAServ300 kbSNAServ400
	Version           : WINDOWS:3.0,3.0SP1,3.0SP2,3.0SP3,4.0,4.0SP1
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
