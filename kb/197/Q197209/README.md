---
layout: page
title: "Q197209: WD97: Calculation Form Field Is Not Updated"
permalink: /kb/197/Q197209/
---

## Q197209: WD97: Calculation Form Field Is Not Updated

{% raw %}

	Article: Q197209
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbdta word8 word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After you create a form to calculate a total, the Calculation form field is not
	updated automatically.
	
	CAUSE
	=====
	
	A possible cause is that the "Calculate on exit" option is not set for the form
	fields that are referenced by the expression contained in the Calculation form
	field.
	
	RESOLUTION
	==========
	
	IMPORTANT NOTE: In some earlier versions of Microsoft Word, to update a
	Calculation form field, you had to use a macro. However, in Microsoft Word 97,
	you should use the "Calculate on exit" option to update your form fields. If you
	have an Entry or Exit macro assigned to your form fields, you need to remove the
	macro in the form field options of each of the form fields that the calculation
	form field calculates.
	
	To correct this problem, use the "Calculate on exit" option to update the
	Calculation form field. To do this, follow these steps:
	
	NOTE: The "Calculate on exit" option is set only on the form fields that you type
	information into that are referenced by the expression of the Calculation form
	field. The "Calculate on exit" check box has no effect if you set it in the
	"Text Form Field Options" of a Calculation form field.
	
	1. Unprotect your form. To do this, click Unprotect Document on the Tools menu.
	
	2. Click to select a form field that is referenced in the expression of the
	  Calculation form field.
	
	  For example, if the expression of your Calculation form field is
	  "Item1*Price1", click to select the form field named "Item1."
	
	3. Right-click the selected form field, and click Properties on the shortcut
	  menu that appears.
	
	4. In the "Text Form Field Options" dialog box, select the Calculate on exit
	  check box.
	
	  NOTE: If you have an Entry or Exit macro assigned to this form field, clear
	  the Entry or Exit macro. To do this, in either the Entry or Exit box, click
	  the down arrow and click to select "(none)".
	
	5. Click OK to close the "Text Form Field Options" dialog box.
	
	6. Repeat steps 2-5 for each form field referenced in the expression of your
	  Calculation form field.
	
	7. On the Tools menu, click Protect Document.
	
	8. In the Protect Document dialog box, click to select Forms and click OK.
	
	MORE INFORMATION
	================
	
	For additional information, click the article number below to view the article
	in the Microsoft Knowledge Base:
	
	  Q157463 WD97: How to Use Calculate on Exit in a Forms Document
	
	Additional query words: update updating field fields form forms bookmarks formfield
	
	======================================================================
	Keywords          : kbdta word8 word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
