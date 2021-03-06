---
layout: page
title: "Q190005: A Site Set Up for Anonymous Access Prompts Users for Password"
permalink: /kb/190/Q190005/
---

## Q190005: A Site Set Up for Anonymous Access Prompts Users for Password

{% raw %}

	Article: Q190005
	Product(s): Internet Information Server
	Version(s): 3.0,4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 01-MAR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server versions 3.0, 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Users are prompted for a user name and password when logging on to a Web site
	that has been set up for anonymous access.
	
	CAUSE
	=====
	
	The anonymous user account (by default, IUSR_<computer_name>) may need to
	be resynchronized. In other words, the password listed for the anonymous account
	under User Manager for Domains, and the password again listed for that anonymous
	account in the Internet Service Manager (ISM), do not currently match.
	
	WORKAROUND
	==========
	
	To work around this problem, do either of the following (each option is
	described in more detail below):
	
	- If you are running Internet Information Server (IIS) 4.0 and using anonymous
	  user accounts defined on the local computer, consider enabling Automatic
	  Password Synchronization.
	
	  -or-
	
	- Manually set the password for the anonymous user account in both the Internet
	  Service Manager (ISM) and the User Manager for Domains to the same value. The
	  procedure for doing this differs, depending on whether you are using IIS 3.0
	  or 4.0. The instructions for each version are given below.
	
	Turn on Automatic Password Synchronization in IIS 4.0
	-----------------------------------------------------
	
	Synchronization may not work on a backup domain controller (BDC), or when the
	original anonymous account has been deleted and re-created. Furthermore, it
	should not be used with remote computers. The following information is taken
	from the Online Help in IIS 4.0 is about automatic password synchronization, and
	it further explains when it should be used.
	
	  Enable Automatic Password Synchronization:
	
	  When you create a new anonymous account, you must make sure that your
	  Web site and Windows NT password settings are identical. Select this
	  option to automatically synchronize your anonymous password settings
	  with those set in Windows NT.
	
	  Important:
	
	  Password synchronization should only be used with anonymous user
	  accounts defined on the local computer, not with anonymous accounts
	  remote computers.
	
	To turn on automatic password synchronization, perform the following steps:
	
	1. In the ISM, open the Web Properties for your web site.
	
	2. On the Directory Security tab, under Anonymous Access and Authentication
	  Control, click Edit.
	
	3. Under Allow Anonymous Access, click Edit.
	
	4. Verify that the correct user name is listed, and then select the Enable
	  Automatic Password Synchronization check box.
	
	IIS 4.0 Instructions to Manually Synchronize Passwords
	------------------------------------------------------
	
	If you choose not to enable automatic password synchronization in IIS 4.0,
	perform the following steps to manually synchronize the user name and password
	used by both User Manager for Domains and the ISM:
	
	1. In User Manager for Domains, set the password for the anonymous account.
	
	2. In the ISM, open the Web Properties for your Web site.
	
	3. On the Directory Security tab, under Anonymous Access and Authentication
	  Control, click Edit.
	
	4. Under Allow Anonymous Access, click Edit.
	
	5. Set the user name and password to the same settings you specified in User
	  Manager for Domains.
	
	  NOTE: The Enable Automatic Password Synchronization check box must be cleared
	  in order to manually set the password.
	
	IIS 3.0 Instructions to Manually Synchronize Passwords
	------------------------------------------------------
	
	1. In User Manager for Domains, set the password for the anonymous account.
	
	2. In the ISM, open the WWW Service properties.
	
	3. On the Service tab, under Anonymous Logon, set the user name and password to
	  the same settings you specified in User Manager for Domains.
	
	(c) Microsoft Corporation 2000, All Rights Reserved. Contributions by Kevin
	Zollman, Microsoft Corporation.
	
	
	Additional query words: login logon sign id pass word machine_name MMC machinename username anonomous akz
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis400 kbiis300
	Version           : :3.0,4.0
	Issue type        : kbprb
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
