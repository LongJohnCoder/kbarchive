---
layout: page
title: "Q321141: HOW TO: Disable or Remove Unnecessary IIS Services"
permalink: /kb/321/Q321141/
---

## Q321141: HOW TO: Disable or Remove Unnecessary IIS Services

{% raw %}

	Article: Q321141
	Product(s): Internet Information Server
	Version(s): 4.0,5.0
	Operating System(s): 
	Keyword(s): kbHOWTOmaster
	Last Modified: 22-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 4.0 
	- Microsoft Internet Information Services version 5.0 
	- Microsoft Internet Information Services version 5.1 
	-------------------------------------------------------------------------------
	
	
	IN THIS TASK
	------------
	
	- SUMMARY
	
	   - Disable IIS Services in IIS 4.0
	- Remove IIS Services in IIS 4.0
	- Disable IIS Services in IIS 5.0 and IIS 5.1
	- Remove IIS Services in IIS 5.0 and IIS 5.1
	
	SUMMARY
	=======
	
	This step-by-step article describes how to temporarily disable unnecessary
	Internet Information Server (IIS) and Internet Information Services (IIS)
	services to keep the services from being used except under controlled
	circumstances, and how to remove individual IIS services if you have no need for
	them.
	
	Disable IIS Services in IIS 4.0
	-------------------------------
	
	1. In Microsoft Windows NT 4.0, click Start, click Settings, click Control
	  Panel, and then double-click Services.
	
	2. Scroll through the list of services, click to select the service that you
	  want to disable, and then click Startup.
	
	3. Click to select Disabled, and then click OK.
	
	4. Repeat steps 2 and 3 for each service that you want to disable.
	
	5. To exit, click Close, and then close Control Panel.
	
	Remove IIS Services in IIS 4.0
	------------------------------
	
	1. In Windows NT 4.0, click Start, click Programs, click Windows NT 4.0 Option
	  Pack, and then click Windows NT 4.0 Option Pack Setup.
	
	2. In the Windows NT 4.0 Option Pack Setup window, click Next, and then click
	  Add/Remove.
	
	3. Click to select Internet Information Server (IIS), and then click Show
	  Subcomponents.
	
	4. Click to clear the check box next to the subcomponent or subcomponents of IIS
	  that you want to remove. For example, if you clear the File Transfer Protocol
	  (FTP) Server check box, the FTP service will be removed from the Windows NT
	  4.0 server.
	
	5. When you have finished clearing the subcomponent check boxes, click OK, click
	  Next, and then click Finish.
	
	NOTE: You can use this process to add subcomponents by selecting instead of
	clearing the subcomponent check box, but you may have to have the Windows NT 4.0
	Option Pack CD available.
	
	Disable IIS Services in IIS 5.0 and IIS 5.1
	-------------------------------------------
	
	1. Open Control Panel. To do this with Microsoft Windows 2000 (which uses IIS
	  5.0), click Start, click Settings, and then click Control Panel. To do this
	  with Microsoft Windows XP (which uses IIS 5.1), click Start, and then click
	  Control Panel.
	
	2. In Control Panel, double-click Administrative Tools, and then double-click
	  Computer Management.
	
	3. In the left pane of the Computer Management Services window, expand Services
	  and Applications, and then click to select Services.
	
	4. In the right pane of the Computer Management window, scroll through the
	  services that are listed in the Name column, right-click the service that you
	  want to disable, and then click Properties.
	
	5. The service_name window will appear with the General tab selected (note that
	  you can click the other tabs at the top of the window to see other options).
	  Click the drop-down arrow next to Startup type, and then select Disabled.
	
	6. Click OK.
	
	7. Repeat steps 3 through 6 for each service that you want to disable.
	
	8. Verify that the Status of the service is Started, right-click the service,
	  and then click Stop.
	
	9. To exit, close the Computer Management window.
	
	Remove IIS Services in IIS 5.0 and IIS 5.1
	------------------------------------------
	
	1. Open Control Panel. To do this with Microsoft Windows 2000 (which uses IIS
	  5.0), click Start, click Settings, and then click Control Panel. To do this
	  with Microsoft Windows XP (which uses IIS 5.1), click Start, and then click
	  Control Panel.
	
	2. In Control Panel, double-click Add/Remove Programs. In the Add/Remove
	  Programs window, click Add/Remove Windows Components (located in the lower
	  left side of the window).
	
	3. In the Windows Component Wizard window, click to select Internet Information
	  Services (IIS), and then click Details.
	
	4. Scroll through the list of Subcomponents of Internet Information Services
	  (IIS), click to clear the check box next to the subcomponent or subcomponents
	  that you want to remove, click OK, click Next, and then click Finish.
	
	NOTE: You can use this process to add subcomponents by selecting instead of
	clearing the subcomponent check box, but you may have to have the operating
	system CD available.
	
	5. To exit, click Close in the Add/Remove Programs window, and then close
	  Control Panel.
	
	Additional query words:
	
	======================================================================
	Keywords          : kbHOWTOmaster 
	Technology        : kbiisSearch kbiis500 kbiis400 kbiis510
	Version           : :4.0,5.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
