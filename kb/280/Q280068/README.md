---
layout: page
title: "Q280068: Games: How to Troubleshoot Invalid Page Faults (Part 1)"
permalink: /kb/280/Q280068/
---

## Q280068: Games: How to Troubleshoot Invalid Page Faults (Part 1)

{% raw %}

	Article: Q280068
	Product(s): Microsoft Home Games
	Version(s): 1.0,2.0,3.0
	Operating System(s): 
	Keyword(s): kberrmsg
	Last Modified: 06-AUG-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Age of Empires Expansion: The Rise of Rome, version 1.0 
	- Microsoft Age of Empires II Expansion: The Conquerors 
	- Microsoft Age of Empires II: The Age of Kings, version 2.0 
	- Microsoft Age of Empires, Gold Edition 
	- Microsoft Age of Empires, version 1.0 
	- Microsoft Allegiance, version 1.0 
	- Microsoft Asheron's Call, version 1.0 
	- Microsoft Baseball 2000 
	- Microsoft Baseball 2001 
	- Microsoft Best of Windows Entertainment Pack, version 1.0 
	- Microsoft Casino 
	- Microsoft Classic Board Games 
	- Microsoft Close Combat for Windows 1.0 
	- Microsoft Close Combat III: The Russian Front, version 3.0 
	- Microsoft Close Combat: A Bridge Too Far, version 2.0 
	- Microsoft Combat Flight Simulator 2: WWII Pacific Theater, version 1.0 
	- Microsoft Combat Flight Simulator: WWII Europe Series, version 1.0 
	- Microsoft Crimson Skies 
	- Microsoft Flight Simulator 2000 
	- Microsoft Flight Simulator 2000 Professional Edition 
	- Microsoft Flight Simulator 98 
	- Microsoft Golf 1999 Edition 
	- Microsoft Golf 2001 Edition 
	- Microsoft International Soccer 2000, version 1.0 
	- Microsoft Links 2001 
	- Microsoft Links LS 2000 
	- Microsoft MechWarrior 4: Vengeance 
	- Microsoft Metal Gear Solid 
	- Microsoft Midtown Madness 2, version 2.0 
	- Microsoft Midtown Madness, version 1.0 
	- Microsoft Monster Truck Madness 2, version 2.0 
	- Microsoft Monster Truck Madness, version 1.0 
	- Microsoft Motocross Madness 2, version 2.0 
	- Microsoft Motocross Madness, version 1.0 
	- Microsoft NBA Full Court Press for Windows, version 1.0 
	- Microsoft NBA Inside Drive 2000, version 1.0 
	- Microsoft NFL Fever 2000, version 1.0 
	- Microsoft Outwars, version 1.0 
	- Microsoft Pandora's Box, version 1.0 
	- Microsoft Pinball Arcade, version 1.0 
	- Microsoft Plus! Game Pack: Cards and Puzzles 
	- Microsoft Return of Arcade for Windows, version 1.0 
	- Microsoft Return of Arcade, Anniversary Edition 
	- Microsoft Revenge of Arcade, version 1.0 
	- Microsoft Soccer, version 1.0 
	- Microsoft StarLancer, version 1.0 
	- Microsoft Train Simulator, version 1.0 
	- Microsoft Urban Assault, version 1.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	This article is the first of two articles that describe how to troubleshoot
	"invalid page fault" and "fatal exception" error messages in the Microsoft games
	listed at the beginning of this article.
	
	For additional information about how to troubleshoot "invalid page fault" and
	"fatal exception" error messages, click the article number below to view the
	article in the Microsoft Knowledge Base:
	
	  Q280069 Games: How to Troubleshoot Invalid Page Faults and Exception Errors
	  (Part 2)
	
	MORE INFORMATION
	================
	
	The following topics are covered in part 1 of this article:
	
	- Types of Error Messages That You May Receive
	
	- How to Gather Clues About an Error Message
	
	Types of Error Messages that You May Receive
	--------------------------------------------
	
	When you run any of the Microsoft games listed at the beginning of this article,
	you may receive one of the following three types of error message:
	
	- Fatal exception
	
	- Illegal Operation
	
	Fatal Exception:
	
	A "fatal exception" error message is typically displayed on a blue screen, and
	appears similar to the following
	
	  A fatal exception <0X> has occurred at <xxxx:xxxxxxxx>
	
	where <0X> is a hexadecimal number from 00 to 0F that indicates the
	processor exception, and <xxxx:xxxxxxxx> is the code segment pointer and
	memory address at which the exception error occurred.
	
	A fatal exception error can occur if any of the following conditions is true:
	
	- A program attempts to call an illegal instruction.
	
	- A program attempts to access invalid data or instructions.
	
	- The privilege level of an operation is invalid.
	
	For additional information about "fatal exception" error messages, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q150314 Information About Fatal Exception Errors
	
	Illegal Operation:
	
	An "illegal operation" error message appears similar to the following:
	
	  This program has performed an illegal operation and will be shut down. If the
	  problem persists, contact the program vendor.
	
	When you click Details, you receive a detailed error message similar to the
	following:
	
	  <Program> caused an invalid page fault in module <filename> at
	  <xxxx:xxxxxxxx>.
	
	When you click OK, the program quits.
	
	You typically receive an "invalid page fault" or "general protection fault" error
	message when a program or a component attempts to read or write to a memory
	address that is not allocated to the program. When this occurs, the program may
	overwrite or damage data or instructions for another program that is using that
	memory address. You may also receive a different type of "illegal operation"
	error message, such as a "divide error," "invalid instruction," or "stack fault"
	error message.
	
	For additional information about possible causes of "illegal operation" error
	messages, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q82710 Causes of General Protection Faults
	
	NOTE: If you receive an "invalid page fault in module kernel32.dll" error
	message, a conflict may exist between the program and the Microsoft Windows
	operating system.
	
	For additional information about how to troubleshoot "invalid page fault in
	module kernel32.dll" error messages, click the article numbers below to view the
	articles in the Microsoft Knowledge Base:
	
	  Q218853 OFF2000: Troubleshooting Office Kernel32.dll Errors Under Win 98
	
	  Q218873 OFF2000: Troubleshooting Office Kernel32.dll Errors Under Win 95
	
	How to Get Clues from an Error Message
	--------------------------------------
	
	To use the error message to diagnose your problem, note the module name that is
	listed in the "Details" section of the "invalid page fault" error message.
	
	If the module name is a printer driver, a video driver, a sound card driver, an
	antivirus tool, or a component that is not part of the game, you can remove or
	update that module.
	
	If you do not recognize the module name, query the Microsoft Knowledge Base for
	the module name at the following Microsoft Web site:
	
	  http://support.microsoft.com/?pr=kbinfo
	
	For example, if you received an invalid page fault in module <unknown>:
	
	1. In the "Search (KB)" box, click the name of the game in which you receive the
	  error message.
	
	2. In the "For Solutions containing" box, type "invalid page fault in module
	  unknown".
	
	3. In the "Using" box, select The exact phrase entered, and then click Search
	  Now.
	
	NOTE: If you do not see the Using box, click Show Options.
	
	For additional information about how to search for information in the Microsoft
	Knowledge Base, click the article number below to view the article in the
	Microsoft Knowledge Base:
	
	  Q129725 Obtaining Knowledge Base Articles on the World Wide Web
	
	For additional information about how to contact Microsoft Technical Support,
	click the article number below to view the article in the Microsoft Knowledge
	Base:
	
	  Q280069 Games: How to Troubleshoot Invalid Page Faults and Exception Errors
	  (Part 2)
	
	How to Get Clues from Events That Precede an Error Message
	----------------------------------------------------------
	
	Sometimes, you can determine the cause of the problem by noting what occurred
	just before you received the error message, whether the problem also occurs in
	other programs, or if the problem occurs every time you attempt to perform a
	particular action.
	
	To determine the cause of the problem, answer the following questions:
	
	- Are other programs running on your computer when you receive the error message?
	
	- Is this a known issue with your game?
	
	- Does the problem only occur at a particular time, such as when you start the game or when you use a joystick?
	
	- Does the problem occur in other programs or games?
	
	- Can you reproduce the problem, or does it occur randomly?
	
	The following sections discuss each question and possible resolutions.
	
	Are other programs running on your computer when you receive the error message?:
	
	You can prevent or resolve many error messages by quitting all programs that are
	running on your computer before you start a game.
	
	To do this, follow these steps:
	
	1. Press CTRL+ALT+DELETE.
	
	2. In the Close Program dialog box, click any program except Explorer or Systray
	  (which are components of Microsoft Windows), and then click End Task.
	
	  If you receive a message stating that the program is busy or not responding,
	  click End Task again.
	
	3. Repeat steps 1 and 2 to quit all programs except Explorer and Systray.
	
	Is this a known issue with your game?:
	
	Certain "invalid page fault" or "fatal exception" error messages only occur when
	specific conditions are true. For more information about how to resolve specific
	error messages in the games listed at the beginning of this article, query the
	Microsoft Knowledge Base for the exact text of the error message at the
	following Microsoft Web site:
	
	  http://search.support.microsoft.com/kb/c.asp
	
	For example, if you received an invalid page fault in module <unknown>:
	
	1. In the "My search is about" box, click the name of the game in which you
	  receive the error message.
	
	2. Under "I want to search by", click "Keyword Search using" using, and then
	  click Exact Phrase in the "Keyword Search using" box.
	
	3. In the "My question is about" box, type invalid page fault in module unknown,
	  and then click Go.
	
	For additional information about how to find articles in the Microsoft Knowledge
	Base, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q129725 Obtaining Knowledge Base Articles on the World Wide Web
	
	If none of the articles in the Microsoft Knowledge Base describes your problem,
	please continue troubleshooting your problem using the information in this
	article.
	
	Does the problem only occur at a particular time?:
	
	If you receive the error message only when you perform a specific action or set
	of actions in the game, the actions that trigger the error message may provide
	clues about which solutions you should try first.
	
	For example if you only receive the error message when you press a programmed
	button on your joystick, you may want to disable programmed buttons, updated the
	joystick software, or even update the sound driver for your sound card if the
	joystick is connected to the game port on your sound card.
	
	If you receive an error message when you attempt to install the game, your CD-ROM
	or DVD-ROM drive may be unable to read the CD-ROM for the game.
	
	For additional information about how to troubleshoot CD-ROM read errors, click
	the article number below to view the article in the Microsoft Knowledge Base:
	
	  Q218617 How to Troubleshoot CD-ROM Read Errors
	
	Does the problem occur in other programs or games?:
	
	If the problem occurs in other programs or games, the problem most likely is
	caused by an outdated device driver, a damaged or missing component of Windows,
	or another program that is running in the background.
	
	NOTE: Although some of the troubleshooting tips and possible solutions in this
	article may help with these issue, the focus of this article is to resolve error
	messages that are specific to the game listed at the beginning of this article.
	
	Can you reproduce the problem, or does it occur randomly?:
	
	If you always receive the error message each time you perform a specific action
	or set of actions, use one of the suggested resolutions for the problem, and
	then perform that action or set of actions again. If you no longer receive the
	error message, you can assume that the problem is resolved. If you continue to
	receive the error message, you need to continue troubleshooting the problem.
	
	If you cannot easily reproduce the problem, use one of the suggested resolutions
	for the problem, and then play the game until you feel comfortable that the
	problem is resolved. If you continue to receive the error message, try another
	possible resolution.
	
	NOTE: Be sure to keep track of the resolutions that you have tried, along with
	the results for each one.
	
	For additional information about how to troubleshoot "invalid page fault" and
	"fatal exception" error messages in the games listed at the beginning of this
	article, click the article number below to view the article in the Microsoft
	Knowledge Base:
	
	  Q280069 Games: How to Troubleshoot Invalid Page Faults and Exception Errors
	  (Part 2)
	
	For more information about how to troubleshoot "invalid page fault" and "fatal
	exception" error messages in the games listed at the beginning of this article,
	click the article number below to view the second part of this article in the
	Microsoft Knowledge Base:
	
	  Q280069 Games: How to Troubleshoot Invalid Page Faults and Exception Errors
	  (Part 2)
	
	For additional information about other troubleshooting strategies, click the
	article number below to view the article in the Microsoft Knowledge Base:
	
	  Q275481 How to Troubleshoot Program Faults with Dr. Watson
	
	Additional query words: msgame trainsim
	
	======================================================================
	Keywords          : kberrmsg 
	Technology        : kbHomeProdSearch _IKkbbogus kbHomeMMsearch kbLinkGolfSearch kbAOE kbGamesSearch kbFlightSimSearch kbArcadeRet kbArcadeRev kbZNotKeyword kbGolf2001 kbGolf99 kbGolfSearch kbNFLFever2000 kbNFLSearch kbPinballArc kbArcadeSearch kbMSNSearch _IK kbAllegianceSearch kbMetalGearSearch kbPandoraSearch kbPlusSearch kbMotocrossSearch kbStarlancerSearch kbOutwarsSearch kbOutwars kbCrimsonSkiesSearch kbAsheronSearch kbCloseCombatSearch kbBaseballSearch kbMidtownMadSearch kbMonsterTMSearch kbAOESearch kbMidtownMadness kbWinEntPkSearch kbMonsterTM kbZNotKeyword3 kbAllegiance kbAsheron100 kbStarlancer kbWinEntPkBest kbUrbanAssault kbMonsterTM2 kbAOEExpRome kbAOE2ExpConquerors kbAOE2Kings kbBaseBall2001 kbCloseCombat2 kbCloseCombat3 kbCloseCombat kbCombatFlightSim2 kbCombatFlightSim kbCombatFlightSimSearch kbFlightSim2000 kbFlightSim98 kbSoccer kbMotocrossM kbClassicBoardGames kbMetalGearSolid kbMidtownMadness2 kbPandorasBox kbMotocrossM2 kbCasino kbCrimsonSkies kbLinks2001 kbLinksLS2000 kbNBAFullCourtPress kbNBAInsideDrive2000 kbBaseBall2000 kbIntlSoccer2000 kbPlusGamePk kbTrainSim kbSimSearch
	Version           : :1.0,2.0,3.0
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
