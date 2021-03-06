---
layout: page
title: "Q296784: SMS: Collid.lkp File Is Corrupted on Secondary Sites"
permalink: /kb/296/Q296784/
---

## Q296784: SMS: Collid.lkp File Is Corrupted on Secondary Sites

{% raw %}

	Article: Q296784
	Product(s): Microsoft Systems Management Server
	Version(s): 2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Operating System(s): 
	Keyword(s): kbsms200 kbsms200bug kbCollections kbSoftwareDist kbsms200preSP4fix
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Systems Management Server versions 2.0, 2.0 SP1, 2.0 SP2, 2.0 SP3 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	On secondary site servers, the Collid.lkp file in the SMS\Inboxes\Colleval.box
	folder may become corrupted. The Collection Evaluator component may report
	errors when the Collection Evaluator component attempts to update collections.
	
	The following error message may be logged in the Colleval.log file:
	
	  Cannot allocate collection ID for site ID <collection_ID>
	  Could not load collection definition from parent site. Will retry later.
	
	After the corruption to the Collid.lkp file occurs, the Offer Manager component
	may also log the following error message in the Offermgr.Log file:
	
	  Cannot find collection <collection_ID> in the collection source, skip
	  it.
	
	As a result of this condition, Offer Manager does not make advertisements
	available to clients of the secondary site.
	
	In some cases, the Collection Evaluator can recover from the problem and rebuild
	the Collid.lkp file. However, at times you may need to delete the corrupted
	Collid.lkp file for the Collection Evaluator to rebuild the Collid.lkp.
	
	CAUSE
	=====
	
	This problem can occur if both the Collection Evaluator and Offer Manager at the
	secondary site are attempting to manipulate the Collid.lkp file simultaneously.
	When the Collid.lkp file is updated, a temporary file called Collid.tmp file is
	created. The corruption occurs when the Collid.tmp file is deleted by one
	component when the Collid.tmp file is in use by the other component.
	
	RESOLUTION
	==========
	
	To resolve this problem, obtain the latest service pack for Systems Management
	Server version 2.0. For additional information, click the following article
	number to view the article in the Microsoft Knowledge Base:
	
	  Q288239 SMS: How to Obtain the Latest Systems Management Server 2.0 Service
	  Pack
	
	
	
	STATUS
	======
	
	Microsoft has confirmed that this is a problem in the Microsoft products that
	are listed at the beginning of this article. This problem was first corrected in
	Systems Management Server 2.0 Service Pack 4.
	
	MORE INFORMATION
	================
	
	This problem generally occurs on servers that are processing a large number of
	collections and servers that are operating in a stressed condition, where
	excessive disk paging can slow file input/output (I/O) operations.
	
	
	Additional query words: prodsms
	
	======================================================================
	Keywords          : kbsms200 kbsms200bug kbCollections kbSoftwareDist kbsms200preSP4fix 
	Technology        : kbSMSSearch kbSMS200 kbSMS200SP1 kbSMS200SP2 kbSMS200SP3
	Version           : :2.0,2.0 SP1,2.0 SP2,2.0 SP3
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
