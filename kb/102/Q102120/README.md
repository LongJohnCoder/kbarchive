---
layout: page
title: "Q102120: Mac Srv: Server-to-Server Messages"
permalink: /kb/102/Q102120/
---

## Q102120: Mac Srv: Server-to-Server Messages

{% raw %}

	Article: Q102120
	Product(s): Microsoft Mail For Appletalk Networks
	Version(s): WINDOWS:3.0,3.1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 10-NOV-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Mail for AppleTalk Networks, versions 3.0, 3.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	In version 3.0 and 3.1 of Microsoft Mail for AppleTalk Networks, mail servers
	communicate with each other by sending messages. These messages contain
	administrative data, such as user lists, group lists, routing information, etc.
	These messages are referred to as Server-to-Server messages.
	
	In a multiple-server environment, servers will automatically scan for other
	Microsoft Mail servers and exchange this data with those servers.
	Server-to-Server messages or normally "hidden" from the normal view of Network
	Managers.
	
	Network Managers can utilize the Mail Network Administration program to produce a
	Global-Server Report that will show all known servers on the network. Any
	messages awaiting deliver will be displayed after the server information.
	
	Server-to-Server messages may be included in this report by holding the OPTION
	key while selecting Server Report from the Global menu. If any server-to-server
	classified messages are awaiting delivery, they will be displayed after each
	server listed.
	
	MORE INFORMATION
	================
	
	The following is a description of the different messages that can be displayed.
	
	NOTE: When the term GX is used below, it means group expansion or Schedule+
	schedule/calendar data.
	
	Local User List
	---------------
	
	This message contains the entire local user list and local group list for a
	server. The user list can be from the sending server, but can also be from
	another server in the same site, if this server is the bridgehead. If the
	bridgehead is a Mail 3.1 server, the local user list should indicate which
	server the user list is coming from.
	
	Create Request
	--------------
	
	This message contains an entire GX. This GX is either new or meant to replace an
	existing one.
	
	Modify Request
	--------------
	
	This message contains changes to an existing GX. This message may also be a local
	user list modification if the sending and receiving servers are Mail 3.1
	servers.
	
	Remove Request
	--------------
	
	This message identifies a GX to be removed.
	
	Enslave Request
	---------------
	
	This message should be queued for the master gateway and indicates an access
	gateway has just been INSTALLED with the Gateway Installer program. This message
	is telling the master gateway to send gateway recipient list/updates.
	
	Deslave Request
	---------------
	
	This message should be queued for the master gateway and indicates an access
	gateway has just been REMOVED with the Gateway Installer program. This message
	is telling the master gateway to stop sending gateway recipient list/updates.
	
	MasterGone Request
	------------------
	
	A MasterGone message is queued for all servers in the same site as the master
	gateway when the master gateway has been removed with the Gateway Installer, if
	the master gateway was auto-propagating. A gateway is an auto-propagating
	gateway if it was installed with the checkbox All in Site Servers Can Access
	selected. If the master gateway was not an auto-propagating gateway, no messages
	are sent to other servers.
	
	Site List
	---------
	
	This message is sent from a bridge server to other servers in its site. It
	contains a list of servers in other sites the bridge server can talk to.
	
	Link List
	---------
	
	This message is sent from a bridge server in one site to its corresponding bridge
	server in another site. It contains a list of servers in the originator's site.
	
	New Request
	-----------
	
	The Mail Network Administrator displays this message for message types that it
	does not currently understand. This may be corrected by using a current version
	of the Mail Network Administrator.
	
	Additional query words: 3.00 3.10
	
	======================================================================
	Keywords          :  
	Technology        : kbMailSearch kbZNotKeyword3 kbMailATN300 kbMailATN310
	Version           : WINDOWS:3.0,3.1
	
	=============================================================================
	

{% endraw %}
