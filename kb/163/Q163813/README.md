---
layout: page
title: "Q163813: WD97: Boxes in Central European, Russian, or Greek Document"
permalink: /kb/163/Q163813/
---

## Q163813: WD97: Boxes in Central European, Russian, or Greek Document

{% raw %}

	Article: Q163813
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbinterop kbualink97 kbdta wd2000kbfaq
	Last Modified: 11-JUN-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	IMPORTANT: This article contains information about modifying the registry. Before you modify the registry, make sure to back it up and make sure that you understand how to restore the registry if a problem occurs. For information about how to back up, restore, and edit the registry, click the following article number to view the article in the Microsoft Knowledge Base:
	
	  Q256986 Description of the Microsoft Windows Registry
	
	SYMPTOMS
	========
	
	If you open a Microsoft Word document that was created using a Central European,
	Russian, or Greek version of Microsoft Word, the text of the document may appear
	as square boxes when you open the document in the U.S. version of Word 97.
	
	In rare cases, this problem may also occur opening documents created in the U.S.
	version of Microsoft Word.
	
	CAUSE
	=====
	
	Many fonts available in the Central European, Russian, and Greek markets have
	incorrect character set information. In these fonts, the character set parameter
	is mistakenly set to 0, incorrectly indicating a Western font.
	
	When the U.S. version of Word 97 opens the document, it converts it to Unicode
	based on the character set parameter. Since this parameter is incorrect, the
	conversion process is incorrect.
	
	
	RESOLUTION
	==========
	
	To correct this problem, install Microsoft Word 97 for Windows Service Release 1
	(SR- 1). This version of Word has been modified to correctly handle fonts that
	are known to have problems.
	
	For additional information about how to obtain Service Release 1 (SR-1), click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q172475 OFF97: How to Obtain and Install MS Office 97 SR-1
	
	WORKAROUND
	==========
	
	If you are unable to update to SR-1, use the following workaround.
	
	WARNING: If you use Registry Editor incorrectly, you may cause serious problems
	that may require you to reinstall your operating system. Microsoft cannot
	guarantee that you can solve problems that result from using Registry Editor
	incorrectly. Use Registry Editor at your own risk.
	
	To work around this problem, modify the Windows Registry to specify the correct
	font and code page Word needs to map the foreign language character set. To do
	this, follow these steps:
	
	1. Quit Word.
	
	2. On the Windows Start menu, click Run.
	
	3. In the Open box, type "RegEdit" (without the quotation marks) and then click
	  OK.
	
	4. Click to select the following key in the Windows Registry:
	
	  HKEY_CURRENT_USER\Software\Microsoft\Shared Tools\Font Mapping
	
	  This key determines which font and code page Word substitutes for a missing
	  font. If the font that exhibits the problem is not on your system, Word
	  substitutes the font specified by this key.
	
	5. If a font mapping does not already exist for the font that exhibits the
	  problem, create a new mapping. (If a font mapping already exists for this
	  font, skip to step 6.)
	
	  On the Edit menu, point to New, and then click String Value. Type the name of
	  the original font that is contained in the document, and then press ENTER.
	
	6. Click to select the original font name from step 5. On the Edit menu, click
	  Modify, and type the name of the font you want Word to use, followed by a
	  comma and the appropriate code page number from the following table. Use the
	  OEM Primary code page for Windows fonts and the Macintosh code page for
	  Macintosh fonts.
	
	  Code page            Macintosh     Windows
	  ------------------------------------------
	
	  Greek                10006         737
	  Russian              10007         866
	  Central European     10029         852
	
	For example, the following Edit String entry maps Systemny, a Macintosh font, to
	the Cyrillic portion of Arial.
	
	  Value Name: Systemny
	  Value Data: Arial,10007
	
	Reopening the Document in Word 6.0 or 7.0
	-----------------------------------------
	
	If you need to open the document again in Word 6.0 or 7.0, map the fonts
	correctly back to the original font. To do this, follow these steps:
	
	1. Open the document in Word 6.0 or 7.0.
	
	2. On the Tools menu, click Options.
	
	3. Click to select the Compatibility tab.
	
	4. Click Font Substitution, and then select the desired fonts for those that are
	  not available. Click OK.
	
	STATUS
	======
	
	Microsoft has confirmed this to be a problem in the Microsoft products that are
	listed at the beginning of this article.<A0>This problem was corrected in Microsoft
	Word 97 for Windows, Service Release 1 (SR-1).
	
	MORE INFORMATION
	================
	
	The following is a list of all known fonts that incorrectly set the character
	set parameter to 0. Microsoft Word 97 for Windows, Service Release 1 will
	perform a font substitution when opening a document containing one of these
	fonts and substitute the indicated font.
	
	The list of fonts is stored in the following registry location:
	
	  [HKEY_CURRENT_USER\Software\Microsoft\Shared Tools\Font Mapping]
	
	  "Tms Rmn"="Times Roman"
	  "Times"="Times Roman"
	  "Times Roman"="Times New Roman"
	  "Times New Roman"="Times"
	  "Helv"="Helvetica"
	  "Helvetica"="Arial"
	  "Arial"="Helvetica"
	  "Courier"="Courier New"
	  "Courier New"="Courier"
	  "Helvetica Narrow"="Arial Narrow"
	  "Arial Narrow"="Helvetica-Narrow"
	  "Helvetica-Narrow"="Helvetica Narrow"
	  "Bookman"="Bookman Old Style"
	  "Bookman Old Style"="Bookman"
	  "AvantGarde"="Avant Garde"
	  "Avant Garde"="Century Gothic"
	  "Century Gothic"="AvantGarde"
	  "Palatino"="Book Antiqua"
	  "Book Antiqua"="Palatino"
	  "NewCenturySchlbk"="New Century Schlbk"
	  "New Century Schlbk"="Century Schoolbook"
	  "Century Schoolbook"="NewCenturySchlbk"
	  "ZapfDingbats"="Zapf Dingbats"
	  "Zapf Dingbats"="Monotype Sorts"
	  "Monotype Sorts"="ZapfDingbats"
	  "ZapfChancery"="Zapf Chancery"
	  "Zapf Chancery"="Monotype Corsiva"
	  "Monotype Corsiva"="ZapfChancery"
	  "Garamond MT"="Garamond"
	  "Geneva"="Arial"
	  "Monaco"="Courier New"
	  "Chicago"="Arial"
	  "New York"="Times New Roman"
	  "London"="Old English Text MT"
	  "Los Angeles"="Onyx"
	  "Elite"="Roman 12cpi"
	  "EliteD"="Roman 6cpi"
	  "NLQ"="Roman 10cpi"
	  "Pica"="Roman 10cpi"
	  "PicaD"="Roman 5cpi"
	  "PS"="Roman PS"
	  "PSD"="Roman PX"
	  "Roman 12cpi"="Courier 12cpi"
	  "Courier 12cpi"="Roman 12cpi"
	  "Roman 6cpi"="Courier 6cpi"
	  "Courier 6cpi"="Roman 6cpi"
	  "Roman 10cpi"="Courier 10cpi"
	  "Courier 10cpi"="Roman 10cpi"
	  "Roman 5cpi"="Courier 5cpi"
	  "Courier 5cpi"="Roman 5cpi"
	  "Roman PS"="Courier PS"
	  "Courier PS"="Roman PS"
	  "NLQDblHigh"="NLQII 10cpi"
	  "PSNLQ"="Courier PS"
	  "Letter Gothic"="Courier New"
	  "CGTimes_Scale"="CG Times"
	  "CG Times"="CG Times (W1)"
	  "CG Times (W1)"="Times New Roman"
	  "Univers_Scale"="Univers"
	  "Univers"="Univers (W1)"
	  "Univers (W1)"="Arial"
	  "CourierPC"="MS LineDraw"
	  "Gothic"="Century Gothic"
	  "MT Symbol"="Symbol"
	  "MS LineDraw"="Courier New,437"
	  "Kafisma"="Arial,866"
	  "linedraw"="Courier New,437"
	
	Earlier versions of Word did not support Unicode. Unicode is a character set that
	supports most alphabets (languages) in the world. Before Unicode, a character
	set could support only 256 characters, so a different character set was needed
	for each alphabet. Word 97, which supports Unicode, maps characters from the old
	character set to the Unicode character set.
	
	To do a correct mapping, Word 97 must map the text to the proper character set.
	For example, character number 200 represents both a capital E (with a grave
	accent) in the Western European character set, and a capital I in the Cyrillic
	character set. To map each of these characters correctly to the Unicode
	character set, Word must map character number 200 to either the Western European
	range or the Cyrillic range within the Unicode character set. Word 97 has added
	extra functionality that allows character mapping to be made to a specific
	Unicode range in a font. For additional information, click the article number
	below to view the article in the Microsoft Knowledge Base:
	
	  Q141306 How to Enable Support for Multiple Languages in Windows
	
	
	  Q159418 WD97: Characters Appear as Square Boxes in Printed Document
	
	  Q159471 WD97: How to Install the Far East Support Files
	
	  Q99884 Unicode and Microsoft Windows NT
	
	
	For information about technical support for international versions of Microsoft
	products, please contact the Microsoft subsidiary in the appropriate country.
	
	To locate your subsidiary, please see the Microsoft World Wide Offices Web page
	at the following Web address:
	
	  http://www.microsoft.com/worldwide/default.htm
	
	Additional query words: SR1 release1 8.0 8.00
	
	======================================================================
	Keywords          : kbinterop kbualink97 kbdta wd2000 kbfaq
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbbug
	Solution Type     : kbfix
	
	=============================================================================
	

{% endraw %}
