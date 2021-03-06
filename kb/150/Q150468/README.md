---
layout: page
title: "Q150468: HOWTO: Clear the Contents of a DBGrid Control"
permalink: /kb/150/Q150468/
---

## Q150468: HOWTO: Clear the Contents of a DBGrid Control

{% raw %}

	Article: Q150468
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVBDB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to clear the contents of a DBGrid control. A DBGrid
	control is bound to a Data control. To clear the DBGrid control of all data, set
	the RecordSource property of the Data control so no records are returned, and
	then execute the Refresh method on the Data control. The DBGrid control displays
	the data retrieved by the Data control.
	
	MORE INFORMATION
	================
	
	The following instructions show how to create a sample program that demonstrates
	how to clear the DBGrid control. The form contains a DBGrid control bound to a
	Data control. The Data control is bound to the sample database shipping with
	Microsoft Visual Basic, BIBLIO.MDB, and the RecordSource is set to the Titles
	table. Two Command buttons are used to populate and clear the DBGrid control. To
	clear the DBGrid control, the RecordSource is set to a SQL statement that does
	not return any records. To populate the DBGrid control, the RecordSource
	property is set to the Titles table.
	
	When you run the program, the DBGrid control is immediately populated because the
	RecordSource property of the Data control is bound to the Titles table. Click
	the Command button to clear the DBGrid control.
	
	Follow these instructions to create a sample application that demonstrates this
	process:
	
	1. Start Visual Basic version 4.0. If it is already running, from the File menu,
	  select New Project.
	
	2. Add a Data control, a DBGrid control, and two Command buttons to Form1.form.
	
	3. Set the following properties for each control:
	
	     Control          Default Name       Property           Value
	     ---------------------------------------------------------------
	
	     Data Control     Data1              DatabaseName     BIBLIO.MDB
	                                         RecordSource     Title
	
	     DBGrid Control   DBGrid1            DataSource       Data1
	
	4. Copy the following code to the Code window of the Form1 form:
	
	        Option Explicit
	        Dim sql As String
	
	        Private Sub Command2_Click()
	           ' SQL statement that does not return records.
	           sql = "SELECT * From Titles Where Title = Null"
	           Data1.RecordSource = sql
	           Data1.Refresh
	           Command1.Visible = True
	           Command2.Visible = False
	        End Sub
	
	        Private Sub Command1_Click()
	        ' Set the RecordSource to fill the DBGrid control.
	           Data1.RecordSource = "Titles"
	           Data1.Refresh
	           Command1.Visible = False
	           Command2.Visible = True
	        End Sub
	
	        Private Sub Form_Load()
	           Command1.Caption = "Fill DBGrid"
	           Command1.Visible = False
	           Command2.Caption = "Clear DBGrid"
	           Command2.Visible = True
	        End Sub
	
	5. From the Run menu, select Start, or press the F5 key. Click the visible
	  Command button to clear or populate the DBGrid control.
	
	Additional query words: kbVBp400 kbVBp600 kbdse kbDSupport kbVBp
	
	======================================================================
	Keywords          : kbGrpDSVBDB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVBA600 kbVB600 kbVB400Search kbVB400 kbVB16bitSearch
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
