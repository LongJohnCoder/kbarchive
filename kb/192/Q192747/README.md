---
layout: page
title: "Q192747: XFOR: Linkage SNADS Connector Does Not Handle NDR Properly"
permalink: /kb/192/Q192747/
---

## Q192747: XFOR: Linkage SNADS Connector Does Not Handle NDR Properly

{% raw %}

	Article: Q192747
	Product(s): Microsoft Exchange
	Version(s): 3.2
	Operating System(s): 
	Keyword(s): 
	Last Modified: 20-MAY-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- LinkAge Message Exchange, version 3.2 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When an NDR message is received by the Exchange Server computer through the
	Linkage SNADS Connector, an entry similar to the following is logged in the
	Exchange Connectivity Manager's log browser:
	
	  LME-SNADS-IN(014e) 4 22464:- Recipient: FPTEST(ATTPING), Status1: 0
	  '{SNA:0(No error)}' Status2: 201'{DIA:201(system error occurred)}'
	
	The Exchange Server recipient receives the following message in their inbox:
	
	  The message was undeliverable because the recipient specified in the
	  recipient postal address refused to accept the message.
	
	RESOLUTION
	==========
	
	A supported fix that corrects this problem is now available from Microsoft, but
	has not been fully regression-tested and should be applied only to systems
	experiencing this specific problem. If you are not severely affected by this
	specific problem, Microsoft recommends that you wait for the next service pack
	that contains this fix.
	
	To resolve this problem immediately, contact Microsoft Product Support Services
	to obtain the fix. For a complete list of Microsoft Product Support Services
	phone numbers and information on support costs, please go to the following
	address on the World Wide Web:
	
	  http://support.microsoft.com/default.aspx?scid=fh;EN-US;CNTACTMS
	
	The English version of this fix should have the following file attributes or
	later:
	
	  Component: Linkage SNADS Connector
	
	  File Name      Date      Time     Size
	  ----------------------------------------------
	  Lsdiamex.exe   8/19/98   10:31a   74,220 bytes
	  Mexdia.msg     8/19/98   10:22a    2,158 bytes
	
	This is a hotfix and distribution requires manager approval. To receive the
	hotfix, customers must be encountering the bug as described above. You must
	track the customers you send this to and supply them with the next service pack
	when it becomes available.
	
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in Linkage Message Exchange version
	3.2.
	
	MORE INFORMATION
	================
	
	If you enable the debug option by doing following:
	
	  add DEBUG=A30 in the [LME-SNADS-IN] and [LME-SNADS-OUT] sections of the
	  Linkage.ini and use Decsnd.exe to parse the *.snr files in the
	  \\Linkage\Traces directory
	
	you will get information similar to the following:
	
	  Prefix              >
	  Dist_Command        >
	  Dist_ID             >
	  Origin_REN          : "HOUSSW3"
	  Origin_DGN          : ""
	  Origin_DEN          : "        "
	  Origin_Seqno        : "0000"
	  Origin_DTM          : 1998/7/31 16:31:3:1
	  Dist_Gen_Options    >
	  Dist_Flags          : REPORT: Do not generate a report.
	  Hop_Count           : I(255)
	  Service_Parms       : Priority   (RLG) DATALO
	                     Protection (RLG) LEVEL 2 (SAFE STORE REQUIRED)
	                     Capacity   (RLG) INDEFINITE
	  Server_Object_Ind   : (No Server Object)
	  Origin_Agent        : 20F0F0F0: DIA Process Destination TP
	  Begin_Dest_Operands > C3 52 01                            |CR |
	  Dest_RGN            > ""
	  Begin_REN_List      > C3 53 01                            |CS |
	  Dest_REN            > "BENGAL"
	  Begin_DGN_List      > C3 54 01                            |CT |
	  Dest_DGN            > "BURMESE"
	  Begin_DEN_List      > C3 55 01                            |CU |
	  Dest_DEN            > "LPLESS3"
	  End_DEN_List        >
	  End_DGN_List        >
	  End_REN_List        >
	  End_Dest_Operands   >
	  Report_Correlation  >
	  Report-On_Origin_DGN: "BURMESE"
	  Report-On_Origin_DEN: "LPLESS3"
	  Report-On_Seqno     : "0010"
	  Report-On_DTM       : 1998/7/31 15:0:8:18
	  Report-On_Agent_Corr: E2 A3 85 A2 A3 40 A3 96 40 81 A3 A3 |Stest to att|
	                        97 89 95 87                         |ping|
	  Begin_Reprt_DGN_List> C3 54 01                            |CT |
	  Reported-On_Dest_DGN> "FPTEST"
	  Begin_Reprt_DEN_List> C3 55 01                            |CU |
	  Reported-On_Dest_DEN> "ATTPING"
	  Spec_SNADS/DIA_Type > DIA Report
	  Spec_SNADS/DIA_Conte>
	  SNADS/DIA Code      : System Error / Routing Error <<<<< Return code
	  End_Report_DEN_List >
	  End_Report_DGN_List >
	  DS_Suffix           >
	
	Additional query words:
	
	======================================================================
	Keywords          :  
	Technology        : kbZNotKeyword6 kbExchangeSearch kbLinkAgeSearch kbLinkAge320
	Version           : :3.2
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
