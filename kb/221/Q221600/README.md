---
layout: page
title: "Q221600: Working with Distributed Authoring and Versioning (DAV) and Web"
permalink: /kb/221/Q221600/
---

## Q221600: Working with Distributed Authoring and Versioning (DAV) and Web

{% raw %}

	Article: Q221600
	Product(s): Internet Information Server
	Version(s): 5.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 11-DEC-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Microsoft Internet Information Services (IIS) version 5.0 supports the
	Distributed Authoring and Versioning (DAV) extensions to the HTTP protocol as
	defined in RFC 2518. You can use Web folders from Microsoft Office 2000 or
	Windows 2000 with an IIS 5.0 computer to take advantage of the DAV features when
	authoring.
	
	MORE INFORMATION
	================
	
	The following information will lead you through the various steps and possible
	errors that can occur when configuring Web folders.
	
	NOTE: This example uninstalls the FrontPage Server Extensions from your default
	Web site. If this is not acceptable for your default Web site, you may want to
	try these steps on an alternate testing server.
	
	1. In order to use DAV only, ensure that the FrontPage Server Extensions are not
	  installed (they can be reinstalled later):
	
	  a. Open up Internet Services Manager in the MMC.
	
	  b. Right-click your default Web site.
	
	  c. Select All Tasks on the pop-up menu.
	
	  d. If Remove Server Extensions is an option, do the following:
	
	     1. Click Remove Server Extensions.
	
	     2. Check the box to preserve the FrontPage metadata and click OK.
	
	2. Create a virtual directory for testing:
	
	  a. Create a new folder named "C:\DavTests".
	
	  b. Open Internet Services Manager in the MMC.
	
	  c. Right-click your default Web site.
	
	  d. Select New, and then select Virtual Directory on the pop-up menu.
	
	  e. Click Next to start the wizard.
	
	  f. Enter "davtests" for the alias and click Next.
	
	  g. Enter the folder "C:\DavTests" and click Next.
	
	  h. Select Read and Run Scripts, and then click Next.
	
	  i. Click Finish to complete the wizard.
	
	  j. Right-click the new virtual directory and click Properties on the pop-up
	     menu.
	
	  k. Select the Virtual Directory tab and verify that only Read Access is
	     currently selected.
	
	  l. Move this window to the side for now, as you'll need this information
	     later.
	
	3. Create a new Web folder for the virtual directory you just created:
	
	  a. Double-click My Computer on your desktop.
	
	  b. Double-click Web Folders.
	
	  c. Double-click Add Web Folder.
	
	  d. Enter "http://localhost/davtests" in the text box provided and click Next.
	
	  e. Enter "Dav Tests" for the name and click Finish.
	
	  f. Double-click the new Dav Tests Web folder. You should see an empty folder.
	
	  g. Move this window to the side for now as well.
	
	4. Create two pages for testing:
	
	  a. Copy the following ASP code and save it as "Hello.asp" on your desktop:
	
	  <% @Language="VBSCRIPT" %>
	  <html>
	  <head><title>DAV Test Page</title></head>
	  <body>
	  <%="Hello World!"%>
	  </body>
	  </html>
	
	  b. Copy the following text and save it as "Hello.txt" on your desktop:
	
	  Hello World!
	
	5. The following section discusses possible configurations and the errors that
	  you may see when working with Web folders. Switch back to the Virtual
	  Directory tab and verify again that only Read Access is currently selected.
	
	  a. Enabling Write Access:
	
	     1. Try to drag the Hello.txt file into the Dav Tests Web folder.
	
	     2. You should get an error stating that the file could not be copied.
	
	     3. Switch back to the Virtual Directory tab, check the Write Access box,
	        and click Apply.
	
	  b. Enabling Directory Browsing:
	
	     1. Drag the Hello.txt file into the Dav Tests Web folder, and then refresh
	        the window.
	
	     2. You should see an empty folder.
	
	     3. Switch back to the Virtual Directory tab, check the Directory Browsing
	        box, and click Apply.
	
	     4. Refresh the Dav Tests window.
	
	     5. You should now see the Hello.txt file.
	
	  c. Enabling and Disabling Script Source Access:
	
	     1. Try to drag the Hello.asp file into the Dav Tests Web folder.
	
	     2. You should get an error stating that the file could not be copied.
	
	     3. Switch back to the Virtual Directory tab, check the Script Source
	        Access box, and click Apply.
	
	     4. Drag the Hello.asp file into the Dav Tests Web folder.
	
	     5. You should see the Hello.asp file.
	
	     6. Open Notepad and move it to the side.
	
	     7. Drag the "Hello.asp file into Notepad. You should see the ASP source
	        code.
	
	     8. Drag the Hello.txt file into Notepad, and you should see the text.
	
	     9. Switch back to the Virtual Directory tab, uncheck the Script Source
	        Access box, and click Apply.
	
	     10. Try to drag the Hello.asp file into Notepad.
	
	     11. You should get an error stating that the file could not be copied.
	
	     12. Drag the Hello.txt file into Notepad. You should see the text.
	
	     13. Switch back to the Virtual Directory tab, check the Script Source
	        Access box, and click Apply.
	
	Additional query words: iis dav asp
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis500
	Version           : :5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
