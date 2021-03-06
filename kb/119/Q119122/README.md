---
layout: page
title: "Q119122: WD97: Changing the Calendar Wizard Document Formatting"
permalink: /kb/119/Q119122/
---

## Q119122: WD97: Changing the Calendar Wizard Document Formatting

{% raw %}

	Article: Q119122
	Product(s): Word 97 for Windows
	Version(s): WINDOWS:97
	Operating System(s): 
	Keyword(s): kbualink97 kbdta kbtemplate word97
	Last Modified: 14-NOV-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Word 97 for Windows 
	-------------------------------------------------------------------------------
	
	
	SUMMARY
	=======
	
	Microsoft Word provides a Calendar Wizard for creating calendars. The wizard
	does not prompt you to modify character formatting such as font, point size, and
	so forth. This article describes how you can use the Calendar Wizard to create
	your own custom wizard.
	
	NOTE: Microsoft does not support the modification of its wizards or templates.
	Modifications done by the user are at the user's risk and constitute no
	obligations or warranties, either written or expressed, by Microsoft.
	
	MORE INFORMATION
	================
	
	To create a new, modified calendar wizard, follow these steps.
	
	NOTE: The Calendar Wizard is not installed when you do a complete installation of
	Office or Word. It is available on the Office or Word CD-ROM in the
	"\Valupack\Template\Word" folder. Copy the template from the CD-ROM to the
	following folder on your hard disk drive: C:\Program Files\Microsoft
	Office\Templates\Other Documents.
	
	1. On the File menu, click Open. Change to the "\Program Files\Microsoft
	  Office\Templates\Other Documents" folder or to the folder that contains the
	  Calendar Wizard.
	
	  In the Files Of Type list, select All Files. In the File Name list, select the
	  Calendar Wizard and then click Open. On the File menu, click Save As and type
	  a new name for the wizard. Any formatting changes you make will now be stored
	  in your new wizard.
	
	2. On the View menu, click Page Layout.
	
	3. NOTE: The Calendar Wizard is composed of AutoText entries which correspond to
	  the styles listed in the following table. Before you insert and modify an
	  AutoText entry, change the page orientation to either portrait or landscape
	  to correspond with the calendar style.
	
	  To modify the page orientation, click Page Setup on the File menu, then select
	  the Paper Size tab. Select Portrait or Landscape based on one of the
	  following calendar styles:
	
	  NOTE: The names of the AutoText Entries are listed in the columns labeled
	  Portrait and Landscape.
	
	      Calendar style                          Portrait       Landscape
	      ----------------------------------------------------------------
	
	      Boxes and borders with picture          Boxes00        Boxes10
	      Boxes and borders without picture       Boxes01        Boxes11
	      Banner with picture                     Banner00       Banner10
	      Banner without picture                  Banner01       Banner11
	      Jazzy with picture                      Jazzy00        Jazzy10
	      Jazzy without picture                   Jazzy01        Jazzy11
	
	4. On the Insert menu, point to AutoText, and then click AutoText. Select the
	  AutoText tab. Choose the AutoText entry that corresponds to the calendar
	  style you are creating, and then click the Insert button.
	
	  NOTE: Each AutoText entry contains both drawing objects and text boxes. These
	  drawing objects are visible only in page layout view or print preview. (You
	  will see a blank page after you insert the AutoText entry if you are working
	  in normal view.)
	
	5. Click the Show/Hide button so that it is enabled, display table gridlines (on
	  the Table menu, click Show Gridlines), and turn on Bookmarks (click Options
	  on the Tools menu, select the View tab, click to select the Bookmarks check
	  box, and then click OK).
	
	  NOTE: Do not delete any of the bookmarks. If these are deleted, the wizard may
	  not function properly.
	
	6. Select the text or table cell in which you want to make changes (be sure the
	  end-of-cell marker or paragraph mark is also selected). Make your formatting
	  changes, such as changing the font or point size, adding bold or italics, and
	  so forth. When finished, cancel the selection by clicking in the margin of
	  the document.
	
	7. On the Insert menu, point to AutoText, and then click AutoText. Select the
	  AutoText tab. Select the AutoText entry that you previously selected in step
	  4. Click Delete to delete the old AutoText entry. Click Close to return to
	  the document.
	
	8. Click the Drawing button on the Standard Toolbar to open the Drawing toolbar.
	
	9. Click the Select Drawing Objects button on the Drawing Toolbar. Starting in
	  the upper-left corner of the template, click and drag down and to the
	  lower-right corner to enclose the entire document area. A dashed line appears
	  as you are dragging to enclose the objects.
	
	10. On the Insert menu, point to AutoText and then click AutoText. Select the
	  AutoText tab. In the Enter AutoText Entries Here box, type the AutoText name
	  using the same name as the AutoText entry you deleted in step 7 and click
	  OK. In the "Look In" list, select the template you saved in step 1. Click
	  Add and then click OK.
	
	11. With the document still selected, click Cut on the Edit menu. You should now
	  have a blank page with a single paragraph mark at the upper left of the
	  page. If you have any text or more than a single paragraph mark, delete
	  these items. Click Save on the File menu, and then close the template.
	
	NOTE: The diskette version of Word does not contain the ValuPack folder. This
	wizard, and many more for Word, may be downloaded from Microsoft's World Wide
	Web site for free.
	
	For more information about where to get these additional wizards, please see the
	following article in the Microsoft Knowledge Base:
	
	  Q163549 WD97: Downloads and Updates Available from Microsoft
	
	Now you can use your new, modified Calendar Wizard. To create a new calendar
	based on your modified Calendar Wizard, follow these steps:
	
	1. On the File menu, click New.
	
	2. On the Other Documents tab, click to select your modified Calendar Wizard,
	  click OK, and then complete the steps of the Calendar Wizard.
	
	Additional query words: calendar wizard modify change format value pack 8.0
	
	======================================================================
	Keywords          : kbualink97 kbdta kbtemplate word97 
	Technology        : kbWordSearch kbWord97 kbWord97Search kbZNotKeyword2
	Version           : WINDOWS:97
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
