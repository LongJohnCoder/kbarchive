---
layout: page
title: "Q60607: On New Build with No Changes, QC Environment Changes Size"
permalink: /kb/060/Q60607/
---

## Q60607: On New Build with No Changes, QC Environment Changes Size

{% raw %}

	Article: Q60607
	Product(s): See article
	Version(s): 2.00
	Operating System(s): MS-DOS
	Keyword(s): ENDUSER | s_quickasm | mspl13_c
	Last Modified: 17-JUL-1990
	
	The QuickC Version 2.00 environment may sporadically change its size
	in memory if you make no changes to your source code and recompile or
	rebuild the program.
	
	If you choose the DOS Shell command from the File menu and then run
	CHKDSK, the last line of information returned tells you the amount of
	free memory available to DOS on your system. If you check this amount,
	exit back into QuickC, select Rebuild All from the Make menu, and
	repeat the memory check, you may find that your free memory size has
	changed.
	
	This problem seems to appear sporadically and without a pattern. The
	memory in use may shrink to a very small amount, or it may return to
	the original value. It never seems to grow past the original amount.
	Microsoft is researching this problem and will post new information
	here as it becomes available.

{% endraw %}
