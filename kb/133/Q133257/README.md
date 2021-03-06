---
layout: page
title: "Q133257: FIX: Invalid String Displayed by CToolTipCtrl"
permalink: /kb/133/Q133257/
---

## Q133257: FIX: Invalid String Displayed by CToolTipCtrl

{% raw %}

	Article: Q133257
	Product(s): Microsoft C Compiler
	Version(s): winnt:2.1,2.2
	Operating System(s): 
	Keyword(s): kbcode kbMFC kbToolTip KbUIDesign kbVC210bug kbVC220bug kbVC400fix kbGrpDSMFCATL
	Last Modified: 30-JUL-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Foundation Classes (MFC), used with:
	   - Microsoft Visual C++, 32-bit Editions, versions 2.1, 2.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	A tooltip created with a CToolTipCtrl object displays an incorrect string (or
	"garbage" string). This can happen under the following circumstances:
	
	- A temporary string buffer is passed to AddTool or SetToolInfo.
	
	-or-
	
	- The overloaded version of AddTool, which takes a resource ID as an argument,
	  is used.
	
	CAUSE
	=====
	
	The ToolTip common control stores string information about the tooltips it is
	going to display. When you specify the string to use for a tooltip, you pass a
	pointer to the buffer, which contains this string.
	
	Unlike a list or combo box, a ToolTip control stores the pointer to the string
	buffer instead of copying the string to its own local memory area. Therefore,
	the string buffer passed in must be maintained as long as the tooltip exists.
	
	For example, the following code sequence will not work correctly:
	
	     int CMyWnd::OnCreate()
	     {
	       ...
	       CString str("Helpful Info");
	       m_ToolTip.Create(this);
	       m_ToolTip.AddTool(this,str);
	       ...
	     }
	
	The CString object used in the call to AddTool is temporary. As soon as the
	function exits, the string buffer is freed and the tooltip is pointing to an
	invalid address. The overloaded version of CToolTip::AddTool, which takes a
	resource ID as an argument, has this problem. This is easy to see in the
	implementation of the function:
	
	  BOOL CToolTipCtrl::AddTool(CWnd* pWnd, UINT nIDText,
	                             LPCRECT lpRectTool, UINT nIDTool)
	  {
	    ASSERT(nIDText != 0);
	    CString str;
	    VERIFY(str.LoadString(nIDText));
	    return AddTool(pWnd, str, lpRectTool, nIDTool);
	  }
	
	RESOLUTION
	==========
	
	You can either use hard-coded strings that will never be de-allocated or you
	must store the string data for later use. One possible approach to doing this is
	to create your own CToolTipCtrl-derived class, and store the strings in it. You
	can add a OnAddTool handler for the TTM_ADDTOOL message for this class. In the
	OnAddTool handler, allocate space for the string. Then retrieve the permanent
	address of the stored string, and pass that in the TOOLINFO structure to the
	default Window procedure.
	
	An example of such a CToolTipCtrl-derived class is included in the "Sample Code"
	section of this article.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article. This bug was corrected in Microsoft Visual C++,
	32-bit edition, version 4.0.
	
	MORE INFORMATION
	================
	
	NOTE: This problem may not show up on Windows NT when using Visual C++ version
	2.1 or 2.2 because even though the string is passed in as ANSI, Windows NT
	converts it to UNICODE by thunking it and has to hang on to it. However, if the
	application is compiled using UNICODE, the problem will appear on Windows NT.
	
	Sample Code Showing Example Workaround
	--------------------------------------
	
	  // TTFIX.H
	  // 
	  // CFixToolTipCtrl
	  // 
	  //    CToolTipCtrl-derived class that duplicates the strings
	  //    passed in to AddTool and SetToolInfo so that they will be
	  //    properly stored until the tooltip is destroyed.
	  // 
	
	  class CFixToolTipCtrl : public CToolTipCtrl
	  {
	  protected:
	     CPtrList m_lstTips;
	  public:
	       CFixToolTipCtrl();
	       virtual ~CFixToolTipCtrl();
	
	     // Generated message map functions
	  protected:
	     //{{AFX_MSG(CFixToolTipCtrl)
	  // NOTE - the ClassWizard will add and remove member functions here.
	     //}}AFX_MSG
	        afx_msg LRESULT OnAddTool(WPARAM wParam, LPARAM lParam);
	     DECLARE_MESSAGE_MAP()
	  };
	  // END OF TTFIX.H
	  ///////////////////////////////////////////////////////////////////// 
	
	  //////////////////////////////////////////////////////////////////// 
	  // TTFIX.CPP
	  // 
	  #include "stdafx.h"
	  #include <afxcmn.h>
	  #include "ttfix.h"
	
	  BEGIN_MESSAGE_MAP(CFixToolTipCtrl, CToolTipCtrl)
	     //{{AFX_MSG_MAP(CFixToolTipCtrl)
	    // NOTE - the ClassWizard will add and remove mapping macros here.
	     //}}AFX_MSG_MAP
	       ON_MESSAGE(TTM_ADDTOOL, OnAddTool)
	  END_MESSAGE_MAP()
	
	  CFixToolTipCtrl::~CFixToolTipCtrl()
	  {
	      while (!m_lstTips.IsEmpty())
	         free(m_lstTips.RemoveHead());
	  }
	
	  LRESULT CFixToolTipCtrl::OnAddTool(WPARAM wParam, LPARAM lParam)
	  {
	        TOOLINFO ti = *(LPTOOLINFO)lParam;
	        if ((ti.hinst == NULL) && (ti.lpszText != LPSTR_TEXTCALLBACK)
	              && (ti.lpszText != NULL))
	        {
	              char *pStr = _tcsdup(ti.lpszText);
	              m_lstTips.AddTail(pStr);
	              ti.lpszText = pStr;
	        }
	        return DefWindowProc(TTM_ADDTOOL, wParam, (LPARAM)&ti);
	  }
	
	  // END OF TTFIX.CPP
	
	Additional query words: 2.10 2.20 3.1 3.10 3.2 3.20 Incorrect Corrupted
	
	======================================================================
	Keywords          : kbcode kbMFC kbToolTip KbUIDesign kbVC210bug kbVC220bug kbVC400fix kbGrpDSMFCATL 
	Technology        : kbAudDeveloper kbMFC
	Version           : winnt:2.1,2.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
