---
layout: page
title: "Q174426: PRB: Date in Text Box Displays Year With Four Digits"
permalink: /kb/174/Q174426/
---

## Q174426: PRB: Date in Text Box Displays Year With Four Digits

{% raw %}

	Article: Q174426
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a
	Operating System(s): 
	Keyword(s): kbYear2000 kbvfp
	Last Modified: 26-APR-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	The dates in your text boxes display the year with four digits even with the
	setting of SET CENTURY OFF.
	
	CAUSE
	=====
	
	This is by design and is necessary for year 2000 compliance.
	
	RESOLUTION
	==========
	
	To be year 2000 compliant you must display the year with four digits. If,
	however, you want to have just the two-digit year to make data entry easier, you
	can set the StrictDateEntry text box property to 0. With this property set to 0,
	the date is loosely formatted and can take a space, period, hyphen, and forward
	slash as separators. This also allows you to leave off the year, and it assumes
	the current year.
	
	Other hints to make data entry of dates easier are listed below:
	
	1. In Visual FoxPro 5.0 make sure that Set Century To <nCentury> Rollover
	  <nYear> command is set properly. A recommended setting would be:
	
	  m.nYear = Year(Date())+ 50   && Set the rollover 50 years from today.
	  Set Century To (Int(m.nYear/100)-1) Rollover (m.nYear % 100)
	
	2. Use the plus and minus keys to increment and decrement a date in a text box.
	  This only works if the entire field is selected, so you may want to set the
	  text box property SelectOnEntry to .t.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	This feature is called Auto-Century. Auto-Century was added to Visual FoxPro in
	version 3.0 to ensure that any date written in a text box had the century that
	the user intended. Auto-Century operates differently in Visual FoxPro 3.0 than
	it does in Visual FoxPro 5.0a due to minor enhancements.
	
	In version 3.0b, the text box displays 4-digit dates whenever the year is greater
	than 1999.
	
	In version 5.0a, the text box displays 4-digits whenever the century portion of
	the year is greater than SET CENTURY TO and it ignores the ROLLOVER value.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Create a form with a text box called Text1.
	
	2. From the Command window execute the following command:
	
	  Set Century Off
	
	3. Create a push button and enter the code below in the click event:
	
	  ThisForm.Text1.value = {01/01/1999}
	
	4. Create a second push button and in the click event enter this code:
	
	  ThisForm.Text1.value = {01/01/2000}
	
	When you run the form and click the buttons, you see the century displayed when
	the second button is clicked.
	
	REFERENCES
	==========
	
	Visual FoxPro Help; search on: "StrictDateEntry"
	
	(c) Microsoft Corporation 1997, All Rights Reserved. Contributions by David
	Botzenhart, Microsoft Corporation
	
	
	Additional query words: Y2K Year 2000
	
	======================================================================
	Keywords          : kbYear2000 kbvfp 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : WINDOWS:5.0,5.0a
	Issue type        : kbprb
	Solution Type     : kbnofix
	
	=============================================================================
	

{% endraw %}
