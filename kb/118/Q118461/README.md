---
layout: page
title: "Q118461: Ancient Lands: TROUBLE.TXT Contents"
permalink: /kb/118/Q118461/
---

## Q118461: Ancient Lands: TROUBLE.TXT Contents

{% raw %}

	Article: Q118461
	Product(s): Microsoft Home Multimedia Titles
	Version(s): WINDOWS:1.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-NOV-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Ancient Lands for Windows, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The following information is the contents of the TROUBLE.TXT file in the root
	directory of the Ancient Lands CD. The text below remains as released in the
	TROUBLE.TXT file, and has not been edited by PSS.
	
	=====================================================================
	                               TROUBLE.TXT
	=====================================================================
	
	Having problems running Microsoft Ancient Lands? Check the following
	list of solutions. If you don't find the information you need here,
	check the README file that was installed with Ancient Lands.
	
	PERFORMANCE PROBLEMS
	====================
	Microsoft Ancient Lands uses your computer's system memory to
	display pictures. If you find that Ancient Lands runs slowly
	or if you encounter out-of-memory errors, the program probably
	doesn't have enough memory. Consider doing the following to
	improve your computer's performance:
	
	* Close all unnecessary applications.
	
	* Determine how much total memory your computer has available
	 by typing "mem" and pressing ENTER at the DOS prompt.  You
	 need a minimum of 4MB (4,000K) of total memory to use Ancient
	 Lands.  If you do not have at least 4MB of memory available,
	 you will not be able to run Ancient Lands until you add more memory.
	
	* Ancient Lands needs a minimum of 5255K free in Windows for best
	 movie performance. To check the amount of free memory Windows
	 has available, start Windows, and from Program Manager pull down
	 the "Help" menu then choose "About Program Manager."
	
	* If you are running Windows in Enhanced mode, set up a permanent
	 Windows swap file on your hard disk.  A swap file of greater than
	 4MB (4,000K) is recommended. See your Windows documentation for
	 more information.
	
	* Defragment ("clean up") your hard disk by
	 running a defragmentation program.
	
	CD-ROM PROBLEMS
	===============
	
	NOTE - Do not remove the Ancient Lands compact disc from your
	CD-ROM drive while Ancient Lands is in the process of playing a
	sound or displaying a new picture, or is running in Slide Show mode.
	
	If the Ancient Lands program cannot find the data files that it
	needs from the Ancient Lands compact disc, you'll see a message
	that asks you to select the drive containing the files. To find
	the source of the problem, do the following:
	
	* Make sure the Ancient Lands compact disc is correctly
	 inserted into the CD-ROM drive.
	
	* Make sure that the Ancient Lands program is looking
	 for the compact disc on the correct drive. Check to
	 see if the drive letter for your CD-ROM drive has changed.
	 You can use the Windows File Manager to determine which
	 drive letter is assigned to the CD-ROM drive. The Select
	 Drive command in the Disk menu will say "CD-ROM" next to
	 the CD-ROM drive letter.
	
	* If you have an external CD-ROM drive, make sure that the
	 drive is connected to your computer, plugged in, and turned on.
	 If you still see the error message after checking the points
	 above, check the documentation that came with your CD-ROM drive
	 or contact the company that supplied the drive.
	
	* Make sure that your CD-ROM drive is MPC-compatible.
	 MPC-compatible drives meet the following criteria:
	 1. An average seek time of less than
	    one second;
	 2. A transfer rate of 150KB per second
	    while using less than 40% of the
	    CPU bandwidth.
	
	Check the documentation that came with your CD-ROM drive to make
	sure it meets these requirements. A CD-ROM drive that does not
	meet the MPC specifications will exhibit slow performance and/or
	"Audio blips/Interruptions" when sound is played.
	
	PRINTING AND COPYING
	====================
	
	The screens in Ancient Lands are large color pictures. Depending
	on the type of printer you have, printing a picture of the screen
	may take several minutes.  Also, screen resolution and printer
	resolution are often not the same, so the resulting printout may
	not match the quality you see on the screen.
	
	You should be able to print grayscale images from Ancient Lands.
	If you have a black-and-white laser printer you might need to
	upgrade your printer driver. Call the dealer from whom you bought
	the printer or the printer manufacturer. It is also possible to
	print Ancient Lands screens in color on a color printer.
	
	Because the pictures can be quite large, you may have difficulty
	copying or printing in low-memory conditions. In this case, close
	all other unnecessary applications and try again.
	
	GRAPHIC DISPLAY PROBLEMS
	========================
	Ancient Lands will run in 16-color or 256-color screen mode.
	The program will automatically detect what mode you are running
	and display pictures accordingly. If your computer is running
	in 16-color mode, and the video card will support 256 colors,
	you can run the Windows Setup program to change the video driver.
	This will enhance the image quality of Microsoft Ancient Lands.
	For more information on changing video drivers, check your
	Windows documentation.
	
	ANCIENT LANDS IMAGES APPEAR BLACK AND WHITE
	===========================================
	Some color video cards display Ancient Lands images in black and
	white.  This problem can be solved by updating your video driver.
	Contact your video card manufacturer for the updated 256-color
	Windows video drivers.
	
	ATI PROBLEMS
	============
	Microsoft Ancient Lands is incompatible with some advanced
	features used by some video cards such as the Mach32 chip
	set running the ATI drivers. For Ancient Lands to run on the
	ATI driver, the "256 color palette" control in the "Advanced
	features" of the "ATI Control Panel" needs to be set to ON.
	For more information, see the documentation for your video card.
	
	PROBLEMS WITH THE DISPLAY IN ANCIENT LANDS
	==========================================
	If you encounter problems displaying images or videos when
	running Microsoft Ancient Lands, check the currently installed
	video driver:
	
	1. Run the Windows Setup application.
	2. Locate the Display driver item in
	  the application window.
	
	If the display driver item is VGA:
	
	*Try running Windows in Standard Mode by typing "WIN /S"
	from the system prompt. If standard mode Windows works,
	try starting Windows in the enhanced mode with the
	following command:
	
	WIN /D:XV
	
	If this solves the problem, make the following
	modifications to your SYSTEM.INI file in the
	[386Enh] section:
	
	EMMEXCLUDE=A000-EFFF
	VIRTUALHDIRQ=OFF
	
	If the display driver item is NOT VGA:
	
	1. Run the Windows Setup application.
	2. Choose Change System Settings from
	  the Options menu.
	3. Change the Display setting to VGA.
	4. Choose OK and restart Windows.
	5. Run Microsoft Ancient Lands and determine
	  if the display problems still occur. If
	  the problem still exists, follow the
	  suggestions described for VGA
	  drivers, above.
	
	If the problem is solved, this indicates that your current
	video driver selection is experiencing problems rendering
	images in Ancient Lands. You might want to consider choosing
	another video driver (if available) provided by your video
	card manufacturer. To do so, run the Windows Setup application.
	If the problem persists, contact your video card manufacturer
	for updated video drivers.
	
	AUDIO PROBLEMS
	==============
	Audio problems can have many causes. Other applications that
	play sounds may interrupt sounds in Ancient Lands, because
	your computer cannot play two sounds simultaneously. This
	is generally a temporary clash that will resolve itself.
	However, a few applications that play sounds, such as some
	screen savers, may remove audio capability from all other
	Windows applications. If you suspect you have such an
	application, deactivate it or do not run it while running
	Ancient Lands.
	
	SOUNDS PLAY, BUT NOT VERY WELL
	==============================
	Sounds that are distorted or "fuzzy" have several possible
	causes. The most likely one is simply that your speakers are
	not of high quality. Low frequency sounds may not reproduce
	well on some equipment.
	
	It is also possible that the software settings on your
	sound board are causing distortion. For example, if the
	sound card volume or "WAVE file input" is set to near its
	maximum, it will produce amplification distortion, just as
	it would on a stereo system. To find out how to change your
	sound board settings, check the documentation that came with
	your sound board.
	
	Your CD-ROM drive should be MPC-compatible.
	MPC-compatible drives meet the following criteria:
	
	1. An average seek time of less than
	  one second;
	2. A transfer rate of 150KB per second
	  while using less than 40% of the
	  CPU bandwidth.
	
	Check the documentation that came with your CD-ROM drive
	to make sure it meets these requirements. An incompatible
	CD-ROM drive may work, however, it may produce low-quality
	audio or cause the sound to be interrupted while playing.
	
	SOUND BREAKS IN MOVIES
	======================
	If your video display is set to 16 colors and you are running
	Ancient Lands from a single-speed CD-ROM drive, you may experience
	sound breaks in certain movies. Running in 256 colors will fix this
	problem.
	
	SOUND DOESN'T PLAY AT ALL
	=========================
	If you don't hear any sounds,
	make sure that the volume is set to an audible level.
	
	If the volume is set to an audible level and you still
	hear no sounds at all, something may be wrong with your
	sound board setup. Check to see that the drivers are
	installed correctly and, if necessary, reinstall them.
	To determine if the sound drivers are installed check
	the Drivers section of the Windows Control Panel. For
	more information on installing your sound drivers,
	refer to the documentation that came with your sound
	card. If you have any problems, contact your sound
	board manufacturer for assistance.
	
	Please note that Ancient Lands requires an MPC-compatible
	sound board and is not intended to run with drivers which
	use the PC speaker, such as the unsupported "PC Speaker"
	driver. Such a driver will in most cases not play any
	sounds, and if the driver setup option "Enable Interrupts"
	is not checked, the system may lock up. Check the "Drivers"
	configuration in your Windows Control Panel. If you have
	both a sound board and the PC Speaker driver installed, it
	is recommended that you remove the PC Speaker driver.
	
	Media Vision Cards
	==================
	A small number of Media Vision sound card drivers
	(Pro Audio - Spectrum cards) may have problems with
	sound in Ancient Lands.  If you have a Media Vision
	card and do not hear sounds or are having other sound
	problems, you might require updated drivers.
	Contact Media Vision for current driver information.
	
	If you are running Microsoft Ancient Lands on an EISA
	machine and experience "scratchy" audio, try changing
	the DMA channel on the sound card to DMA 7.
	
	RUNNING UNDER MICROSOFT WINDOWS NT
	====================================================
	There are two potential problems with Ancient Lands
	running under Windows NT version 3.0. First, there
	is no VGA support for Ancient Lands, if you are running
	Windows NT you need to be using a VGA+ (256-color)
	or better display to use Ancient Lands.
	
	ANCIENT LANDS MOVIES
	====================
	The Ancient Lands Movies play full-screen by
	default. Some video drivers don't play movies
	properly full-screen (on a black background).
	If Ancient Lands detects a problem when playing
	movies it should switch to playing movies in a window.
	
	If you have problems playing movies full-screen or
	if you would like to switch between playing movies
	full-screen or in a window, change the "VideoInWindow"
	line in your MSLANDS.INI file in your WINDOWS directory
	as follows:
	
	VideoInWindow=0   (This will make movies play full-screen)
	
	VideoInWindow=1   (This will make movies play in a window)
	
	Additional query words: kbhowto 1994multi media multimedia multi-media
	
	======================================================================
	Keywords          :  
	Technology        : kbHomeProdSearch kbZNotKeyword kbAncientLands
	Version           : WINDOWS:1.0
	
	=============================================================================
	

{% endraw %}
