---
layout: page
title: "Q95099: Changing Colors in MS-DOS Shell"
permalink: /kb/095/Q95099/
---

## Q95099: Changing Colors in MS-DOS Shell

{% raw %}

	Article: Q95099
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:5.x,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 17-DEC-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article discusses changing colors in MS-DOS Shell and covers these two
	topics:
	
	- Choosing Colors in MS-DOS Shell Generates a Beep
	
	- Adding New Colors to MS-DOS Shell
	
	MORE INFORMATION
	================
	
	Choosing Colors in MS-DOS Shell Generates a Beep
	------------------------------------------------
	
	If your computer beeps when you try to choose Colors from the Options menu of
	MS-DOS Shell, the DOSSHELL.INI file is probably corrupt.
	
	To change the colors, MS-DOS Shell looks in the DOSSHELL.INI file for a section
	that begins with the line:
	
	     color =
	
	If this section does not exist, choosing Color causes a beep. To correct this
	problem, expand the file EGA.IN_ (for an EGA or VGA monitor) on Disk 3 (MS-DOS
	5.0 5.25-inch set) or Disk 2 (MS-DOS 6.0 5.25-inch set) or Disk 2 (MS-DOS 5.0
	3.5-inch set) or Disk 1 (MS-DOS 6.0 3.5-inch set).
	
	If you have a CGA monitor, the compressed file is CGA.IN_ instead of EGA.IN_. The
	EXPAND.EXE utility can be found on Disk 6 (5.25-inch set) or Disk 3 (3.5-inch
	set). The EGA.IN_ or CGA.IN_ file contains the same color information as the
	original DOSSHELL.INI. To get the color information into the DOSSHELL.INI, do
	the following (substitute "cga.in_" for "ega.in_" if you have a CGA monitor):
	
	1. Expand the file. For example:
	
	  " expand a:\ega.in_ c:\dos\color.txt " (without the quotation marks)
	
	2. Edit COLOR.TXT so only the color information is left in the file. To do this,
	  you can use MS-DOS Editor.
	
	3. Combine the DOSSHELL.INI file with the COLOR.TXT file. Use the COPY command:
	
	  " copy c:\dos\dosshell.ini + c:\dos\color.txt c:\dos\dosshell.ini " (without
	  the quotation marks)
	
	You should now be able to change the color scheme in MS-DOS Shell.
	
	Adding New Colors to MS-DOS Shell
	---------------------------------
	
	To change the colors in MS-DOS Shell, choose Color from the Options menu. Only
	certain choices are available; to create more choices, you must edit the
	DOSSHELL.INI file.
	
	The currentcolor= section is the color scheme being used. The color title is
	placed here. The color= section keeps records of all the available color
	schemes.
	
	The color options for the following include:
	
	  black         brightblack
	  white         brightwhite
	  red           brightred
	  cyan          brightcyan
	  magenta       brightmagenta
	  green         brightgreen
	  blue          brightblue
	  brown         brightyellow
	
	NOTE: There is no yellow or brightbrown color.
	
	The DOSSHELL.INI color settings are as follows:
	
	  Setting         Description
	  -------         -----------
	
	  color=          Header for the list of color schemes
	  selection=      Header for a particular color scheme
	  alert=          Color of a warning dialog box
	  menubar=        Color of the menu bar
	  menu=           Color of the menu text
	  disabled=       Color of a disabled menu item
	  accelerator=    Color of a menu accelerator
	  dialog=         Color of a dialog box
	  button=         Color of a button
	  elevator=       Color of the list box elevator
	  titlebar=       Color of the title bars when focused
	  scrollbar=      Color of a scroll bar
	  borders=        Color of the lines around menus and dialog boxes
	  drivebox=       Color of the area around the drive icons
	  driveicon=      Color of the drive icons
	  cursor=         Color of the mouse cursor
	
	You can change any part of the screen by changing the existing color name. You
	can create a new color scheme by copying one of the existing color schemes and
	changing the title and any of the individual colors. The name you choose for the
	new color scheme will be added to the Color Scheme dialog box.
	
	Additional query words: 5.00 5.00a 6.00
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS600 kbMSDOS500 kbMSDOS500a
	Version           : MS-DOS:5.x,6.0
	
	=============================================================================
	

{% endraw %}
