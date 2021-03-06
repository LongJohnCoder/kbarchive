---
layout: page
title: "Q174646: SNA Server Access Violation in snaservr!s1pufnty()"
permalink: /kb/174/Q174646/
---

## Q174646: SNA Server Access Violation in snaservr!s1pufnty()

{% raw %}

	Article: Q174646
	Product(s): Microsoft SNA Server
	Version(s): WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1
	Operating System(s): 
	Keyword(s): 
	Last Modified: 13-JUN-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft SNA Server, versions 2.11, 2.11 SP1, 2.11 SP2, 3.0, 3.0 SP1, on platform(s):
	   - the operating system: Microsoft Windows NT 
	-------------------------------------------------------------------------------
	
	
	SYMPTOMS
	========
	
	The SNA Server service (snaservr.exe) may fail with an access violation while
	supporting Attachmate Extra! 3270 client sessions. The failure may be recorded
	in the <ntroot>\DRWTSN32.LOG file as follows:
	
	  Application exception occurred:
	       App: snaservr.DBG (pid=<number>)
	       Exception number: c0000005 (access violation)
	
	  [...]
	
	State Dump for Thread Id 0xf1
	
	eax=00000000 ebx=00000001 ecx=011b0000 edx=00cc46bc esi=011bf900 edi=0041617c
	eip=003983b9 esp=002cff10 ebp=00000000 iopl=0         nv up ei pl nz na pe nc
	cs=001b  ss=0023  ds=0023  es=0023  fs=0038  gs=0000             efl=00000202
	
	function: s1pufnty
	       00398391 0fbfc1           movsx   eax,cx
	       00398394 8b04857c614100                                  ds:00000000=????????
	                                 mov     eax,[s1mode+0x380c (0041617c)+eax*4]
	       0039839b 6683781806       cmp     word ptr [eax+0x18],0x6    ds:0087e923=????
	       003983a0 7404             jz      s1pufnty+0x36 (003983a6)
	       003983a2 668b480c         mov     cx,[eax+0xc]               ds:0087e923=????
	       003983a6 0fbfc1           movsx   eax,cx
	       003983a9 8b542408         mov     edx,[esp+0x8]          ss:00b4e833=????????
	       003983ad 8d3c857c614100                                  ds:00000000=????????
	                                 lea     edi,[s1mode+0x380c (0041617c)+eax*4]
	       003983b4 8b7204           mov     esi,[edx+0x4]          ds:01542fde=????????
	       003983b7 8b07             mov     eax,[edi]              ds:0041617c=00000000
	FAULT ->003983b9 80782c04         cmp     byte ptr [eax+0x2c],0x4      ds:0087e922=??
	
	*----> Stack Back Trace <----*
	
	FramePtr ReturnAd Param#1  Param#2  Param#3  Param#4  Function Name
	00000000 00000000 00000000 00000000 00000000 00000000 snaservr!s1pufnty  
	0000000c 00000000 00000000 00000000 00000000 00000000 snaservr!<nosymbols>
	
	CAUSE
	=====
	
	The access violation was caused by a 3270 client emulator sending a Close(SSCP)
	message to the SNA Server which contained an incorrect "destination index"
	(desti) value. The Close(SSCP) message is documented in the SNA Server Emulator
	Interface Specification (EIS) included with SNA Server. The SNA Server EIS
	interface is used by Attachmate Extra! The customer who reported this issue was
	using various versions of the Attachmate Extra! 3270 emulator. The client
	emulator reproduction scenario leading to this problem is not known.
	
	RESOLUTION
	==========
	
	An update to the SNA Server service is available which performs additional
	validation checking on Close(SSCP) requests to prevent this access violation. If
	SNA Server detects that an emulator sent an invalid request, the server will now
	drop the message, disconnect the client connection, and log the following
	event:
	
	  Event ID: 9
	  Source: SNA Server
	  Description: (1117) Internal message sequence error
	  X'1117' Received an invalid message from a 3270 emulator
	
	NOTE: Event 9 may also indicate a minor error not indicative of this problem or
	even a session loss. This event will be enhanced in a future version of SNA
	Server to indicate additional details of this error including the client machine
	which caused the event to occur.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in SNA Server versions 2.1, 2.11,
	2.11 SP1, 2.11 SP2, 3.0, and 3.0 SP1.
	
	A supported fix for SNA Server version 2.11 is now available, but has not been
	fully regression-tested and should be applied only to systems experiencing this
	specific problem. Unless you are severely impacted by this specific problem,
	Microsoft recommends that you wait for the next Service Pack that contains this
	fix. Contact Microsoft Product Support Services for more information.
	
	This problem was corrected in SNA Server version 3.0 Service Pack 2. For
	information on obtaining the Service Pack, query on the following word in the
	Microsoft Knowledge Base (without the spaces):
	
	  S E R V P A C K
	
	Additional query words: trap
	
	======================================================================
	Keywords          :  
	Technology        : kbAudDeveloper kbSNAServSearch
	Version           : WINDOWS:2.11,2.11 SP1,2.11 SP2,3.0,3.0 SP1
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
