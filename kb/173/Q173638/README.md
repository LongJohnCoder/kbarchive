---
layout: page
title: "Q173638: BUG: &quot;What's This?&quot; Button Disappears from MDI Child Forms"
permalink: /kb/173/Q173638/
---

## Q173638: BUG: &quot;What's This?&quot; Button Disappears from MDI Child Forms

{% raw %}

	Article: Q173638
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0
	Operating System(s): 
	Keyword(s): kbVBp500 kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Setting both the WhatsThisButton property and the WhatsThisHelp property of an
	MDI child form to True does not enable the What's This button to appear in the
	title bar of the form.
	
	RESOLUTION
	==========
	
	According to the Help for Visual Basic 5.0, the What's This? button will appear
	in the title bar of a form when the WhatsThisHelp property and the
	WhatsThisButton property are both set to True and the following properties are
	also set as shown:
	
	     ControlBox = True
	
	     MinButton = False and/or MaxButton = False
	     BorderStyle = 1 - Fixed Single or BorderStyle = 2 - Sizable
	        Or
	     BorderStyle = 3 - Fixed Dialog
	
	However, the What's This? button fails to appear in the title bar of an MDI child
	form even when the conditions above are met.
	
	To work around this problem, you can use the Windows SetParent API to make one
	form the child of another and create the illusion of an MDI form in which the
	What's This button is functional.
	
	Step-by-Step Instructions
	-------------------------
	
	1. Start a new Standard EXE project. Form1 is added by default.
	
	2. Add another form (Form2) to the project.
	
	3. Set the following properties of Form2:
	
	        MaxButton = False
	        MinButton = False
	        WhatsThisButton = True
	        WhatsThisHelp = True
	
	4. Insert the following code to Form1's General Declarations section:
	
	        Private Declare Function SetParent Lib "user32" _
	        (ByVal hWndChild As Long, ByVal hWndNewParent As Long) As Long
	
	        Private Declare Function GetWindowLong Lib "user32" _
	        Alias "GetWindowLongA" _
	        (ByVal hwnd As Long, ByVal nIndex As Long) As Long
	        Private Declare Function SetWindowLong Lib "user32" _
	        Alias "SetWindowLongA" _
	        (ByVal hwnd As Long, ByVal nIndex As Long, ByVal dwNewLong As Long) _
	        As Long
	
	        Const WS_CHILDWINDOW = &H40000000
	        Const GWL_STYLE = (-16)
	
	5. Insert the following code to Form1's Load event procedure:
	
	        Private Sub Form_Load()
	           Dim x As Long
	           Dim y As Long
	           'Set Form1 as the parent of form2
	           x = SetParent(Form2.hwnd, Form1.hwnd)
	           Form2.Show
	
	           x = GetWindowLong(Form2.hwnd, GWL_STYLE)
	           y = x + WS_CHILDWINDOW
	           x = SetWindowLong(Form2.hwnd, GWL_STYLE, y)
	        End Sub
	
	6. Press the F5 key to run the program. You will see Form2 acting as Form1's
	  child with a What's This? Button on its toolbar.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. We are researching this bug and will post new
	information here in the Microsoft Knowledge Base as it becomes available.
	
	MORE INFORMATION
	================
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Start a new Standard EXE project. Form1 is added by default.
	
	2. Add a MDI form (MDIForm1) to the project.
	
	3. Set the following properties of Form1:
	
	     MaxButton = False
	     MDIChild = True
	     MinButton = False
	     WhatsThisButton = True
	     WhatsThisHelp = True
	
	4. Press the F5 key to run the project. The What's This ('?') button disappears
	  from Form1's title bar.
	
	Additional query words: vb5
	
	======================================================================
	Keywords          : kbVBp500 kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVBA500Search kbVBA500 kbVB500 kbZNotKeyword3
	Version           : WINDOWS:5.0
	Hardware          : x86
	Issue type        : kbbug
	
	=============================================================================
	

{% endraw %}
