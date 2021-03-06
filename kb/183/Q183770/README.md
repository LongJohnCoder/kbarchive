---
layout: page
title: "Q183770: SMS: Snmpelea Unable to Open Security Event Log"
permalink: /kb/183/Q183770/
---

## Q183770: SMS: Snmpelea Unable to Open Security Event Log

{% raw %}

	Article: Q183770
	Product(s): Microsoft Systems Management Server
	Version(s): winnt:1.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-SEP-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 1.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you apply the appropriate fix (for your version of Windows NT) mentioned
	in the Microsoft Knowledge Base article Q142615 "Event Log Service Fails to
	Check Access to Security Log File," when you run Systems Management Server, the
	SNMP Event Log Extension Agent (Snmpelea) generates the following Event ID 3007
	error:
	
	  Error opening event log file Security. Log will not be processed. Return code
	  from OpenEventLog is 1314.
	
	CAUSE
	=====
	
	The updated Eventlog.dll file requires a special privilege to access the
	security log.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Systems Management Server
	version 1.2. This problem has been corrected in the latest U.S. service pack for
	Systems Management Server version 1.2. For information on obtaining the service
	pack, query on the following word in the Microsoft Knowledge Base (without the
	spaces):
	
	  S E R V P A C K
	
	WORKAROUND
	==========
	
	To work around this problem, obtain the hotfix mentioned in the STATUS section
	of this article, or wait for the next Systems Management Server service pack.
	The hotfix should have the following timestamp:
	
	  4/3/98   9:31pm      112,032 Snmpelea.dll
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbSMSSearch kbSMS120
	Version           : winnt:1.2
	Hardware          : ALPHA x86
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
