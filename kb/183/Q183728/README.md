---
layout: page
title: "Q183728: BUG: &quot;Failed To Reload Project&quot; Err Opening VB Group File"
permalink: /kb/183/Q183728/
---

## Q183728: BUG: &quot;Failed To Reload Project&quot; Err Opening VB Group File

{% raw %}

	Article: Q183728
	Product(s): Microsoft SourceSafe
	Version(s): 
	Operating System(s): 
	Keyword(s): kbSSafe500bug kbSSafe600bug
	Last Modified: 01-MAY-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Control Creation Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Opening a Visual Basic group file (.vbg) under source control generates the
	following error:
	
	  Failed to Reload the Project. Please close the project from the file menu and
	  re-open it to get the correct versions of all the files loaded into memory.
	
	CAUSE
	=====
	
	The .vbg file may have been added to SourceSafe, marking it read-only.
	
	Please refer to the REFERENCES section for other articles relating to this error
	message.
	
	RESOLUTION
	==========
	
	Before opening the .vbg file, remove the read-only attribute. In addition, if
	the .vbg file has been added to SourceSafe, delete it, making sure the "Destroy
	permanently" option is checked. Placing the group file under source control is
	currently unsupported.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products listed at
	the beginning of this article.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a new Visual Basic (VB) project (.vbp), and save it as "Project1".
	  From the Tools menu, choose SourceSafe, and then select Add Project to
	  SourceSafe.
	
	2. From the File menu, choose Add Project, and add a new project.
	
	3. Save the new .vbp as "Project2" and add it to SourceSafe using the menu
	  options given in Step 1.
	
	4. Exit VB, and save the .vbg file as "Group1" when prompted.
	
	5. Right-click the Group1.vbg, and then select Properties.
	
	6. Set the read-only flag.
	
	7. Restart VB and open Group1.vbg.
	
	8. Select "Yes" when you see "Get latest checked-in version of files when
	  opening the VB Project".
	
	  NOTE: Make sure to have this option set to either "Ask" or "Yes". From the
	  Tools menu, click Sourcesafe and then select Options.
	
	REFERENCES
	==========
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q176351 BUG: Referenced Project Causes "Failed to Reload the Project"
	
	  Q177409 BUG: "Failed to Reload Project" Error When Checking In VB File
	
	  Q174650 PRB: VBG Files Do Not Appear to Work with Visual SourceSafe
	
	Additional query words:
	
	======================================================================
	Keywords          : kbSSafe500bug kbSSafe600bug 
	Technology        : kbVBSearch kbSSafeSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVB500 kbVB600 kbZNotKeyword3 kbSSafe600 kbSSafe500
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
