---
layout: page
title: "Q172268: PRB: Error Passing Recordset to Excel Using Automation From VB"
permalink: /kb/172/Q172268/
---

## Q172268: PRB: Error Passing Recordset to Excel Using Automation From VB

	Article: Q172268
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:4.0,5.0,6.0
	Operating System(s): 
	Keyword(s): kbinterop kbAutomation kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbExcel97
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Standard Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Professional Edition, 32-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 16-bit, for Windows, version 4.0 
	- Microsoft Visual Basic Enterprise Edition, 32-bit, for Windows, version 4.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you try to pass a Recordset object to Microsoft Excel using Automation from
	Microsoft Visual Basic 4.0, it fails with one of the following errors:
	
	  Run-time error '1004': Cannot find macro '<procedure name>'. (If you
	  are using Microsoft Excel for Windows 95, version 7.0)
	
	  -or-
	
	  Run-time error '13': Type Mismatch (If you are using Microsoft Excel 97)
	
	This article describes how you can work around this limitation and successfully
	pass a Recordset to Microsoft Excel.
	
	RESOLUTION
	==========
	
	One workaround is to pass the database and Recordset names as string arguments
	to an Excel procedure using Automation. The Excel procedure then creates the
	Database and Recordset objects and can therefore use CopyFromRecordset using its
	own Recordset object.
	
	Another workaround is to copy the Recordset into an array and pass the array to
	Excel using Automation. Following is a step-by-step example on how to do this:
	
	1. Start Visual Basic. Form1 is created by default.
	
	2. Add a command button to Form1.
	
	3. Add a data control and set its properties as follows:
	
	        DatabaseName       biblio.mdb
	        RecordSource      Authors
	
	4. Add the following code to the General Declarations section of Form1:
	
	        ' User defined type to help determine the
	        ' starting cell in the range receiving the recordset
	
	        Option Explicit
	
	        Private Type ExlCell
	           row As Long
	           col As Long
	        End Type
	
	        Private Sub CopyRecords(rs As Recordset, ws As Object, _
	          StartingCell As ExlCell)
	           Dim SomeArray() As Variant
	           Dim row As Long, col As Long
	
	           ' You might want to check if rs is not empty
	           ' before re-dimensioning the array
	           rs.MoveLast
	           ReDim SomeArray(rs.RecordCount - 1, rs.Fields.Count - 1)
	
	           ' Copy rs to some array
	           rs.MoveFirst
	           For row = 0 To rs.RecordCount - 1
	              For col = 0 To rs.Fields.Count - 1
	                 SomeArray(row, col) = rs.Fields(col).Value
	                 ' Excel will be offended if you try setting one
	                 ' of its cells to a NULL
	                 If IsNull(SomeArray(row, col)) Then _
	                   SomeArray(row, col) = ""
	              Next
	              rs.MoveNext
	           Next
	
	           ' The range should have the same number of
	           ' rows and cols as in the recordset
	           ws.Range(ws.Cells(StartingCell.row, StartingCell.col), _
	             ws.Cells(StartingCell.row + rs.RecordCount - 1, _
	             StartingCell.col + rs.Fields.Count - 1)).Value = SomeArray
	        End Sub
	
	        Private Sub Command1_Click()
	           Dim stcell As ExlCell
	           Dim objExlApp As Object
	
	           ' Get an Excel app object reference
	           On Error Resume Next
	           Set objExlApp = GetObject(, "Excel.Application")
	           ' If Excel is not launched start it
	           If Err = 429 Then
	              Err = 0
	              Set objExlApp = CreateObject("Excel.Application")
	              ' Can't create object
	              If Err = 429 Then
	                 MsgBox Err & ": " & Error
	                 Exit Sub
	              End If
	           End If
	           On Error GoTo 0
	
	           ' Add a new Workbook
	           objExlApp.Workbooks.Add
	
	           ' Select the first sheet
	           objExlApp.Worksheets("sheet1").Select
	
	           ' Start fill range at A1
	           stcell.row = 1
	           stcell.col = 1
	
	           ' Call CopyRecords procedure to populate sheet with array
	           CopyRecords Data1.Recordset, objExlApp.ActiveSheet, stcell
	
	           ' Show Excel and kill reference
	           objExlApp.Visible = True
	           objExlApp.Interactive = True
	           Set objExlApp = Nothing
	        End Sub
	
	5. Start the project and click the command button. Excel should start (if it is
	  not already started) and fill the first sheet of a new workbook with the rows
	  from the Authors table in the biblio.mdb database.
	
	MORE INFORMATION
	================
	
	When you program in Excel using VBA, the most efficient way to fill a sheet's
	range from a Recordset is by using the CopyFromRecordset method. However, when
	you try to call the CopyFromRecordset method using Automation from Visual Basic
	4.0, it fails with a run-time error. A workaround would seem to pass the
	Recordset object to a procedure in Excel to allow the Excel procedure to issue
	the CopyFromRecordset method. However, when you try to pass the Recordset object
	to the Excel procedure, it also fails with a run-time error.
	
	These limitations do not apply when you use Automation between Visual Basic 5.0
	or later and Microsoft Excel 97.
	
	Additional query words: Excel kbVBp
	
	======================================================================
	Keywords          : kbinterop kbAutomation kbVBp400 kbVBp500 kbVBp600 kbGrpDSVB kbExcel97 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbVB400Search kbVB400 kbVB16bitSearch
	Version           : WINDOWS:4.0,5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	