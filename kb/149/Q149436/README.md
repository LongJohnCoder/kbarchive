---
layout: page
title: "Q149436: Err Msg When Adding Remoteboot Workstations to Windows NT"
permalink: /kb/149/Q149436/
---

## Q149436: Err Msg When Adding Remoteboot Workstations to Windows NT

{% raw %}

	Article: Q149436
	Product(s): Microsoft Windows NT
	Version(s): 3.50 3.51
	Operating System(s): 
	Keyword(s): 
	Last Modified: 08-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.5, 3.51 
	-------------------------------------------------------------------------------
	
	SYMPTOMS
	========
	
	When you attempt to add a remoteboot workstation to the Remoteboot Manager in
	Windows NT. The following error messages appears when you manually enter the
	media access control address of a workstation:
	
	  The following error occurred creating the workstation: Chosen profile is
	  incompatible with this workstation.
	
	The following error message appears when you select a media access control
	address that has been broadcast over the network and choose the Convert Adapters
	option.
	
	  You have specified a profile which is not compatible with the adapter for
	  this workstation."
	
	In addition to this message, note that the selected profile in the Convert
	Adapters dialog box displays a workstation with a red X drawn through it,
	indicating that this profile is invalid for this workstation.
	
	CAUSE
	=====
	
	Windows NT examines the media access control address of the workstation's
	network adapter to determine if the adapter is valid for the selected
	configuration. The first six hexadecimal digits are examined and compared to a
	database kept by the Remoteboot Manager. The first six digits are a unique
	vendor ID. The remaining six digits are a unique network adapter address.
	
	Should a vendor acquire a new vendor ID, Windows NT will flag this media access
	control address as invalid because the new ID does not match those held in the
	remoteboot database.
	
	RESOLUTION
	==========
	
	Update the database so that it will recognize the new vendor ID. The steps below
	are an example, using an updated vendor ID for a 3Com Etherlink III adapter.
	
	1. Obtain the new media access control address for the workstation that you want
	  to add as a remoteboot workstation. This can often be done with utilities
	  that are included with the adapter. Another method can also be used: with the
	  remoteboot service started, boot the remote workstation. Although the boot
	  process will not be able to complete, the media access control address of the
	  workstation will be broadcast over the network and captured by the Windows NT
	  remoteboot service. Press F5 while Remoteboot Manager is the foreground task
	  to refresh the screen. The media access control address of the machine just
	  booted should be displayed. Note the first six digits of this address (the
	  vendor ID).
	
	2. Open a Command Prompt. Some commands entered will display many lines of text
	  that may scroll off the Command Prompt window. To retain this information
	  click the Command Prompt Control box and choose Properties. Select the Screen
	  Size and Position tab. In the Screen Size Buffer section increase the value
	  for height to a value such as 200.
	
	3. At the command prompt, type RPLCMD and press ENTER. A menu will be displayed
	  offering choices such as Adapter Boot Config. To select a menu item, type the
	  first letter of the command and press ENTER.
	
	4. Select Boot, then Enum. When asked for the Information Level, enter 2.
	
	5. A good deal of information will scroll by. The information for each adapter
	  will begin with an entry called "Bootname." Additional information for each
	  adapter is indented below that line. Scroll to the entry describing the
	  network adapter of interest.
	
	  This can be easily done by reading the BootComment line for each record since
	  this line describes the network card to which the record applies. In the case
	  of the Etherlink III used in this example you will find that the BootName
	  entry for this card is DOSH.
	
	6. Note all the information for this adapter, as you will need this information
	  later.
	
	7. Again, select Boot.
	
	8. Select Add. You will now be prompted for a BootName. Type the same name as
	  found in the information you recorded in step 6. For the the 3Com Etherlink
	  III, this name is DOSH.
	
	9. You are now prompted for a VendorName. Type the first six digits of the media
	  access control address found in step 1.
	
	10. You are now prompted for a BbcFile. Enter the same information as found in
	  step 6. For the 3Com Etherlink III the BbcFile is:
	
	  BBLOCK\NETBEUI\ELNK3\DOSBB.CNF.
	
	11. For BootComment, add any description that makes sense to you.
	
	12. For WindowsSize, enter a 0 (zero).
	
	13. You will now be taken back to the menu. Select Quit.
	
	The new vendor ID has now been entered into the database. It should now be
	possible to add this adapter back into the Remoteboot Manager without errors.
	
	
	Additional query words: prodnt
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNT351search kbWinNT350search kbWinNTSsearch kbWinNTS351 kbWinNTS350 kbWinNTS351search kbWinNTS350search
	Version           : 3.50 3.51
	
	=============================================================================
	

{% endraw %}
