---
layout: page
title: "Q246068: Listing the Default IIS MIME Map Settings Using WSH"
permalink: /kb/246/Q246068/
---

## Q246068: Listing the Default IIS MIME Map Settings Using WSH

{% raw %}

	Article: Q246068
	Product(s): Internet Information Server
	Version(s): winnt:5.0
	Operating System(s): 
	Keyword(s): kbOSWin2000
	Last Modified: 13-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Services version 5.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article describes how to create a Windows Scripting Host (WSH) script to
	list the default Multipurpose Internet Mail Extensions (MIME) Map settings for a
	server running Microsoft Internet Information Services (IIS).
	
	MORE INFORMATION
	================
	
	Multipurpose Internet Mail Extensions (MIME) is a way of configuring browsers or
	mail clients to view files that are in multiple formats based on a MIME Type.
	MIME Mapping is a process by which IIS maps files by their extensions to a
	particular MIME Type. For example, a file with a .htm extension has a MIME Type
	of "text/html," whereas a file with a .gif extension has a MIME Type of
	"image/gif."
	
	When a request is made by a client for a particular file, IIS uses the MIME Map
	to determine the correct MIME Type that the client will be receiving. IIS
	contains a large list of default MIME Types to use, and returns a MIME type of
	"application/octet-stream" for any file extension that is not explicitly
	mapped.
	
	When Web administrators create or store new file formats with extensions that may
	be undefined, the following WSH code may help determine the contents of the
	default MIME Types list by displaying a sorted list of all current MIME Type
	definitions.
	
	Listing the Default MIME Map:
	
	Copy the following WSH code and save it as Mimemaps.vbs:
	
	  Option Explicit
	
	  Dim objMimeMap
	  Dim varMimeMap
	  Dim intMimeMap
	  Dim objDictionary
	  Dim intCount
	  Const dictKey  = 1
	  Const dictItem = 2
	
	  Set objDictionary = CreateObject("Scripting.Dictionary")
	  Set objMimeMap = GetObject("IIS://localhost/mimemap")
	  varMimeMap = objMimeMap.Get("MimeMap")
	
	  If IsArray(varMimeMap) Then
	    For intCount = LBound(varMimeMap) To UBound(varMimeMap)
	      objDictionary.Add varMimeMap(intCount).Extension, varMimeMap(intCount).MimeType
	    Next
	    SortDictionary objDictionary,dictKey
	    intMimeMap = objDictionary.Count
	    WScript.Echo "Total MIME Map Entries: " & intMimeMap & vbCrLf
	    WScript.Echo "Extension" & vbTab & "MIME Type"
	    For Each varMimeMap in objDictionary
	      WScript.Echo varMimeMap & vbTab & objDictionary(varMimeMap)
	    Next
	  End If
	
	  Function SortDictionary(objDict,intSort)
	    Dim strDict()
	    Dim objKey
	    Dim strKey,strItem
	    Dim X,Y,Z
	    Z = objDict.Count
	    If Z > 1 Then
	      ReDim strDict(Z,2)
	      X = 0
	      For Each objKey In objDict
	          strDict(X,dictKey)  = CStr(objKey)
	          strDict(X,dictItem) = CStr(objDict(objKey))
	          X = X + 1
	      Next
	      For X = 0 to (Z - 2)
	        For Y = X to (Z - 1)
	          If StrComp(strDict(X,intSort),strDict(Y,intSort),vbTextCompare) > 0 Then
	              strKey  = strDict(X,dictKey)
	              strItem = strDict(X,dictItem)
	              strDict(X,dictKey)  = strDict(Y,dictKey)
	              strDict(X,dictItem) = strDict(Y,dictItem)
	              strDict(Y,dictKey)  = strKey
	              strDict(Y,dictItem) = strItem
	          End If
	        Next
	      Next
	      objDict.RemoveAll
	      For X = 0 to (Z - 1)
	        objDict.Add strDict(X,dictKey), strDict(X,dictItem)
	      Next
	    End If
	  End Function
	
	Run the WSH script from a command prompt using the following syntax:
	
	  
	  C:\>CSCRIPT.EXE C:\MIMEMAPS.VBS | MORE
	
	The output should be similar to the following:
	
	  Microsoft (R) Windows Script Host Version 5.1 for Windows
	  Copyright (C) Microsoft Corporation 1996-1999. All rights reserved.
	
	  Total MIME Map Entries: 189
	
	  Extension       MIME Type
	  .*      application/octet-stream
	  .323    text/h323
	  .acx    application/internet-property-stream
	  .ai     application/postscript
	  .aif    audio/x-aiff
	  .aifc   audio/aiff
	  .aiff   audio/aiff
	  .asf    video/x-ms-asf
	  .asr    video/x-ms-asf
	  .asx    video/x-ms-asf
	  .au     audio/basic
	  -- More  --
	
	Microsoft provides programming examples for illustration only, without warranty
	either expressed or implied, including, but not limited to, the implied
	warranties of merchantability and/or fitness for a particular purpose. This
	article assumes that you are familiar with the programming language being
	demonstrated and the tools used to create and debug procedures. Microsoft
	support professionals can help explain the functionality of a particular
	procedure, but they will not modify these examples to provide added
	functionality or construct procedures to meet your specific needs. If you have
	limited programming experience, you may want to contact a Microsoft Certified
	Partner or the Microsoft fee-based consulting line at (800) 936-5200. For more
	information about Microsoft Certified Partners, please visit the following
	Microsoft Web site:
	
	  http://www.microsoft.com/partner/referral/
	
	For more information about the support options that are available and about how
	to contact Microsoft, visit the following Microsoft Web site:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	REFERENCES
	==========
	
	For more information on Microsoft's scripting technologies, see the Microsoft
	Developer Network web site at the following URL:
	
	  http://msdn.microsoft.com/scripting/
	
	Additional query words: iis
	
	======================================================================
	Keywords          : kbOSWin2000 
	Technology        : kbiisSearch kbiis500
	Version           : winnt:5.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
