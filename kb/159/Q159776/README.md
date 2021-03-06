---
layout: page
title: "Q159776: FIX: VC++ Crash When Adding Test Case Under Source-Code Control"
permalink: /kb/159/Q159776/
---

## Q159776: FIX: VC++ Crash When Adding Test Case Under Source-Code Control

{% raw %}

	Article: Q159776
	Product(s): Microsoft SourceSafe
	Version(s): 3.0 4.0 4.1 4.2
	Operating System(s): 
	Keyword(s): kbusage kbSSafe400bug kbSSafe500fix kbVC400 kbVC410 kbVC420
	Last Modified: 04-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 4.0, 4.1, 4.2 
	- Microsoft Visual SourceSafe for Windows, version 4.0 
	- Microsoft Test for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you add a new test case to a Visual Test project and the project is under
	source-code control, Developer Studio may cause one of the following errors:
	
	  MSDEV.EXE - Application Error
	
	  MSDEV caused an invalid page fault in module MSVCBLD.PKG at <memory
	  location>.
	
	  The instruction at <memory location> referenced memory at "<memory
	  location>". The memory could not be "read".
	
	  MSDEV caused an invalid page fault in module SSSCC.DLL at <memory
	  location>.
	
	  MSDEV caused an invalid page fault in module KERNEL32.DLL at <memory
	  location>.
	
	RESOLUTION
	==========
	
	You must remove the project from source-code control before adding a new test
	case.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Visual SourceSafe version
	5.0.
	
	MORE INFORMATION
	================
	
	Steps To Reproduce Behavior
	---------------------------
	
	1. Under File, New, select Project Workspace (MFC AppWizard EXE). Accept all
	  defaults.
	
	2. Under Tools, select Source Control, then select Add To Source Control (keep
	  all files checked out).
	
	3. Select the TestView tab (the one with the red check).
	
	4. Right-click the project name and select New.
	
	5. Give the item a name and leave the type as "Test Case."
	
	6. Click OK. Developer Studio will probably generate a fatal application error.
	
	Additional query words: ssvt visualc
	
	======================================================================
	Keywords          : kbusage kbSSafe400bug kbSSafe500fix kbVC400 kbVC410 kbVC420 
	Technology        : kbVCsearch kbVC400 kbSSafeSearch kbAudDeveloper kbVC410 kbTest kbVC420 kbSSafe400
	Version           : 3.0 4.0 4.1 4.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
