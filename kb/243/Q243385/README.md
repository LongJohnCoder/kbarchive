---
layout: page
title: "Q243385: Enabling Network Abstraction Layer Logging and Setting Logging"
permalink: /kb/243/Q243385/
---

## Q243385: Enabling Network Abstraction Layer Logging and Setting Logging

{% raw %}

	Article: Q243385
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0
	Operating System(s): 
	Keyword(s): kbtool kbsms200
	Last Modified: 22-APR-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server version 2.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following registry files to enable and disable network abstraction layer
	logging are included with the Microsoft BackOffice 4.5 Resource Kit CD-ROM and
	the System Management Server (SMS) 2.0 CD-ROM:
	
	- Turn_on_nal_logging.reg
	
	- Turn_off_nal_logging.reg
	
	By default, network abstraction layer logging is disabled. However, you can
	enable logging to populate the SMS server and client log files with network
	abstraction layer information to troubleshoot connectivity problems. If you want
	to further increase the network abstraction layer logging level, you can
	manually increase the logging level in the registry.
	
	NOTE: To enable or disable network abstraction layer logging on a specific
	computer, you must run the .reg files on the specific computer because this is
	not a site-wide setting.
	
	MORE INFORMATION
	================
	
	When you run the Turn_on_nal_logging.reg file, the "Verbosity" level is set to 7
	(the sum of 1, 2, and 4). However, if you need even more detailed network
	abstraction layer logging, you can increase the "Verbosity" level by changing a
	value in the registry. The following registry key contains the value you can
	alter:
	
	  HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NAL\Logging
	  "Log To"=dword:00000003
	
	Verbosity: REG_DWORD
	
	These are the various verbosity levels that are defined:
	
	NAL_LOG_VERBOSITY_LEVEL_1 = Errors
	NAL_LOG_VERBOSITY_LEVEL_2 = Warnings
	NAL_LOG_VERBOSITY_LEVEL_4 = Information
	NAL_LOG_VERBOSITY_LEVEL_8 = (Not used)
	NAL_LOG_VERBOSITY_LEVEL_16 = (Not used)
	NAL_LOG_VERBOSITY_LEVEL_32 = Special Information (DLL reference count)
	NAL_LOG_VERBOSITY_LEVEL_64 = Special Information (Method entry/exit)
	NAL_LOG_VERBOSITY_LEVEL_MAX = 0xFFFFFFFF; // Maximum NAL logging verbosity level.
	
	The preceding verbosity levels can be added up to provide you with the logging
	level you need. However, if the verbosity level set by the
	Turn_on_nal_logging.reg file is not sufficient, you would typically set the
	Verbosity registry value to 0xFFFFFFFF to obtain as detailed logging as is
	possible. Afterwards, you can disable logging again when you are finished
	troubleshooting by running the Turn_off_nal_logging.reg file.
	
	IMPORTANT: Note that enabling NAL_LOG_VERBOSITY_LEVEL_32 may cause the SMS client
	to attempt a network logon to the CAP using its local SMSCliToknAcct& or
	SMSCliSvcAcct& accounts. If an account lockout policy is enabled for the
	domain, this can cause the SMSCliToknAcct& and SMSCliSvcAcct& domain
	accounts to be locked out.
	
	Additional query words: prodsms nal
	
	======================================================================
	Keywords          : kbtool kbsms200 
	Technology        : kbSMSSearch kbSMS200
	Version           : :2.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
