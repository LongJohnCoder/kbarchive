---
layout: page
title: "Q134288: Cannot Connect to Internet and MSN with Static DNS"
permalink: /kb/134/Q134288/
---

## Q134288: Cannot Connect to Internet and MSN with Static DNS

{% raw %}

	Article: Q134288
	Product(s): The Microsoft Network
	Version(s): WINDOWS:1.2,1.3,2.0,2.5
	Operating System(s): 
	Keyword(s): kbenv kberrmsg kbmsn
	Last Modified: 09-OCT-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Network versions 1.2, 1.3, 2.0, 2.5 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to connect to Internet and The Microsoft Network, you may receive
	the following error message:
	
	  Cannot locate the MSN data center.
	
	
	CAUSE
	=====
	
	If you have a static Domain Name Server (DNS) address, you cannot connect to
	Internet and The Microsoft Network. This is most likely to occur if you have a
	network card or already have Dial-Up Networking installed for access to a
	corporate network or a different Internet service provider.
	
	To check the DNS address, follow these steps:
	
	1. Click Start, point to Settings, and then click Control Panel.
	
	2. Double-click Network.
	
	3. Click either the TCP/IP protocol (if you do not have a network card) or the
	  TCP/IP Dial-Up Network Adapter protocol (if you have a network card).
	
	4. Click Properties.
	
	5. On the DNS Configuration tab, click Disable DNS.
	
	RESOLUTION
	==========
	
	To connect to Internet and The Microsoft Network, you must have the Disable DNS
	option selected and no DNS addresses listed.
	
	However, the DNS configuration affects all network cards and modems. If you have
	a network card and are on a local area network (LAN) that uses TCP/IP with
	static DNS addresses (that is, without DHCP), removing the static DNS address
	listed on the DNS Configuration tab will cause you to lose all TCP/IP access to
	your LAN.
	
	If you run a TCP/IP LAN with static DNS and want to connect to Internet and The
	Microsoft Network, you have three options:
	
	- Run a different protocol (such as IPX/SPX or NetBEUI) on your LAN.
	
	- Run DHCP on the LAN and have it assign DNS addresses dynamically.
	
	- Change the DNS configuration manually every time you run Internet and The
	  Microsoft Network. That is, before connecting, delete the static DNS address
	  and restart your computer. Then after disconnecting, add the static address
	  back and restart so you can see your LAN again.
	
	Additional query words: msn multihoming multi-homing
	
	======================================================================
	Keywords          : kbenv kberrmsg kbmsn 
	Technology        : kbMSNSearch kbMSN200 kbMSN130 kbMSN250 kbMSN120
	Version           : WINDOWS:1.2,1.3,2.0,2.5
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
