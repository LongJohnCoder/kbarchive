---
layout: page
title: "Q96250: How to Remove DoubleSpace and Preserve Your Files"
permalink: /kb/096/Q96250/
---

## Q96250: How to Remove DoubleSpace and Preserve Your Files

{% raw %}

	Article: Q96250
	Product(s): Microsoft Disk Operating System
	Version(s): MS-DOS:6.0,6.2,6.22
	Operating System(s): 
	Keyword(s): 
	Last Modified: 03-DEC-1999
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft MS-DOS operating system versions 6.0, 6.2, 6.22 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	
	The procedure for uncompressing a drive differs depending on which version of
	MS-DOS you are using. If you are using MS-DOS 6.2, run the DoubleSpace
	maintenance program and choose Uncompress from the Tools menu. If you are using
	MS-DOS 6.22, run the DriveSpace maintenance program and choose Uncompress from
	the Tools menu. If you are using MS-DOS 6.0 or you are having difficulty with
	MS-DOS 6.2 DoubleSpace uncompressing a drive, follow the procedure outlined in
	this article.
	
	The following procedure describes how to remove DoubleSpace from your hard disk
	while preserving your files. It is a lengthy procedure and should be followed
	only if DoubleSpace removal is necessary. If you need to change the size of your
	DoubleSpace volume, type "help dblspace" (without the quotation marks) at the
	MS-DOS command prompt and refer to the Help topic DBLSPACE /SIZE.
	
	If you want to remove DoubleSpace (and all data stored on the compressed drive)
	but you do not need to preserve your files, DoubleSpace provides a way to delete
	a compressed drive without manual intervention. You can delete a compressed
	volume file (CVF) using the DoubleSpace maintenance program interface or the
	command-line interface. To delete DoubleSpace using the DoubleSpace maintenance
	program, choose Delete from the Drive menu.
	
	MORE INFORMATION
	================
	
	This example assumes that you have compressed your boot drive (C) and that your
	DoubleSpace host partition is H. For more information on how DoubleSpace assigns
	host partitions, query on the following words in the Microsoft Knowledge Base:
	
	  doublespace and assigns and host
	
	The example also exclusively refers to MS-DOS 6.2 and DoubleSpace. If you are
	using MS-DOS 6.22, substitute DRVSPACE for DBLSPACE commands, DRVSPACE.* for
	DBLSPACE.*, and DRVSPACE.SYS for DBLSPACE.SYS.
	
	If you are not removing DoubleSpace from your boot drive, skip steps 2-7.
	
	1. Back up all the files you want to preserve from your compressed drive (C) by
	  using Microsoft Backup or a third-party backup utility. (For information on
	  using Microsoft Backup, see Chapter 3, "Managing Your System," in the
	  "Microsoft MS-DOS User's Guide.")
	
	2. When you remove DoubleSpace, what is now drive H will become drive C, which
	  means you will boot from drive H. To be able to boot from drive H and restore
	  your backup files, the DoubleSpace host partition must contain the necessary
	  MS-DOS system files and utilities. Furthermore, if you stored your backup
	  files on a network drive, network redirectors must be available.
	
	  Determine how much free space you will need to copy the MS-DOS files (and
	  network redirectors) on the DoubleSpace host partition (drive H). To do so,
	  use the DIR command. For example, to see how much space is needed for your
	  MS-DOS files, type the following command:
	
	  " dir c:\dos" (without the quotation marks)
	
	  The output appears as follows:
	
	      ...
	      UNFORMAT.COM
	      VALIDATE.COM
	      VSAFE.COM
	      XCOPY.EXE
	      194 file(s)    7003143 bytes
	                    12959744 bytes free
	
	  The next-to-last line shows the number of bytes used by the files in the DOS
	  directory. This number is the amount of free disk space needed to store the
	  necessary files and utilities after DoubleSpace is removed.
	
	3. To free unused disk space from the DoubleSpace compressed volume, use the
	  /SIZE switch as follows:
	
	      dblspace /size
	
	4. Determine how much free space there is on the DoubleSpace host partition. To
	  do this, change to drive H and use the DIR /A command. The last line of the
	  output from the DIR command shows the number of bytes free on drive H. If
	  this number is greater than the number you found in step 2, there is enough
	  space to copy the necessary files and utilities, and you can proceed with
	  step 6. If there is not enough space on the DoubleSpace host partition,
	  proceed to step 5.
	
	5. Delete enough files on drive C to create the needed space you determined
	  during step 2. (Note: Do not delete any MS-DOS or network files; those files
	  must be present during this procedure.)
	
	  You can use the DELTREE command to do this. (DELTREE quickly deletes entire
	  directories.) For example, to remove the WORD directory and all the files and
	  subdirectories it contains, type the following:
	
	  " deltree /y c:\word" (without the quotation marks)
	
	  After you delete some files, shrink the DoubleSpace volume file again by
	  typing the following:
	
	  " dblspace /size" (without the quotation marks)
	
	  To find out if you've created enough free disk space, change to drive H and
	  use the DIR command. Again, the bytes in use and bytes free are displayed. If
	  the last line, "bytes free," shows enough free disk space, continue with step
	  6. Otherwise, repeat step 5.
	
	6. Copy all the MS-DOS and network files that you need (the files you determined
	  were necessary during step 2) to the DoubleSpace host partition (drive H). To
	  preserve the file and directory structure, you can use the XCOPY command with
	  the /S switch. For example, to copy all the MS-DOS files into a DOS directory
	  on H, type the following:
	
	  " md h:\dos
	  xcopy c:\dos\*.* h:\dos /s" (without the quotation marks)
	
	7. Make sure there is a copy of COMMAND.COM in the root of the DoubleSpace host
	  partition by typing the following:
	
	  " dir h:\command.com" (without the quotation marks)
	
	  If COMMAND.COM is not present, copy it from the boot drive (C) with the
	  following command:
	
	  " copy c:\command.com h:\ " (without the quotation marks)
	
	  Repeat this step for AUTOEXEC.BAT and CONFIG.SYS files. These files need to be
	  in the root of the DoubleSpace host partition as well.
	
	  You now have all the files you need to boot from the uncompressed drive and
	  restore your backup files; you can begin removing the DoubleSpace volume.
	
	8. Switch to the root of the DoubleSpace host partition by typing the
	  following:
	
	  " h:
	  cd\ " (without the quotation marks)
	
	9. Delete the DoubleSpace files by using the following command:
	
	      deltree /y dblspace.*
	
	10. If you are removing DoubleSpace from your boot drive, open the CONFIG.SYS
	  file from the DoubleSpace host partition (H) in a text editor, such as
	  MS-DOS Editor. If you are not removing DoubleSpace from your boot drive,
	  open the CONFIG.SYS file from drive C. Remove any reference to DBLSPACE.SYS.
	  For example, change your DBLSPACE.SYS DEVICE command to appear as follows:
	
	      rem device=c:\dos\dblspace.sys
	
	11. Restart your computer by pressing CTRL+ALT+DEL.
	
	12. Restore your backup files.
	
	DoubleSpace has now been removed from your system.
	
	Additional query words: 6.00 6.20 uninstall un-install install mwbackup msbackup dblspace delete double space manager /uncompress
	
	======================================================================
	Keywords          :  
	Technology        : kbMSDOSSearch kbMSDOS622 kbMSDOS620 kbMSDOS600
	Version           : MS-DOS:6.0,6.2,6.22
	
	=============================================================================
	

{% endraw %}
