---
layout: page
title: "Q251297: How to Customize the Account Joiner Utility for a Specific MA"
permalink: /kb/251/Q251297/
---

## Q251297: How to Customize the Account Joiner Utility for a Specific MA

{% raw %}

	Article: Q251297
	Product(s): Microsoft Windows NT
	Version(s): 2.1
	Operating System(s): 
	Keyword(s): kbenv kbtool
	Last Modified: 21-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Metadirectory Services, version 2.1 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The Account Joiner tool is a Lightweight Directory Access Protocol (LDAP) client
	that you can use to help manage and control the join process. Use Account Joiner
	to process those connector space entries that cannot be joined by using the
	standard join rules of the management agent (MA).
	
	Account Joiner is defined in part by the Accjnr.cfg file. This is a configuration
	file that is distributed with each MA. This file defines the configuration for
	Account Joiner based on that specific MA. The Accjnr.cfg file is stored with all
	the MA templates in the Zoomserv\Data\Dsgates\* folders on the Microsoft
	Metadirectory Services (MMS) server. (The asterisk [*] represents the MA type,
	for example, LDAP-Exchange, Notes, or Vines.) When you first create a new MA,
	the Accjnr.cfg file is loaded into the directory as an attribute of the MA and
	provides MA-specific configuration for Account Joiner.
	
	You can customize Account Joiner to view certain MAs by using the View menu and
	disabling or enabling the MA. By default, all MAs are displayed. By using the
	Configure menu, you can then configure each MA to display specific settings
	based on the data contained in the MA. Account Joiner allows you to configure
	the column view for both disconnectors and the metadirectory.
	
	MORE INFORMATION
	================
	
	You can use the following commands to customize a specific MA:
	
	- View/View Metaverse: Entries are shown in both the disconnector and the
	  metaverse panel in a columnar detail view. You can use these options to
	  configure which attributes are shown in each column, the column width, and
	  the heading text for each column. The View option lets you configure the
	  disconnector (upper) panel; the Metaverse View option applies to the
	  metaverse (lower) panel.
	
	- Queries: Queries are predefined search criteria in the form of LDAP search
	  filters. Each one you define is represented by a button on the form. When you
	  click a connector entry, the metaverse is automatically searched for matches
	  by using the currently active query; the results are shown in the metaverse
	  panel. Clicking a different query button automatically performs another
	  search and replaces the previous search results. On successful searches, the
	  actual filter string associated with the current query is shown in the status
	  bar at the bottom of the form, which otherwise contains error messages. The
	  queries must be entered as LDAP search filters. For example:
	
	  (&(sn=$sn) (telephoneNumber=$telephoneNumber))
	
	The $attribute parts of the filter are replaced with the corresponding attribute
	values from the selected disconnector before the search request is submitted.
	You can customize your predefined queries for each MA. You can add, edit,
	delete, or reorder queries.
	
	- MA Options: This allows for the following customizations:
	
	   - MA Search Limit:
	     The maximum number of connector space entries to be returned from a search.
	
	   - MA Timeout Limit:
	     The waiting time in seconds before a connector space search request times
	     out. Use 0 for no limit.
	
	   - MA Filter:
	     This is another LDAP search filter (the same as the queries) that controls
	     the disconnector entries shown in the upper panel. If there are many
	     disconnected entries, you can use this filter to reduce them to a more
	     manageable number, and then change the filter to process another subset.
	
	You can customize Account Joiner for a specific MA by using the following steps:
	
	1. Click Start, point to Programs, and then click Zoomit Directory Service V2.
	
	2. Click the Account Joiner utility.
	
	3. On the Configure menu, click the MA you want to modify.
	
	4. Click the menu that corresponds to the specific configuration change you want
	  to make.
	
	For additional information about Account Joiner, click the article number below
	to view the article in the Microsoft Knowledge Base:
	
	  Q250528 Using the Account Joiner Utility in Microsoft Metadirectory Services
	
	Additional query words:
	
	======================================================================
	Keywords          : kbenv kbtool 
	Technology        : kbMMSSearch kbMMS210
	Version           : :2.1
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
