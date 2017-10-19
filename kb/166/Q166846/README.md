---
layout: page
title: "Q166846: Cannot Reconnect to TN3270 Server with Close Listen Sockets"
permalink: /kb/166/Q166846/
---

## Q166846: Cannot Reconnect to TN3270 Server with Close Listen Sockets

	Article: Q166846
	Product(s): Microsoft Windows NT
	Version(s): 2.11 SP1,2.11 SP2,3.0,3.51,4.0
	Operating System(s): 
	Keyword(s): kbWinNT400sp4fix
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0 
	- Microsoft Windows NT Server version 4.0, Terminal Server Edition 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	When you configure the Microsoft SNA Server 2.11 or SNA Server 3.0 TN3270 Server
	to use the Close Listen Socket option, TN3270 clients are unable to reconnect to
	the TN3270 server even though LUA sessions are available.
	
	When the Close Listen Socket option is enabled, the TN3270 service performs a
	CloseSocket() call when all SNA sessions are in use. The TN3270 service
	indicates this by logging the following Windows NT event:
	
	  Event ID: 207
	  Source: TN3270 Server
	  Description:
	  The TN3270E Server has closed the socket which listens for clients
	
	While existing TN3270 client sessions continue to work normally, new TN3270
	client connection requests are rejected immediately with a TCP/IP Reset. This
	allows the TN3270 client emulator to be notified of a connection failure so it
	can try a different TN3270 service for a session.
	
	When a TN3270 client disconnects causing an SNA session to become available, the
	TN3270 service reopens the listen socket again and logs the following event:
	
	  Event ID: 206
	  Source: TN3270 Server
	  Description:
	  The TN3270E Server has opened a socket to listen for clients
	
	However, TN3270 clients are still unable to reconnect until the TN3270 server is
	stopped and restarted or if all users disconnect from the TN3270 server.
	
	CAUSE
	=====
	
	When the TN3270 server calls the CloseSocket() function, the Windows NT TCP/IP
	address object connect handler address is set to NULL, which causes TCP/IP to
	send a TCP/IP Reset when clients attempt to connect to the TN3270 port number.
	
	When an SNA session becomes available, the TN3270 Server reopens the listen
	socket by calling the socket() function. This causes the Windows NT TCP/IP
	driver to create a duplicate address object with a valid connect handler
	address. However, connection requests are validated against the old TCP/IP
	address object, which still has a NULL connect handler.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Windows NT 4.0 or
	Windows NT Server 4.0, Terminal Server Edition. For additional information,
	please see the following article in the Microsoft Knowledge Base:
	
	  Q152734 How to Obtain the Latest Windows NT 4.0 Service Pack
	
	
	A hotfix for Windows NT 3.51 is available to correct this problem.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Windows NT 4.0 and Windows NT
	Server 4.0, Terminal Server Edition. This problem was first corrected in Windows
	NT 4.0 Service Pack 4.0 and Windows NT Server 4.0, Terminal Server Edition
	Service Pack 4.
	
	
	Microsoft has confirmed this to be a problem in Windows NT version 3.51. A
	supported fix is now available, but has not been fully regression-tested and
	should be applied only to systems experiencing this specific problem. Unless you
	are severely impacted by this specific problem, Microsoft recommends that you
	wait for the next Service Pack that contains this fix. Contact Microsoft
	Technical Support for more information.
	
	
	Additional query words: closelistensocket prodsna snatn3270
	
	======================================================================
	Keywords          : kbWinNT400sp4fix 
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT400search kbWinNTSsearch kbWinNTS400search kbWinNTS400 kbWinNTS351 kbNTTermServ400 kbNTTermServSearch kbWinNTS351search
	Version           : :2.11 SP1,2.11 SP2,3.0,3.51,4.0
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	