---
layout: page
title: "Q224526: Windows NT 4.0 Supports Maximum of 7.8-GB System Partition"
permalink: /kb/224/Q224526/
---

## Q224526: Windows NT 4.0 Supports Maximum of 7.8-GB System Partition

{% raw %}

	Article: Q224526
	Product(s): Microsoft Windows NT
	Version(s): 3.5,3.51,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Operating System(s): 
	Keyword(s): 
	Last Modified: 27-OCT-2000
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Windows NT Server versions 3.51, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	- Microsoft Windows NT Server versions 4.0, 4.0 SP4, Terminal Server Edition 
	- Microsoft Windows NT Server, Enterprise Edition versions 4.0, 4.0 SP4 
	- Microsoft Windows NT Workstation versions 3.5, 3.51, 4.0, 4.0 SP1, 4.0 SP2, 4.0 SP3, 4.0 SP4, 4.0 SP5, 4.0 SP6, 4.0 SP6a 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Although Windows NT 4.0 can in theory support partitions of up to 16 exabytes in
	size using the NTFS file system, the maximum size of the system partition is
	limited to 7.8 gigabytes (GB).
	
	MORE INFORMATION
	================
	
	The system partition is defined as the partition containing the files needed for
	the initial system startup. For Windows NT, the files are Ntdetect.com, NTLDR,
	Boot.ini, and sometimes Ntbootdd.sys.
	
	A boot partition is defined as the partition containing the system files. For
	Windows NT, this is the partition containing the %SystemRoot%\System32 folder.
	
	The system partition and boot partition can be on the same partition or on
	different partitions. Because there can be multiple operating systems installed
	on a single computer, a computer can have multiple boot partitions, but a
	computer has only a single system partition.
	
	In some cases, the boot partition must be entirely within the first 7.8 GB of the
	drive. If the Boot.ini file uses the multi() syntax for locating the boot
	partition, NTLDR uses the INT13 interface to load the HAL, the kernel, and
	boot-start device drivers. In this case, these files must reside within the 7.8
	GB addresseable range of the INT13 interface. If the Boot.ini file uses scsi()
	syntax to find the boot partition, then a file named Ntbootdd.sys should exist
	on the system partition. This file is simply a renamed copy of the disk
	controller driver. In this case, NTLDR uses the Ntbootdd.sys driver to access
	the disk when loading the HAL, kernel, and boot-start device drivers. The
	addressable area of the disk is determined by this driver.
	
	When an Intel-based computer first boots, a number of things occur that result in
	the operating system being loaded and started. This process, known as the
	bootstrap process, has inherent hardware and software limitations beyond which
	Windows NT cannot operate. It is these limitations that prevent Windows NT 4.0
	from using a partition larger than 7.8 GB as a system partition.
	
	During the bootstrap process, the only mechanism available to Windows NT (or any
	other operating system) to access the drive is a set of functions in the BIOS
	known as Interrupt 13 (INT13). The INT13 functions allow low-level code to read
	from and write to the drive by addressing a specific sector on the drive. When
	the INT13 architecture was developed back in the early 1980s, the possibility of
	multi-gigabyte hard disks was not taken into consideration. The INT13 functions
	define 24 bits to describe a sector on the hard disk. This breaks down to a
	maximum of 256 heads (or sides), 1024 cylinders, and 63 sectors. With these
	numbers, only 256*1024*63 (or 16,515,072) sectors can be used with INT13
	functions. At a standard 512 bytes per sector, this is 8,455,716,864 bytes, or
	approximately 7.8 GB. Note that for most modern drives, the computer's BIOS must
	support some form of sector translation for the BIOS functions to address the
	first 7.8 GB of disk space. The BIOS in virtually all modern computers supports
	"Logical Block Addressing," which allows INT13 functions to address the first
	7.8 GB of drive space independent of the drive's physical geometry.
	
	The INT13 functions are the only means available to the operating system to gain
	access to the drive and system partition until the operating system loads
	additional drivers that allow it to gain access to the drive without going
	through INT13. Therefore, Windows NT 4.0 cannot use a system partition larger
	than 7.8 GB. In fact, the entire system partition must be entirely within the
	first 7.8 GB of the physical disk. Windows NT can use a 7.8-GB system partition
	only if the partition begins at the start of the physical drive.
	
	NOTE: Partitions other than the system partition are not affected by the these
	limitations.
	
	Other operating systems, such as Microsoft Windows 95 OEM Service Release 2,
	Microsoft Windows 98, and Microsoft Windows 2000, can boot from larger
	partitions because these operating systems were written after the computer
	industry defined a new standard for BIOS INT13 functions (the "INT13
	extensions") and implemented this new functionality on manufactured
	motherboards. Because Windows NT 4.0 was written before this new standard was
	invented, Windows NT 4.0 is unaware of this new technology and is unable to use
	its features.
	
	When you are installing Windows NT 4.0, you can create a system partition with a
	maximum size of 4 GB. This occurs because Setup first formats the partition
	using the FAT file system. If you want to use an NTFS partition, the partition
	is converted to NTFS after the first reboot. The FAT file system has a file
	system limitation (unrelated to any BIOS limitations) of 4 GB. When you perform
	an unattended installation, use of the ExtendOEMPartition directive in an
	Unattend.txt file can expand the system partition to a maximum of 7.8 GB.
	
	In the future, additional limitations may come into play as well. Although the
	NTFS file system can address 16 exabytes of disk space in a single partition,
	current disk-partitioning schemes store partition information in structures that
	limit partitions to 2^32 sectors, or 2 terabytes, in size. The ATA hardware
	interface uses 28-bit addressing, which supports drives that are 2^24 sectors,
	or 137 GB, in size. These limitations may apply to partitions other than the
	system partition as well.
	
	Note that file system limitations and hardware limitations exist independently of
	each other, and the most restrictive of the two is the determining factor in the
	maximum partition size. Another factor to consider when you are troubleshooting
	partitioning problems is that hard disk manufacturers often use "decimal
	megabytes" (1 megabyte = 1,000,000 bytes), whereas Windows NT uses "binary
	megabytes" (1 megabytes = 1,048,576 bytes). Using both definitions of a megabyte
	in calculations can often account for "lost" disk space. Also, this article
	assumes a sector size of 512 bytes in all calculations. Although a 512-byte
	sector has become a de facto industry standard, it is possible that disk
	manufacturers could produce drives with a different sector size. This would
	result in a corresponding change in partition limits. Partitions are based on
	cylinder, head, and sector calculations, not on byte calculations. Therefore, a
	change in bytes per sector causes a change in bytes per partition.
	
	
	REFERENCES
	==========
	
	For additional information about disk partitioning and limitations, please see
	the following articles in the Microsoft Knowledge Base:
	
	  Q114841 Windows NT Boot Process and Hard Disk Constraints
	
	  Q119497 Boot Partition Created During Setup Limited to 4 Gigabytes
	
	  Q197667 Installing Windows NT Server on a Large IDE Hard Disk
	
	  Q185773 NTFS Corruption on Drives > 4 GB Using ExtendOEMPartition
	
	  Q227879 Formatting Using the Compaq Array Configuration Utility
	
	Additional query words: smallbiz
	
	======================================================================
	Keywords          :  
	Technology        : kbWinNTsearch kbWinNTWsearch kbWinNTW400 kbWinNTW400search kbWinNT351xsearch kbWinNT350xsearch kbWinNT400xsearch kbWinNTW350 kbWinNTW350xsearch kbWinNTW351xsearch kbWinNTW351 kbWinNTW400sp5 kbWinNTW400sp4 kbWinNTW400sp3 kbWinNTW400sp2 kbWinNTW400sp1 kbWinNTSsearch kbWinNTSEntSearch kbWinNTSEnt400sp4 kbWinNTSEnt400 kbWinNTS400sp6 kbWinNTS400sp5 kbWinNTS400sp4 kbWinNTS400sp3 kbWinNTS400sp2 kbWinNTS400sp1 kbWinNTS400xsearch kbWinNTS400 kbWinNTS351 kbNTTermServ400 kbNTTermServ400sp4 kbNTTermServSearch kbWinNTS351xsearch kbWinNTW400sp6 kbWinNTW400SP6a
	Version           : :3.5,3.51,4.0,4.0 SP1,4.0 SP2,4.0 SP3,4.0 SP4,4.0 SP5,4.0 SP6,4.0 SP6a
	Issue type        : kbinfo
	
	=============================================================================
	

{% endraw %}
