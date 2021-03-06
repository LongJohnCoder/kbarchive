---
layout: page
title: "Q272024: BUG: Release Calls When Using _ATL_DEBUG_INTEFACES May Crash"
permalink: /kb/272/Q272024/
---

## Q272024: BUG: Release Calls When Using _ATL_DEBUG_INTEFACES May Crash

{% raw %}

	Article: Q272024
	Product(s): Microsoft C Compiler
	Version(s): WINDOWS:3.0
	Operating System(s): 
	Keyword(s): kbATL kbVC600 kbVC600bug kbATL300 kbATL300bug
	Last Modified: 28-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- The Microsoft Active Template Library (ATL) 3.0, included with:
	   - Microsoft Visual C++, 32-bit Enterprise Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Professional Edition, version 6.0 
	   - Microsoft Visual C++, 32-bit Learning Edition, version 6.0 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	Release calls that are made with _ATL_DEBUG_INTERFACES or _ATL_DEBUG_REFCOUNT
	defined are not thread-safe. The most common symptom is an access violation (AV)
	under the stress of multiple threads (even if they are all STA). The crash may
	not occur near any ATL code.
	
	In addition, _QIThunk::Release may access member variables after the object has
	been deleted regardless of your threading model. This can lead to unpredictable
	behavior, including an access violation. Typically, a crash related to this
	occurs inside _QIThunk::Release.
	
	If you experience crashing with _ATL_DEBUG_INTERFACES defined but do not
	experience the crashing without it defined, then the crashing behavior may be
	caused by one of several ATL 3.0 bugs in the _QIThunk releasing mechanism.
	
	CAUSE
	=====
	
	There are two functions that contribute to the thread safety problems:
	ATL::CComModule::DeleteNonAddRefThunk and ATL::_QIThunk::Release.
	
	The purpose of the DeleteNonAddRefThunk function is to iterate through the array
	of interface thunks and delete all thunks that cannot be AddRef'ed. However,
	DeleteNonAddRefThunk does not check whether a thunk is marked as not AddRef'able
	before deleting it.
	
	The Release method's problems stem from two sources:
	
	- Release accesses _QIThunk object members after a call to
	  InterlockedDecrement. In a multithreaded scenario, another thread could
	  decrement the count after the call to InterlockedDecrement and delete the
	  _QIThunk object. This might cause an access violation if the first thread
	  accesses any class members.
	
	- Release should delete the thunk before allowing the underlying object the
	  chance to be deleted, because once the underlying object is deleted, another
	  thread can allocate another object and get the same address. The AddThunk
	  function can then find the existing thunk (that is about to be deleted) and
	  return it, instead of creating a new thunk.
	
	RESOLUTION
	==========
	
	Replace ATL::CComModule::DeleteNonAddRefThunk and ATL::_QIThunk::Release in
	Atlbase.h with the following:
	
	  void DeleteNonAddRefThunk(IUnknown* pUnk)
	  {
	      EnterCriticalSection(&m_csObjMap);
	      for (int i = 0; i < m_paThunks->GetSize(); i++)
	      {
	          if (m_paThunks->operator[](i)->pUnk == pUnk 
	              && m_paThunks->operator[](i)->bNonAddRefThunk
	              )
	          {
	              delete m_paThunks->operator[](i);
	              m_paThunks->RemoveAt(i);
	              break;
	          }
	      }
	      LeaveCriticalSection(&m_csObjMap);
	  }
	
	  inline ULONG _QIThunk::Release()
	  {
	      if (bBreak)
	          DebugBreak();
	      ATLASSERT(m_dwRef > 0);
	      IUnknown *r_pUnk           = pUnk;
	      bool     r_bNonAddRefThunk = bNonAddRefThunk;
	      LPCTSTR  r_lpszClassName   = lpszClassName;
	      IID      r_iid             = iid;
	      ULONG    r_dwRef           = InterlockedDecrement(&m_dwRef);
	      ATLTRACE(_T("%d< "), r_dwRef);
	      AtlDumpIID(r_iid, r_lpszClassName, S_OK);
	      if (r_dwRef==0 && !r_bNonAddRefThunk)
	          _pModule->DeleteThunk(this);
	      r_pUnk->Release();
	      return r_dwRef;
	  }
	
	STATUS
	======
	
	Microsoft has confirmed this to be a bug in the Microsoft products listed at the
	beginning of this article.
	
	MORE INFORMATION
	================
	
	The _ATL_DEBUG_INTERFACES mechanism can assist you in troubleshooting reference
	counting and QueryInterface-related problems in your code.
	
	The _ATL_DEBUG_INTERFACES mechanism does this by returning an object of type
	ATL::_QIThunk in place of any interface you request. This object tracks
	reference counting for each interface. It does this by intercepting all method
	calls.
	
	For any method calls but IUnknown method calls, the _QIThunk object adds no
	functionality. For the IUnknown method calls, the _QIThunk object does the
	appropriate tracking before passing the call on to the real object.
	
	ATL::_QIThunk::Release must manage the lifetime of the _QIThunk object as well as
	allow the underlying object to manage its lifetime.
	
	Most of the _QIThunk lifetime-management-related code is enclosed in a critical
	section. This is not possible in _QIThunk::Release because of the call to the
	Release method in the underlying object.
	
	The Release method in the underlying object could wait for a second thread to
	terminate. If the second thread also requires a Release call or a QueryInterface
	call through _QIThunk, a deadlock would result.
	
	This justifies the need to use InterlockedDecrement instead of a critical
	section, and also adds a level of complexity to designing a thread-safe
	function.
	
	Additional query words: AV 0xC0000005
	
	======================================================================
	Keywords          : kbATL kbVC600 kbVC600bug kbATL300 kbATL300bug 
	Technology        : kbVCsearch kbAudDeveloper kbATLsearch
	Version           : WINDOWS:3.0
	Issue type        : kbbug
	Solution Type     : kbpending
	
	=============================================================================
	

{% endraw %}
