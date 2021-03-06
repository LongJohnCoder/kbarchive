---
layout: page
title: "Q181609: NoClick.exe Illustrates Click Method of StatusBar OCX"
permalink: /kb/181/Q181609/
---

## Q181609: NoClick.exe Illustrates Click Method of StatusBar OCX

{% raw %}

	Article: Q181609
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:5.0,5.0a
	Operating System(s): 
	Keyword(s): kbfile kbinterop kbOOP kbvfp500 kbDSupport
	Last Modified: 11-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 5.0, 5.0a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The NoClick.exe file contains sample forms that can be used to illustrate when
	the Click method of the Microsoft StatusBar ActiveX control becomes disabled. To
	use the file, place it in a new or existing folder and extract the sample forms.
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This problem was corrected Visual FoxPro 6.0 for
	Windows.
	
	MORE INFORMATION
	================
	
	The following files are available for download from the Microsoft Download
	Center:
	
	  Noclick.exe
	  (http://download.microsoft.com/download/vfox50/sample6/1/W9X/EN-US/Noclick.exe)
	
	For additional information about how to download Microsoft Support files, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q119591 How to Obtain Microsoft Support Files from Online Services
	
	Microsoft used the most current virus detection software available on the date of
	posting to scan this file for viruses. Once posted, the file is housed on secure
	servers that prevent any unauthorized changes to the file.
	
	The Click method of the Microsoft Status Bar ActiveX control can become disabled
	if a non-modal form is displayed in the form that the Status Bar control is on
	and then this non-modal form displays a modal form. Once the modal form is
	closed, the Click method of the Status Bar control will not fire.
	
	Steps to Reproduce Behavior
	---------------------------
	
	NOTE: The following steps assume that the Microsoft Status Bar control, version
	5.0 is installed properly on the computer.
	
	1. Extract the contents of the downloaded file.
	
	2. Run the NoClick.scx form.
	
	3. Follow the instructions on the forms in the sample.
	
	4. Note that after the button on the non-modal form is used to display the modal
	  form and the modal form is closed, the Click method of the StatusBar ActiveX
	  control no longer fires.
	
	Additional query words: Noclick
	
	======================================================================
	Keywords          : kbfile kbinterop kbOOP kbvfp500 kbDSupport 
	Technology        : kbVFPsearch kbAudDeveloper kbVFP500 kbVFP500a
	Version           : WINDOWS:5.0,5.0a
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
