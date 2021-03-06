---
layout: page
title: "Q143104: FP: Browsing Web Returns List of Files Instead of Home Page"
permalink: /kb/143/Q143104/
---

## Q143104: FP: Browsing Web Returns List of Files Instead of Home Page

{% raw %}

	Article: Q143104
	Product(s): Word Front Page
	Version(s): windows:1.0,1.1,97
	Operating System(s): 
	Keyword(s): kbdta
	Last Modified: 04-OCT-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft FrontPage 97 for Windows with Bonus Pack 
	- Microsoft FrontPage for Windows, versions 1.0, 1.1 
	-------------------------------------------------------------------------------
	
	For a Microsoft FrontPage 2000 version of this article, see Q205479.
	
	For a Microsoft FrontPage 98 version of this article, see Q194328.
	
	SYMPTOMS
	========
	
	If you are running the FrontPage Personal Web Server and you browse a FrontPage
	Web site, you may see a list of files in the Web's directory instead of the home
	page.
	
	CAUSE
	=====
	
	This behavior occurs because the FrontPage Personal Web Server looks for a home
	page with a name specified in the Srm.cnf file in the server's \conf directory.
	A page with this name must reside in the default Web folder when using the
	FrontPage Personal Web server. In FrontPage 1.1 and 97 this folder is typically
	C:\FrontPage Webs\Content. In FrontPage 1.0, this folder is typically
	C:\Content.
	
	The default home page for the FrontPage Personal Web Server is Index.htm.
	
	RESOLUTION
	==========
	
	To correct this behavior, you may either rename your home page to Index.htm or
	reconfigure the FrontPage Personal Web Server to serve the home page name of
	your choosing.
	
	If you choose to rename your home page, you may need to correct any links in the
	Web that point back to the home page. If you are using FrontPage 1.1 and 97, you
	will be prompted to automatically update incoming links.
	
	If you choose to reconfigure the FrontPage Personal Web Server to serve the home
	page name of your choosing, please see the following article in the Microsoft
	Knowledge Base:
	
	  Q150681 FP: How to Use a Document Other Than Index.htm as Default Page
	
	NOTE: Other Web servers, use different default home page file names, such as
	Index.html, Welcome.htm, Welcome.html, Default.htm, or Default.html.
	
	Additional query words: front page
	
	======================================================================
	Keywords          : kbdta 
	Technology        : kbFrontPageSearch kbFrontPage1xSearch kbFrontPage97Search kbZNotKeyword3 kbFrontPage100 kbFrontPage110
	Version           : windows:1.0,1.1,97
	Hardware          : x86
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
