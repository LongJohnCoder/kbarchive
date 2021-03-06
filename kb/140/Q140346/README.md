---
layout: page
title: "Q140346: Possible Reasons for OLE Control Registration Failure"
permalink: /kb/140/Q140346/
---

## Q140346: Possible Reasons for OLE Control Registration Failure

{% raw %}

	Article: Q140346
	Product(s): Microsoft C Compiler
	Version(s): 1.51 1.52 | 2.00 2.10 2.20 4.00
	Operating System(s): 
	Keyword(s): kbcode kbole kbCtrl
	Last Modified: 07-SEP-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual C++, versions 1.5, 1.51, 1.52, 2.0, 2.1, 2.2, 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	OLE controls can be registered by using Visual C++ from the Tools menu, from the
	Test Container provided with the Control Development Kit (CDK), or by using the
	regsvr or regsvr32 applications provided with Visual C++. In some cases, the
	registration of a control may fail; use this article to help troubleshoot the
	problem.
	
	MORE INFORMATION
	================
	
	All of the previously mentioned methods for registering an OLE Control use
	essentially the same technique. LoadLibrary() is called to load the control into
	memory, GetProcAddress() is called to get the address of the DllRegisterServer()
	function, and then DllRegisterServer() is called to register the control.
	
	Reasons Why the Registration of a Control May Fail
	--------------------------------------------------
	
	- One or more of the necessary OLE DLLs is not in the path. Instructions for
	  distributing OLE Controls as well as an explanation of what DLLs are
	  necessary to ship can be found in the Shipctrl.wri file located in the same
	  directory as the CDK.
	
	- The control is loading a DLL other than the OLE DLL, and that DLL is not in
	  the path. When the control is loaded into memory, any DLLs that are
	  implicitly loaded through an import library are also loaded. If any of these
	  DLLs are not in the path, the control is not loaded successfully, so
	  registration fails.
	
	- One or more DLLs may be the wrong version. If the control was built with a
	  newer version of a DLL than the one installed on the computer, the control
	  may not load properly, so registration fails.
	
	- An old version of Ocd25.lib is being linked to. If the control is using the
	  MFC database classes, there may be a problem with the version of the
	  Ocd25.lib file that is being linked to.
	
	- The OLE control is located on a Novell server's remote drive. In this case,
	  the access rights to the .ocx file may be preventing the control from
	  loading. Make sure that the access rights for the .ocx file are set to
	  read-only, shareable access, which is the typical setting for executable
	  files.
	
	Troubleshooting Techniques
	--------------------------
	
	If none of the possible causes are true in your case, try the following
	techniques.
	
	1. With the control project loaded in Visual C++, set the executable for the
	  debug session to the OLE Control Test Container (Tstcon16.exe or
	  Tstcon32.exe). When you start the Test Container (under the debugger), you
	  will get a warning that the Test Container does not contain debug
	  information. Ignore this and proceed.
	
	2. From the Test Container, attempt to register the control. Watch for debug
	  output from the OLE Control DLL or any of its dependent DLLs. If you are
	  running the 16-bit product, remember to run the DBWIN program to receive
	  debug output.
	
	  For information on how to set the executable for a DLL debug session, please
	  see the help topic "Debugging DLLs" in Books Online.
	
	As an alternative, you can attempt to register the control programmatically.
	First create an MFC AppWizard application selecting Dialog-based application and
	OLE Automation. Enabling OLE Automation will initialize OLE so that the code to
	register the control will work properly. In the CWinApp-derived class, you will
	find the function InitInstance() with the initial code as follows:
	
	  BOOL CTestregApp::InitInstance()
	  {
	
	     // Initialize OLE libraries
	     if (!AfxOleInit())
	     {
	        AfxMessageBox(IDP_OLE_INIT_FAILED);
	        return FALSE;
	     }
	
	At this point, add the following code segment, which will allow you to check the
	return codes from LoadLibrary(), GetProcAddress(), and DllRegisterServer.
	
	  #ifdef _WIN32
	      HINSTANCE hDLL = LoadLibrary("some.ocx");
	      if(NULL == hDLL)
	      {
	          // See Winerror.h for explaination of error code.
	          DWORD error = GetLastError();
	          TRACE1("LoadLibrary() Failed with: %i\n", error);
	          return FALSE;
	      }
	
	      typedef HRESULT (CALLBACK *HCRET)(void);
	      HCRET lpfnDllRegisterServer;
	
	      lpfnDllRegisterServer =
	              (HCRET)GetProcAddress(hDLL, "DllRegisterServer");
	      if(NULL == lpfnDllRegisterServer)
	      {
	          // See Winerror.h for explaination of error code.
	          DWORD error = GetLastError();
	          TRACE1("GetProcAddress() Failed with %i\n", error);
	          return FALSE;
	      }
	
	      if(FAILED((*lpfnDllRegisterServer)()))
	      {
	          TRACE("DLLRegisterServer() Failed");
	          return FALSE;
	      }
	
	  #else // 16-bit
	      HINSTANCE hDLL = LoadLibrary("regtest.ocx");
	      if(HINSTANCE_ERROR > hDLL)
	      {
	          // See LoadLibrary() help for explaination of error code.
	          TRACE1("LoadLibrary() Failed with: %i\n", hDLL);
	          return FALSE;
	      }
	
	      typedef HRESULT (CALLBACK *HCRET)(void);
	      HCRET lpfnDllRegisterServer;
	
	      lpfnDllRegisterServer =
	              (HCRET)GetProcAddress(hDLL, "DllRegisterServer");
	      if(NULL == lpfnDllRegisterServer)
	      {
	          // See GetProcAddress() help for explaination of error code.
	          TRACE("GetProcAddress() Failed");
	          return FALSE;
	      }
	
	      if(FAILED((*lpfnDllRegisterServer)()))
	      {
	          TRACE("DLLRegisterServer() Failed");
	          return FALSE;
	      }
	  #endif
	
	Additional query words: kbinf 1.51 1.52 1.52b 2.00 2.10 2.20 2.50 2.51 2.52 3.00 3.10 3.20 4.00
	
	======================================================================
	Keywords          : kbcode kbole kbCtrl 
	Technology        : kbVCsearch kbVC400 kbAudDeveloper kbvc150 kbVC220 kbVC151 kbVC200 kbVC210 kbVC152
	Version           : 1.51 1.52 | 2.00 2.10 2.20 4.00
	
	=============================================================================
	

{% endraw %}
