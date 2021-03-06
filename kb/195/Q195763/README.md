---
layout: page
title: "Q195763: HOWTO: Use GetTempFileName API to Create a Unique Temporary File"
permalink: /kb/195/Q195763/
---

## Q195763: HOWTO: Use GetTempFileName API to Create a Unique Temporary File

{% raw %}

	Article: Q195763
	Product(s): Microsoft Visual Basic for Windows
	Version(s): WINDOWS:5.0,6.0
	Operating System(s): 
	Keyword(s): kbcode kbAPI kbKernBase kbSDKWin32 kbVBp kbVBp500 kbVBp600 kbGrpDSVB kbCodeSam
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, versions 5.0, 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, versions 5.0, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	For Visual Basic programmers unfamiliar with the Win32 API, making a file name
	for a temporary file is often a matter of hard-coding some value and hoping that
	the name does not conflict with an existing file. Fortunately, there is a better
	way that requires very little code.
	
	This article demonstrates how to use the GetTempPath and GetTempFileName API
	functions to construct a unique temporary file name located in the default temp
	directory of an end user's system.
	
	MORE INFORMATION
	================
	
	GetTempPath
	-----------
	
	The GetTempPath API function allows you to determine the path location of a
	system's temporary folder. It takes two parameters: the length of a fixed-
	length or pre-initialized string that will contain the path name, and the string
	itself. You must use either a fixed-length string, or a string initialized to a
	length that you believe will be long enough to contain the path information.
	This is to guarantee that Visual Basic allocates enough buffer space for Windows
	to return the information.
	
	GetTempPath returns the length of the path name measured in bytes, or 0 if an
	error occurs. If the return value is greater than the buffer size you specified,
	then no path information was written to the string.
	
	The declaration for GetTempPath is provided in the sample below.
	
	GetTempFileName
	---------------
	
	The GetTempFileName API function is used to create a fully-qualified temporary
	file name at a given location. The function takes four parameters: the string
	containing the path for the file, a string containing a prefix used to start the
	unique file name, a unique number to construct the temp name, and, finally, a
	fixed-length or pre-initialized string used to return the fully qualified file
	name. Both the path and prefix strings are required and cannot be empty. The
	unique number can be 0 (NULL), in which case GetTempFileName creates a unique
	number based on the current system time.
	
	GetTempFileName returns the unique number used to create the file name, or
	returns 0 if an error occurs.
	
	The declaration for GetTempFileName is provided in the sample below.
	
	Step-by-Step Example
	--------------------
	
	1. Create a new Standard EXE project. Form1 is created by default.
	
	2. Add a CommandButton to Form1.
	
	3. Add the following code to the General Declarations section of Form1:
	
	         Option Explicit
	
	        Private Declare Function GetTempPath Lib "kernel32" _
	           Alias "GetTempPathA" (ByVal nBufferLength As Long, _
	           ByVal lpBuffer As String) As Long
	
	        Private Declare Function GetTempFileName Lib "kernel32" _
	           Alias "GetTempFileNameA" (ByVal lpszPath As String, _
	           ByVal lpPrefixString As String, ByVal wUnique As Long, _
	           ByVal lpTempFileName As String) As Long
	
	        Private Function CreateTempFile(sPrefix As String) As String
	           Dim sTmpPath As String * 512
	           Dim sTmpName As String * 576
	           Dim nRet As Long
	
	           nRet = GetTempPath(512, sTmpPath)
	           If (nRet > 0 And nRet < 512) Then
	              nRet = GetTempFileName(sTmpPath, sPrefix, 0, sTmpName)
	              If nRet <> 0 Then
	                 CreateTempFile = Left$(sTmpName, _
	                    InStr(sTmpName, vbNullChar) - 1)
	              End If
	           End If
	        End Function
	
	        Private Sub Command1_Click()
	           Dim sTmpFile As String
	           Dim sMsg As String
	           Dim hFile As Long
	
	           sTmpFile = CreateTempFile("VBT")
	           hFile = FreeFile
	
	           Open sTmpFile For Binary As hFile
	              Put #hFile, , "This is a test. 1234"
	           Close hFile
	
	           sMsg = "Temp FileName: " & sTmpFile & vbCrLf
	           sMsg = sMsg & "File Length: " & FileLen(sTmpFile) & vbCrLf
	           sMsg = sMsg & "Time Created: " & _
	              Format$(FileDateTime(sTmpFile), "long time") & vbCrLf
	
	           MsgBox sMsg, vbInformation, "TempFile"
	
	           Kill sTmpFile
	        End Sub
	
	4. Press the F5 key to run the project. When you click the CommandButton, a
	  temporary file is created. A message box displays information regarding the
	  temp file. The file is then destroyed using the Kill statement.
	
	REFERENCES
	==========
	
	For additional information, please see the following articles in the Microsoft
	Knowledge Base:
	
	  Q190000 : HOWTO: Get Started Programming With the Windows API (LONG)
	
	  Q137034 : PRB: Win32 GetTempFileName API Differs from 16-bit
	
	(c) Microsoft Corporation 1998, All Rights Reserved. Contributions by Richard R.
	Taylor, Microsoft Corporation.
	
	
	======================================================================
	Keywords          : kbcode kbAPI kbKernBase kbSDKWin32 kbVBp kbVBp500 kbVBp600 kbGrpDSVB kbCodeSam 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVB500 kbVB600
	Version           : WINDOWS:5.0,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
