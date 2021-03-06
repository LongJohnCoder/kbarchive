---
layout: page
title: "Q188055: SMS: How to Remove Inactive SMS Site Servers"
permalink: /kb/188/Q188055/
---

## Q188055: SMS: How to Remove Inactive SMS Site Servers

{% raw %}

	Article: Q188055
	Product(s): Microsoft Systems Management Server
	Version(s): 1.2
	Operating System(s): 
	Keyword(s): kbConfig kbInventory kbSCMan smsinv smsconfig smssiteconfigman
	Last Modified: 17-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	If Systems Management Server child site servers (primary or secondary) are
	removed from the network, before removing them from the parent's database
	through the Systems Management Server Administrator program, you may experience
	errors when you attempt to communicate with them. You will notice that System
	Jobs destined for the 'removed' site go into a retrying state.
	
	MORE INFORMATION
	================
	
	To remove the servers from the database, run the "preinst /delsite:{<child
	site code>, <parent site code>}" command, as in the following example:
	
	    preinst /delsite:{prf,scf}
	
	For more information on this process, see the BackOffice Resource Kit 1 SMS
	Guide, page 2.
	
	The child site's database entry should be deleted immediately. Either refresh the
	Systems Management Server Administrator program UI, or quit the Systems
	Management Server Administrator program and start it again.
	
	
	When the refresh occurs, you may notice the following error:
	
	  Some machines in your database are associated with sites or domains that do
	  not appear in your Sites tree. The missing items are listed below.
	
	It would then be followed by the site code and domain name that was removed using
	the steps above. This error occurs because there are still client records in the
	database that belonged to the deleted site. To remove the clients, perform the
	following steps:
	
	1. Start the Systems Management Server Administrator program. On the File menu,
	  click Execute Query.
	
	2. Under Query, select All Personal Computers.
	
	3. Under Query Result Format, select Identification and click OK.
	
	4. Click the word Site in the Site column. This sorts the list by site code.
	
	5. Delete the clients associated with the deleted site.
	
	After the clients have been deleted, quit the Systems Management Server
	Administrator program and then start it again, to confirm that the error does
	not reoccur.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbConfig kbInventory kbSCMan smsinv smsconfig smssiteconfigman 
	Technology        : kbSMSSearch kbSMS120
	Version           : :1.2
	Issue type        : kbhowto kbinfo
	
	=============================================================================
	

{% endraw %}
