---
layout: page
title: "Q175950: HOWTO: Change the Name of a Visual SourceSafe Database"
permalink: /kb/175/Q175950/
---

## Q175950: HOWTO: Change the Name of a Visual SourceSafe Database

{% raw %}

	Article: Q175950
	Product(s): Microsoft SourceSafe
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbSSafe500 kbSSafe600 kbFAQ kbSsafe600FAQ
	Last Modified: 18-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual SourceSafe for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	SourceSafe stores the names of previously opened databases in the registry of
	the client's workstation. Changing the database name involves both changing the
	Database_Name .ini variable in the srcsafe.ini, either by directly editing the
	srcsafe.ini or through the Visual SourceSafe administrator and then removing and
	re-adding the entry to the client's list of databases.
	
	MORE INFORMATION
	================
	
	To change the name of a Visual SourceSafe database, do the following:
	
	1. Open the database in the Visual SourceSafe Administrator program.
	
	2. Set the Database name in the General Tab of the Tools\Options dialog box.
	
	By doing this, you set the database name in the srcsafe.ini. This will be the
	default name that users see when they open a database for the first time.
	However, users are not required to use this name.
	
	In the client machine's registry, Visual SourceSafe stores information concerning
	which databases a user has connected to. Therefore each user must perform the
	following steps to update their database list:
	
	1. Browse for the Database again and select the srcsafe.ini. To do this, go to
	  the Visual SourceSafe Explorer and follow these steps:
	
	  a. On the File menu, click "Open SourceSafe Database..."
	
	  b. Click Browse.
	
	  c. Navigate the Find Database dialog box and find the appropriate srcsafe.ini
	     file.
	
	  d. Click Open.
	
	2. You will be prompted to rename the database since it is already in the list.
	
	The new Database name will be reloaded into the registry.
	
	Additional query words: registry rename
	
	======================================================================
	Keywords          : kbSSafe500 kbSSafe600 kbFAQ kbSsafe600FAQ 
	Technology        : kbSSafeSearch kbAudDeveloper kbSSafe600 kbSSafe500
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
