---
layout: page
title: "Q152694: How To Add BMPs to Picture Properties in OutLine Control"
permalink: /kb/152/Q152694/
---

## Q152694: How To Add BMPs to Picture Properties in OutLine Control

{% raw %}

	Article: Q152694
	Product(s): Microsoft FoxPro
	Version(s): WINDOWS:3.0,3.0b
	Operating System(s): 
	Keyword(s): 
	Last Modified: 15-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The On-line Help for the PictureClosed, PictureOpen, and PictureLeaf properties
	states that these properties can display either bitmap files (*.BMP) or icon
	files (*.ICO). This article describes how to add or change a BMP or ICO file in
	the PictureClosed, PictureOpen, or PictureLeaf properties through the interface
	of the OutLine control. This cannot be done programmatically.
	
	MORE INFORMATION
	================
	
	When using the Outline control, the Style property has 5 items to select from:
	
	1. Picture and Text.
	
	2. Plus/Minus and Text.
	
	3. Plus/Minus, Picture, and Text.
	
	4. Treelines and text.
	
	5. Treelines, Pictures, and Text.
	
	Choosing 1, 3, or 5 allows pictures to be used when items are listed in the
	Outline control. If an item has sub-items under it, the PictureClosed and
	PictureOpen properties can be used to show a different BMP or ICO to illustrate
	if the item is displaying those sub-items or not. The default pictures show an
	open folder for the PictureOpen property and a closed folder for the
	PictureClosed property. Any BMP or ICO can be used for these properties, but
	they have to be assigned in the Properties box for the Outline control in design
	mode.
	
	Step-by Step Example
	--------------------
	
	1. Create a form and choose an OLE container object from the Forms control
	  toolbar.
	
	2. Click the Insert Control button, and select Outline control from the
	  Control_Type box.
	
	3. Place the cursor over the OutLine control and click the right mouse button.
	
	4. After selecting Properties from the menu box, choose the Pictures tab. There
	  will be a Property Name combo box that allows the selection of the
	  PictureClosed, PictureOpen, and PictureLeaf properties.
	
	5. Use the Browse button to select a BMP or ICO for the selected property.
	
	Additional query words: VFoxWin
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b
	Version           : WINDOWS:3.0,3.0b
	
	=============================================================================
	

{% endraw %}
