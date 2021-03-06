---
layout: page
title: "Q233018: FP: Enabling Database Features Without Server Extensions"
permalink: /kb/233/Q233018/
---

## Q233018: FP: Enabling Database Features Without Server Extensions

{% raw %}

	Article: Q233018
	Product(s): Word Front Page
	Version(s): 
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 15-APR-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 2002 
	- Microsoft FrontPage 2000 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to enable the Active Server Pages (ASP) features on
	Web servers that are not running the FrontPage Server Extensions from
	Microsoft.
	
	You can run the FrontPage "Save to Database" feature and the pages that are
	generated by the Database Results Wizard on any server that supports ASP and has
	sufficient database support for the database system that you are using.
	
	Although either FrontPage 2000 Server Extensions from Microsoft or FrontPage 2002
	Server Extensions from Microsoft are required to create pages that use the ASP
	features, FrontPage Server Extensions are not required to run the pages that are
	generated by the ASP features.
	
	NOTE: Microsoft recommends that you install Microsoft Data Access Components
	(MDAC) 2.1 for full support on all Web servers that are based on Microsoft
	Windows, Microsoft Windows NT, or Microsoft Windows 2000.
	
	MORE INFORMATION
	================
	
	Getting Ready to Use the ASP Features in FrontPage
	--------------------------------------------------
	
	Before you can use the ASP features in FrontPage, you must install the components
	that are listed in the following Microsoft Knowledge Base articles. Select the
	article for the version of FrontPage that you are using:
	
	  Q312638 FP: What You Need to Use Active Server Pages (ASP) in FrontPage 2000
	
	  Q318287 FP2002: What You Need to Use Active Server Pages (ASP) in FrontPage
	  2002
	
	Create and Publish Your Database Web
	------------------------------------
	
	1. If you are using a network-based data connection, such as a Microsoft SQL
	  Server connection or an Oracle server connection, you must confirm that the
	  network location is accessible from the destination Web site. If you are
	  using a system data source name (DSN), you must confirm that that the system
	  DSN is valid on the system that is running the destination Web server.
	
	2. Create your database Web. Note the following:
	
	   - If you are using a Web server, the Web server must be a Microsoft Internet
	     Information Services (IIS) server, a Microsoft NT Peer Web Server (NTPWS),
	     or a Microsoft Personal Web Server (MSPWS) that meets the following
	     requirements:
	
	      - Supports Active Server Pages
	      - Has Microsoft Data Access Components (MDAC) 2.1 or later installed
	      - Has the FrontPage Server Extensions installed
	
	     For more information, please see the Knowledge Base articles listed in the
	     "Getting Ready to Use the ASP Features in FrontPage" section of this
	     article.
	
	   - If you are using a disk-based Web, you cannot confirm that the pages work
	     before you publish the pages.
	
	   - If you are using a Web server to author the pages, confirm that the pages
	     work before you publish the pages to the unextended server.
	
	3. When the Web is complete, you can publish the Web by using FTP, or you can
	  copy the Web by using Windows Explorer or the command prompt.
	
	   - If you are publishing by using FTP, follow these steps in FrontPage 2000:
	
	     1. On the File menu, click Publish Web.
	
	     2. Type the FTP URL for the destination in the "Specify the location to
	        publish your web to" section of the Publish Web dialog box.
	
	   - If you are copying through Windows Explorer or the command prompt, make
	     sure that you copy all the files from your local copy of the Web to the
	     destination.
	
	4. On the destination server, find the entry in the Web server's configuration
	  file or files. Make sure that the URL for the folder that you just copied or
	  published by using FTP is configured as an application root. For more
	  information about this process, see your Web server documentation or ISP
	  provider documentation. You must be certain that the setting is created on
	  the HTTP URL for the published files.
	
	Troubleshooting
	---------------
	
	If the published Web is not an application root, you may receive an error message
	similar to the following when you browse to a page that uses a database
	connection:
	
	  The database connection named 'Sample' is undefined.
	
	  This problem can occur if:
	
	- the connection has been removed from the web
	- the file 'global.asa' is missing or contains errors
	- the root folder does not have Scripting permissions enabled
	- the web is not marked as an Application Root
	
	For additional information about this error message, click the article numbers
	below to view the articles in the Microsoft Knowledge Base:
	
	  Q219170 FP2000: Error Browsing Database Results Pages After Publishing from
	  Disk-Based Web
	
	  Q265174 FP2000: "Connection Undefined" Error When You View an Active Server
	  Page in the Web Browser
	
	  Q265323 FP2000: Database Connection List Is Empty When You View Database
	  Results Properties
	
	  Q292628 FP2002: Database Connection Undefined After Publishing Web
	
	If the published Web meets all other requirements described earlier in this
	article, and you do not receive an error message when you submit a database
	form, but no data is added to the database on the Web server, the error may be
	suppressed in the ASP code. For additional information about this error, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q314440 FP2002: Confirmation Form Appears But No Information Is Written to
	  the Database
	
	REFERENCES
	==========
	
	For additional information about the Database command being unavailable in
	FrontPage 2000, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q232532 FP2000: Database Command on Insert Menu Unavailable
	
	For additional information about interoperability between FrontPage 2000 database
	features and Sun Chili!Soft ASP, click the article number below to view the
	article in the Microsoft Knowledge Base:
	
	  Q225204 FP2000: Using FrontPage Database Features on Servers Running Sun
	  Chili!Soft ASP
	
	Additional query words: fpodbc fpfaq front page
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch kbFrontPage2002 kbFrontPage2000Search kbFrontPage2002Search kbZNotKeyword5
	Version           : :
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
