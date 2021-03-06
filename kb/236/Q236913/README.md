---
layout: page
title: "Q236913: Err Msg: Couldn't Open ISV MIF: &lt;ISV MIF FileName&gt;"
permalink: /kb/236/Q236913/
---

## Q236913: Err Msg: Couldn't Open ISV MIF: &lt;ISV MIF FileName&gt;

{% raw %}

	Article: Q236913
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): kberrmsg kbnetwork kbsms120 kbsms120bug
	Last Modified: 08-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you collect ISV MIF files using the Systems Management Server Inventory
	Agent (Inv32cli.exe or Invwin32.exe), you may receive the following error
	message:
	
	  Couldn't Open ISV MIF: <ISV MIF FileName>
	
	CAUSE
	=====
	
	This issue can occur if the ISV MIF file listed in the error message is already
	open by another inventory agent.
	
	RESOLUTION
	==========
	
	A supported fix is now available from Microsoft, but it is only intended to
	correct the problem described in this article and should be applied only to
	systems experiencing this specific problem. This fix may receive additional
	testing at a later time, to further ensure product quality. Therefore, if you
	are not severely affected by this problem, Microsoft recommends that you wait
	for the next Systems Management Server service pack that contains this fix.
	
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
	
	  Date      Time     Size      File name      Platform
	  ----------------------------------------------------
	  6/28/99   8:21pm   283,104   Inv32cli.exe   x86
	  6/28/99   8:21pm   296,368   Invwin32.exe   x86
	  6/28/99   8:22pm   866,576   Inv32cli.exe   Alpha
	  6/28/99   8:23pm   883,472   Invwin32.exe   Alpha
	
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2.
	
	MORE INFORMATION
	================
	
	To install the hotfix, perform the following steps on the Systems Management
	Server site server:
	
	1. Replace the Inv32cli.exe file in the
	  <SMS_root>\Site.srv\Maincfg.box\Client.src\<Platform>.bin folder
	  with the version included in the hotfix.
	
	2. Replace the Invwin32.exe file in the
	  <SMS_root>\Site.srv\Maincfg.box\Client.src\<Platform>.bin folder
	  with the version included in the hotfix.
	
	3. Replace the Invwin32.exe file in the
	  <SMS_root>\Site.srv\<Platform>.bin folder with the version
	  included in the hotfix.
	
	4. Maintenance Manager replicates the updated files to the Systems Management
	  Server logon servers on its next work cycle. To update the clients, either
	  manually run the Upgrade.bat file on each client or follow the instructions
	  in the following article in the Microsoft Knowledge Base:
	
	  Q166771 SMS: How to Force Site-Wide Client Updates
	
	5. You need to reset the site for Invwin32.exe (SMS_INVENTORY_AGENT_NT) to be
	  copied to all servers managed by the Site Configuration Manager.
	
	Additional query words: prodsms inventory isv mif
	
	======================================================================
	Keywords          : kberrmsg kbnetwork kbsms120 kbsms120bug 
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
