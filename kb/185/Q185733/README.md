---
layout: page
title: "Q185733: HOWTO: Limit a Window's Minimum and Maximum Size"
permalink: /kb/185/Q185733/
---

## Q185733: HOWTO: Limit a Window's Minimum and Maximum Size

{% raw %}

	Article: Q185733
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 
	Operating System(s): 
	Keyword(s): kbGrpDSVB
	Last Modified: 11-JAN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Learning Edition for Windows, version 6.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Visual Basic Control Creation Edition for Windows, version 5.0 
	- Microsoft Visual Basic Learning Edition for Windows, version 5.0 
	- Microsoft Visual Basic Professional Edition for Windows, version 5.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	By default, Visual Basic allows a form to be resized to any size you want
	provided the BorderStyle is set appropriately. At times, it may be desirable or
	necessary to limit the range of a window's size (such that it cannot be smaller
	or larger than a predetermined size).
	
	For example, the Windows accessory, Microsoft Paint, prevents its window from
	being sized below a certain point. This is done to allow the user to always see
	at least part of the image they are editing.
	
	With the aid of Windows API functions, you can achieve this same functionality
	within your Visual Basic application.
	
	MORE INFORMATION
	================
	
	WARNING: ANY USE BY YOU OF THE SAMPLE CODE PROVIDED IN THIS ARTICLE IS AT YOUR
	OWN RISK. Microsoft provides this sample code "as is" without warranty of any
	kind, either express or implied, including but not limited to the implied
	warranties of merchantability and/or fitness for a particular purpose.
	
	Below are steps to create a sample application that demonstrate the behavior
	discussed above. To achieve this functionality, a concept known as subclassing
	must be used to detect when the WM_GETMINMAXINFO message occurs. This message
	occurs when an attempt is made to resize the window.
	
	For more information on subclassing, please see the following article in the
	Microsoft Knowledge Base:
	
	  Q168795 : HOWTO: Hook Into a Window's Messages Using AddressOf
	
	Failure to unhook a window before its destruction results in application errors,
	Invalid Page Faults, and data loss. This problem can occur when the new
	WindowProc function being pointed to no longer exists, but the window has not
	been notified of the change. Always unhook the subclassed window upon unloading
	the subclassed form or exiting the application. This is especially important
	while debugging an application that uses this technique within the Microsoft
	Visual Basic Development Environment. Clicking the End button or, on the Run
	menu, clicking End, without unhooking causes an Invalid Page Fault and closes
	Microsoft Visual Basic.
	
	Steps to Create a Sample Application
	------------------------------------
	
	1. Create a new Standard EXE project.
	
	2. Paste the following code into Form1's code module:
	
	        Option Explicit
	
	        Private Sub Form_Load()
	            'Save handle to the form.
	            gHW = Me.hwnd
	
	            'Begin subclassing.
	            Hook
	        End Sub
	
	        Private Sub Form_Unload(Cancel As Integer)
	            'Stop subclassing.
	            Unhook
	        End Sub
	
	3. Add a standard module to the project.
	
	4. Paste the following code into the module:
	
	        Option Explicit
	
	        Private Const GWL_WNDPROC = -4
	        Private Const WM_GETMINMAXINFO = &H24
	
	        Private Type POINTAPI
	            x As Long
	            y As Long
	        End Type
	
	        Private Type MINMAXINFO
	            ptReserved As POINTAPI
	            ptMaxSize As POINTAPI
	            ptMaxPosition As POINTAPI
	            ptMinTrackSize As POINTAPI
	            ptMaxTrackSize As POINTAPI
	        End Type
	
	        Global lpPrevWndProc As Long
	        Global gHW As Long
	
	        Private Declare Function DefWindowProc Lib "user32" Alias _
	           "DefWindowProcA" (ByVal hwnd As Long, ByVal wMsg As Long, _
	            ByVal wParam As Long, ByVal lParam As Long) As Long
	        Private Declare Function CallWindowProc Lib "user32" Alias _
	           "CallWindowProcA" (ByVal lpPrevWndFunc As Long, _
	            ByVal hwnd As Long, ByVal Msg As Long, _
	            ByVal wParam As Long, ByVal lParam As Long) As Long
	        Private Declare Function SetWindowLong Lib "user32" Alias _
	           "SetWindowLongA" (ByVal hwnd As Long, _
	            ByVal nIndex As Long, ByVal dwNewLong As Long) As Long
	        Private Declare Sub CopyMemoryToMinMaxInfo Lib "KERNEL32" Alias _
	           "RtlMoveMemory" (hpvDest As MINMAXINFO, ByVal hpvSource As Long, _
	            ByVal cbCopy As Long)
	        Private Declare Sub CopyMemoryFromMinMaxInfo Lib "KERNEL32" Alias _
	           "RtlMoveMemory" (ByVal hpvDest As Long, hpvSource As MINMAXINFO, _
	            ByVal cbCopy As Long)
	
	        Public Sub Hook()
	            'Start subclassing.
	            lpPrevWndProc = SetWindowLong(gHW, GWL_WNDPROC, _
	               AddressOf WindowProc)
	        End Sub
	
	        Public Sub Unhook()
	            Dim temp As Long
	
	            'Cease subclassing.
	            temp = SetWindowLong(gHW, GWL_WNDPROC, lpPrevWndProc)
	        End Sub
	
	        Function WindowProc(ByVal hw As Long, ByVal uMsg As Long, _
	           ByVal wParam As Long, ByVal lParam As Long) As Long
	            Dim MinMax As MINMAXINFO
	
	            'Check for request for min/max window sizes.
	            If uMsg = WM_GETMINMAXINFO Then
	                'Retrieve default MinMax settings
	                CopyMemoryToMinMaxInfo MinMax, lParam, Len(MinMax)
	
	                'Specify new minimum size for window.
	                MinMax.ptMinTrackSize.x = 200
	                MinMax.ptMinTrackSize.y = 200
	
	                'Specify new maximum size for window.
	                MinMax.ptMaxTrackSize.x = 500
	                MinMax.ptMaxTrackSize.y = 500
	
	                'Copy local structure back.
	                CopyMemoryFromMinMaxInfo lParam, MinMax, Len(MinMax)
	
	                WindowProc = DefWindowProc(hw, uMsg, wParam, lParam)
	            Else
	                WindowProc = CallWindowProc(lpPrevWndProc, hw, uMsg, _
	                   wParam, lParam)
	            End If
	        End Function
	
	5. Save and run the sample application.
	
	6. Attempt to resize Form1.
	
	  RESULT: The form is not allowed to be sized smaller than 200 by 200 pixels or
	  larger than 500 by 500 pixels.
	
	REFERENCES
	==========
	
	For additional information, please see the following article(s) in the Microsoft
	Knowledge Base:
	
	  Q168795 : HOWTO: Hook Into a Window's Messages Using AddressOf
	
	Additional query words: Min Max kbSDKWin32 kbAPI kbDSupport kbDSD sub-class sub 
	class kbVBp500 kbVBp600 kbdsd kbDSupport kbVBp
	
	======================================================================
	Keywords          : kbGrpDSVB 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB500Search kbVB600Search kbVBA500Search kbVBA500 kbVBA600 kbVB500 kbVB600 kbZNotKeyword3
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
