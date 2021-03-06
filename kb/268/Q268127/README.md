---
layout: page
title: "Q268127: TN3270 LUs Must Be Pooled Across Multiple Nodes or Connections"
permalink: /kb/268/Q268127/
---

## Q268127: TN3270 LUs Must Be Pooled Across Multiple Nodes or Connections

{% raw %}

	Article: Q268127
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:3.0 (all SP),4.0,4.0 SP1,4.0 SP2,4.0 SP3; :
	Operating System(s): 
	Keyword(s): kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp
	Last Modified: 12-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 3.0 SP1, 3.0 SP2, 3.0 SP3, 3.0 SP4, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3 
	- Microsoft Host Integration Server 2000 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	3270 clients that are requesting a session through a TN3270 server may fail with
	a blank screen or error message when SNA Server or Host Integration Server 2000
	is configured by using multiple connections or multiple nodes.
	
	See the "More Information" section of this article for configuration environments
	in which these problems may occur.
	
	CAUSE
	=====
	
	When a session request comes in, the TN3270 server searches for the first LU
	name that matches the request (for example, 3278-2-E). When the TN3270 server
	finds this, it specifies the LUA name in RUI_INIT, which causes an OPEN SSCP
	request to be sent to the SNA Server service (node). At this point, the node
	tries to use that resource because it is informed to use that specific LUA LU.
	The TN3270 server does not validate whether the LUA LU is available or inactive.
	It is not the application's (TN3270 server in this case) responsibility to do
	this. If the requested LUA LU is inactive, the problems described in the
	"Symptoms" section occur.
	
	When you use LUA Pools, the problem does not occur because the RUI_INIT request
	contains the Pool name. In this case, the node is responsible for finding an
	available LUA LU in the pool for use.
	
	RESOLUTION
	==========
	
	To resolve this problem, do the following:
	
	1. Delete the individual LUA LUs from the TN3270 server.
	
	2. Assign the LUA LUs from each node or connection to a LUA Pool.
	
	3. Assign the LUA Pool to the TN3270 server.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	In both of the following examples, LUA Pools are not being used. Only individual
	LUA LUs are assigned to the TN3270 server.
	
	Example 1: Using multi-node support:
	
	SNA Server or Host Integration Server 2000 is configured by using multi-node
	support (multiple SNA services on one server), and the last node (for example,
	SNA Server 02) that was added or configured is stopped or paused. When a session
	is requested, a blank screen is displayed, even though sessions are available on
	the other (original) SNA Server or Host Integration Server 2000 node.
	
	In addition to the blank screen, the following error message is displayed in the
	lower left corner of the screen if you are using the 3270 applet that is
	included in SNA Server or Host Integration Server 2000:
	
	  [TN3270-36]: Error - An error occurred during device type/name processing.
	
	NOTE: Other third-party emulators may report a different message.
	
	If you review the Application log in the Event Viewer during this time, the
	following two events are posted:
	
	  Event 1955 - Source: SNA RUI Application
	  RUI_INIT failed for LU <LU_NAME>, primary_rc = 4f0, secondary_rc = 0
	
	  Event 602 - Source: TN3270 Server
	  TN3270(E) session terminated normally with client at <IP_Address>
	  <port_number> using LU <LU_NAME>
	
	Example 2: Multiple Connections across one or more servers:
	
	SNA Server or Host Integration Server 2000 is configured by using multiple
	connections on one SNA Server, or multiple connections on other SNA Servers in
	the same SNA Server or Host Integration Server 2000 subdomain. If the last
	connection that was added or configured is stopped, the following error message
	is displayed if you are using the 3270 applet that is included in SNA Server or
	Host Integration Server 2000, even though other sessions are available on other
	connections:
	
	  TN3270E Service Message 523
	  The data link is activating for LU <LU_NAME>
	  You may continue to wait, or terminate your session.
	
	NOTE: Other third-party emulators may report a different message.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbsna300sp1 kbsna300sp2 kbsna300sp3 kbsna300sp4 sna4 kbsna400sp1 kbsna400sp2 kbsna400sp3 
	Technology        : kbAudDeveloper kbSNAServSearch kbHostIntegServ2000 kbSNAServ400 kbSNAServ300SP3 kbSNAServ300SP1 kbSNAServ400SP1 kbSNAServ400SP2 kbSNAServ400SP3 kbSNAServ300SP2 kbSNAServ300SP4
	Version           : WINDOWS:3.0 (all SP),4.0,4.0 SP1,4.0 SP2,4.0 SP3; :
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
