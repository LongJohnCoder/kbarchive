---
layout: page
title: "Q190509: PRB: VC++ Does Not Convert Help Project File Paths"
permalink: /kb/190/Q190509/
---

## Q190509: PRB: VC++ Does Not Convert Help Project File Paths

{% raw %}

	Article: Q190509
	Product(s): Microsoft C Compiler
	Version(s): 5.0,6.0
	Operating System(s): 
	Keyword(s): kbwizard kbide kbVC500 kbVC600 kbFAQ kbGrpDSTools kbvc600faq
	Last Modified: 24-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, 32-bit Enterprise Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Professional Edition, versions 5.0, 6.0 
	- Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	After loading and converting a project created in a previous version of Visual
	C++, a build attempt fails while compiling a help project with this message:
	
	  error: Problem encountered creating help file
	
	On Windows NT and Windows 2000, the following error message will also appear :
	
	  Error executing c:\winnt\system32\cmd.exe.
	
	The error line indicates the first line of the project's .hpj file.
	
	This error may also occur after moving a project, while building it from a
	different workstation, or after reinstalling Visual C++ to a different path.
	
	CAUSE
	=====
	
	The project contains a hard-coded path within the help project (.hpj) file that
	is no longer valid in the current build environment.
	
	RESOLUTION
	==========
	
	You must modify the .hpj file to correct any file paths that are now invalid.
	You may also modify the custom build step to provide more informative error
	reporting.
	
	To modify the .hpj file:
	
	1. Open the .hpj file in Visual C++.
	
	2. Examine its [FILES] and [MAP] sections for hard-coded paths. Modify them as
	  necessary. Notice that the default installation path for Visual C++ 6.0 is as
	  follows: \Program Files\Microsoft Visual Studio\VC98 whereas the default path
	  for Visual C++ 5.0 is as follows: \Program Files\DevStudio\VC
	
	To upgrade the custom build step rule:
	
	1. Right-click the .hpj file in FileView; then click Settings on the Context
	  menu, and click the Custom Build tab in the Project Settings dialog box.
	
	2. Visual C++ 5.0 uses the following custom build step command to build help
	  files:
	
	        call "$(ProjDir)\makehelp.bat"
	
	  Modify this text in the Commands list box to the following, assuming
	  Makehelp.bat has not been changed from its original form:
	
	  start /wait hcw /C /E /M "hlp\$(InputName).hpj"
	  if errorlevel 1 goto :Error 
	  if not exist "hlp\$(InputName).hlp" goto :Error 
	  copy  "hlp\$(InputName).hlp" $(OutDir) 
	  goto :Done
	  :Error 
	  echo   hlp\$(InputName).hpj(1) : error: 
	  type "hlp\$(InputName).log" 
	  :Done
	
	  NOTE: The above steps are the default for a new project in Visual C++ 6.0.
	
	3. Delete Makehelp.bat from the project; it is normally in the Help Files
	  folder. If desired, you may also delete the Makehelp.bat file as well.
	
	STATUS
	======
	
	This behavior is by design.
	
	MORE INFORMATION
	================
	
	Visual C++ provides help project support with custom build rules, and does not
	recognize the help compiler (Hcw.exe) as a native tool. Consequently, during
	project conversions, Visual C++ does not modify paths embedded in a help project
	file, not even paths that reference standard MFC components.
	
	The uninformative error message is a consequence of executing Hcw.exe from a
	command line. HCW does not display error messages on the standard console, but
	writes them to a log file. See the RESOLUTION section for a method to display
	the log file after a failed HCW build.
	
	Steps to Reproduce Behavior
	---------------------------
	
	1. Using a default installation of Visual C++ 5.0, create a new MFC .EXE project
	  that includes context-sensitive help. In this example, the project is named
	  badhelp.
	
	2. Modify one of the <include ...> directives in the [MAP] section of
	  Badhelp.hpj to reference an invalid file path. In a default installation of
	  Visual C++ 6.0, open Badhelp.dsw. At the dialog box, click Yes to convert the
	  project.
	
	3. Build the project.
	
	RESULT:
	
	  hlp\badhelp.hpj(1) : error: Problem encountered creating help file
	
	Additional query words: kbvc600 kbvc500 kbWizard kbDSSTools
	
	======================================================================
	Keywords          : kbwizard kbide kbVC500 kbVC600 kbFAQ kbGrpDSTools kbvc600faq 
	Technology        : kbVCsearch kbAudDeveloper kbVC500 kbVC600 kbVC32bitSearch kbVC500Search
	Version           : :5.0,6.0
	Issue type        : kbprb
	
	=============================================================================
	

{% endraw %}
