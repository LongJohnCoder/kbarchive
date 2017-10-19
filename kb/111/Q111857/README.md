---
layout: page
title: "Q111857: SMTP: Missing Attachment Name in Client when Using PMDF Mailer"
permalink: /kb/111/Q111857/
---

## Q111857: SMTP: Missing Attachment Name in Client when Using PMDF Mailer

	Article: Q111857
	Product(s): Microsoft Mail For PC Networks
	Version(s): 
	Operating System(s): 
	Keyword(s): 
	Last Modified: 30-JUL-2001
	
	SYMPTOMS
	========
	
	Upon opening an attachment of a message from SMTP, the attachment name may not
	be found if the TCP/IP mail routing host used a PMDF mailer. The attachment
	itself is not lost, and is viewable.
	
	CAUSE
	=====
	
	The problem is in the RFC 822 header fields, and the order in which they appear.
	When using the PMDF mailer on the TCP/IP mail routing host, the
	"X-MS-Attachment" header line is re-ordered to appear before the "Encoding"
	header line. The SMTP gateway uses the "Encoding" header to build up a link list
	to describe the attachments and then fills in the file attributes later when it
	parses the "X-MS-Attachment" lines. If these two lines appear in the wrong
	order, the link list does not exist when the "X-MS-Attachment" header lines are
	being parsed. The gateway then ignores these lines, losing the names of any
	attachments.
	
	Looking at a log file generated by starting the SMTP gateway with the "-cd" and
	"-lacsy" switches, the incorrect header fields appear as:
	
	13:22:41 - Sending message to Microsoft Mail
	13:22:42 - Header: Return-Path: <root@company.com>
	13:22:42 - Header: Received: from company.com by smtp-gateway.company.com
	13:22:42 - Header: id <2C431991@smtp-gateway.company.com>; Tue, 13 Jul 93
	13:22:41 PDT
	13:22:42 - Header: Date: Tue, 13 Jul 1993 13:22:00 -0700 (PDT)
	13:22:42 - Header: From: Root <root@company.com>
	13:22:42 - Header: Subject: Testing word attachment thru SMTPgate
	13:22:42 - Header: To: "ROOT (COMPANY)" <root@company.oom>
	13:22:42 - Header: X-Mailer: Microsoft Mail V3.0
	13:22:42 - Header: X-MS-Attachment: smtptest.doc 1024 07-13-1993 13:20
	13:22:42 - Header: Encoding: 2 TEXT, 29 UUENCODE
	13:22:42 - Header:
	
	A correct set of headers should look like this:
	
	13:22:41 - Sending message to Microsoft Mail
	13:22:42 - Header: Return-Path: <root@company.com>
	13:22:42 - Header: Received: from company.com by smtp-gateway.company.com
	13:22:42 - Header: id <2C431991@smtp-gateway.company.com>; Tue, 13 Jul 93
	13:22:41 PDT
	13:22:42 - Header: Date: Tue, 13 Jul 1993 13:22:00 -0700 (PDT)
	13:22:42 - Header: From: Root <root@company.com>
	13:22:42 - Header: Subject: Testing word attachment thru SMTPgate
	13:22:42 - Header: To: "ROOT (COMPANY)" <root@company.oom>
	13:22:42 - Header: X-Mailer: Microsoft Mail V3.0
	13:22:42 - Header: Encoding: 2 TEXT, 29 UUENCODE
	13:22:42 - Header: X-MS-Attachment: smtptest.doc 1024 07-13-1993 13:20
	13:22:42 - Header:
	
	RESOLUTION
	==========
	
	Obtain the latest version of PMDF, from Innosoft. The latest version no longer
	re-orders the headers.
	
	Additional query words: 3.00 attachment pmdf SMTP
	
	======================================================================
	Keywords          :  
	
	=============================================================================
	