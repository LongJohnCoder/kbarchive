---
layout: page
title: "Q230287: Contents of Internet Information Server 4.0 Release Notes"
permalink: /kb/230/Q230287/
---

## Q230287: Contents of Internet Information Server 4.0 Release Notes

{% raw %}

	Article: Q230287
	Product(s): Internet Information Server
	Version(s): 4.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 22-FEB-2002
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Internet Information Server version 4.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	Following is a copy of the Internet Information Server 4.0 Release Notes
	included with the Windows NT 4.0 Option Pack.
	
	The file containing these Release Notes is located at
	<%SystemRoot%>\Help\iis\htm\core\iisread.htm.
	
	NOTE: The formatting and layout of the text below may vary slightly from the
	original.
	
	MORE INFORMATION
	================
	
	Internet Information Server Version 4.0 Release Notes
	-----------------------------------------------------
	
	Welcome to Microsoft(r) Internet Information Server (IIS) 4.0. Please refer to
	these release notes to obtain the most up-to-date information about
	installation, documentation, support, and other known issues.
	
	  Installing IIS 4.0
	  Product Documentation
	  Other Known Problems and Limitations
	  Providing Feedback
	  Microsoft Technical Support
	
	-------------------------------------------------------------------------------
	
	Installing Internet Information Server Version 4.0 
	--------------------------------------------------
	
	- Windows NT 4.0 and Service Pack 3: The Windows NT(r) Server service must be
	  installed and running.
	
	- When installing IIS 4.0 on a computer running Windows NT Server, the NetLogon
	  and Computer Browser services must be running. If these services are not
	  running, you will receive a dialog that says "Cannot detect OS type" and
	  Setup will fail.
	
	- Removal of Alpha, Beta 1, or Beta 2 software: If you have IIS version 4.0
	  Alpha or IIS version 4.0 (Beta 1 or Beta 2), be sure to uninstall that
	  release (before installing the current release). To do this, first start the
	  Setup program from the compact disc containing the earlier release or, in
	  Windows NT, click "Start", point to "Programs", point to "Microsoft Internet
	  Information Server (Common)", and then click "Internet Information Server
	  Setup". Click "Next", then click "Remove All".
	
	  ODBC installation errors will occur during setup if there are any other
	  applications or system services running that use the existing ODBC on the
	  system. If any ODBC errors occur, please stop all desktop and system service
	  applications, and run Setup again.
	
	  NOTES
	
	  The Windows NT 4.0 Option Pack only can be installed on Windows NT Server 4.0
	  and Windows NT Workstation 4.0.
	
	  The Personal Web Server for Windows 95 contained in the Windows NT 4.0 Option
	  Pack installs on both Windows 95 and Beta 3 of Windows 98.
	
	  The Windows NT 4.0 Option Pack cannot be installed on any version of Windows
	  NT 5.0.
	
	Other Installation Considerations:
	
	  Reinstalling Windows NT Service Pack 3:
	  If you reinstall Windows NT Service Pack 3 for any reason after IIS 4.0 is
	  installed, do not overwrite the newer files that were installed by IIS 4.0.
	
	  Uninstalling the Product:
	  To uninstall the product, rerun the Setup program for this release. There are
	  several ways to access the Setup program. You can use the compact disc, or
	  click "Start", point to "Programs", point to "Windows NT Option Pack 4.0",
	  and then click "Windows NT Option Pack 4.0 Setup". Follow the instructions in
	  the dialog boxes and, when prompted, click the "Add/Remove" button to
	  uninstall the software.
	
	  Installation Errors and Problems:
	
	- Errors that occur during unattended setup will be written to the Windows NT
	  registry. Navigate to the following registry path for error information:
	
	  HKEY_LOCAL_MACHINE\ 
	Software
	 \Microsoft
	  \Windows
	   \Setup
	    \OCmanager
	     \Errors
	
	- When installing IIS 4.0 on a Windows NT Server Backup Domain Controller
	  (BDC), in Setup you should select the Custom installation option and disable
	  Index Server and the Web Wide Web Sample Site. If you want to install Index
	  server or Web Wide Web Sample Site on a BDC, use Add/Remove feature in
	  Control Panel to install these components after the IIS installation has
	  completed.
	
	Upgrading Considerations:
	
	- IIS version 4.0 is not compatible with Microsoft Proxy Server 1.0. In order
	  to use Proxy server with IIS, please upgrade Proxy Server from version 1.0 to
	  version 2.0. Proxy Server version 2.0 should be installed or reinstalled
	  after IIS is upgraded to version 4.0. Additionally, present installations of
	  Proxy Server 2.0 will not function properly after IIS 4.0 has been installed.
	  You should rerun Proxy Server 2.0 Setup after installing IIS 4.0.
	
	- If you are upgrading from a previous version of IIS and you have trouble
	  viewing Default.asp, then you probably have an older version of this file. In
	  order to install the newer IIS 4.0 version of this file, you must manually
	  remove the older version of Default.asp. The default location is
	  C:\InetPub\Wwwroot.
	
	- You cannot use Internet Service Manager for Internet Information Server 3.0
	  to configure administrative properties for Internet Information Server 4.0.
	
	  Certificate Server Issues:
	  If you have Certificate Server installed, you must stop this service before
	  installing IIS. If you do not, you will not have properly installed the
	  updated ODBC drivers. In general, it is a good idea to shut down all
	  background applications before running Setup to avoid issues.
	
	  To stop the Certificate Server service on Windows NT, click "Start", point to
	  "Settings", click "Control Panel", and run the Services application. Select
	  "Certificate Authority", then click the "Stop" button. To restart the service
	  after the IIS installation has successfully completed, open "Control Panel",
	  start the "Services" application, select "Certificate Authority", and click
	  the "Start" button.
	
	  If you receive an error during setup that Msdasql.dll or Odbc*.dll failed to
	  be loaded, you will need to cancel setup, stop the services, and restart.
	
	  Setup.exe is not code signed:
	  When running Setup from the IIS CD from the setup Web page, Internet Explorer
	  will display an error message indicating that Setup.exe has not been code
	  signed. Setup.exe is a 16-bit file and 16-bit file formats cannot be code
	  signed.
	
	Product Documentation
	---------------------
	
	All documentation for the product is available online. You can access the Help
	topics by clicking "Start" and pointing to the program group where the product
	is installed, or by using the "Help" menu of the administration tool.
	Context-sensitive help is also available by clicking the "Help" button on a
	property sheet or dialog box.
	
	Using the Documentation:
	
	Please observe the following guidelines when using the online documentation:
	
	- The WWW service must be installed and the server must be running in order to
	  view the documentation (with the exception of release notes and
	  troubleshooting files). If the Web site is stopped, when you click "Product
	  Documentation" you will get a message that "A connection with the server
	  could not be established." If you get this error, start Internet Service
	  Manager and check the status of the Web site; if the site is stopped, then
	  start the service.
	
	- In Internet Explorer 4.01 users must enable the "Bypass proxy server for
	  local (Intranet) addresses" option on the "Connection" property sheet in
	  order to view local files, such as the product documentation
	
	- If you click the print icon in the Option Pack product documentation
	  "Contents" frame and select the option "Print everything contained in the
	  current heading", you may experience a temporary performance degradation on
	  the server if the selected section contains a large number of topics. Pages
	  printed by using the Contents print icon will not include graphics or linked
	  documents. Also, the Contents print icon does not work in conjunction with
	  the sample scripts and programs found in the Developer Samples section of the
	  IIS documentation. If you select a topic in the Developer Samples section and
	  click the Contents print icon, you will receive an error message indicating
	  that the file cannot be found.
	
	- In order to view the IIS documentation remotely, please use the following
	  URL: http://<servername>/iisHelp/ where <servername> is the
	  nameof the server running IIS.
	
	Other Known Problems and Limitations
	------------------------------------
	
	The following list contains known problems and limitations in this release:
	
	  Administration
	  Remote Administration with Internet Service Manager (HTML)
	  Internet Server Application Program Interface (ISAPI)
	  Active Server Pages
	  Server Security
	  Exploration Air Sample Site Issues
	  General
	
	Administration:
	
	- In previous versions of IIS, you could stop the entire Web service by typing
	  at the command line "net stop w3svc". This would terminate all of the Web
	  services on the computer, and shut down the Inetinfo.exe process. As a result
	  of the new multiple Web site architecture, there is another service,
	  Iisadmin, that keeps running, even when W3SVC is shut down. The same is true
	  for starting and stopping services from Control Panel. If you truly want to
	  unload the Inetinfo.exe process, and make sure that all of the extensions are
	  unloaded properly, you should now type "net stop iisadmin", rather than "net
	  stop w3svc". Typing "net start w3svc" or "net start msftpsvc" automatically
	  starts Iisadmin.
	
	- When you start the Web server it migrates all new virtual roots in the
	  registry to the metabase ("new" meaning, not already in the metabase). The
	  server then deletes all registry virtual roots and mirrors the virtual roots
	  from the metabase to those of the registry. Any change to metabase virtual
	  roots re-mirrors the virtual roots to the registry, deleting any registry
	  entries changed or added since the original installation.
	
	- The PStore service must be running in order to run IIS.
	
	- If you have a .dll file with special dependencies that require these files to
	  be loaded before other Web server processes, you can create a
	  registry-defined list of those .dll files that are to be preloaded into
	  Inetinfo.exe program before any other Web server services start up.
	
	  To preload .dll files, create a new registry key called PreloadDlls at the
	  following registry path:
	
	  HKEY_LOCAL_MACHINE\ 
	SYSTEM
	 \CurrentControlSet
	  \Services
	   \Inetinfo
	    \Parameters
	
	  Set this entry as type multi-sz, with data consisting of the names of the .dll
	  files that you want to preload (separated by carriage returns). If the files
	  reside in the same path, you can type just the name of the .dll file. If the
	  .dll file resides in another directory, type file name and its full path.
	
	- When you attempt to backup Web site configuration information you will be
	  prompted to type in a comment phrase before saving the configuration
	  information. However, you cannot save this information if your comment
	  includes non-alphanumeric characters, including nonprintable characters, or
	  any of the following characters:
	  / \ \ * . ? \ "& ! @ # $ % ^ ( ) = + | ` ~
	
	- You cannot use Internet Service Manager to remotely administer a computer
	  running IIS 4.0 Beta 3.0 from a computer running the final release of IIS
	  4.0. Likewise, you cannot administer a computer running IIS 4.0 final release
	  from one running IIS 4.0 Beta 3.0. This applies to all other applications
	  using the AdminBase interface. The workaround is to put the released version
	  of the file Admwprox.dll on all machines and then reboot.
	
	Remote Administration with Internet Service Manager (HTML):
	
	- To administer a remote computer running IIS 4.0 using Internet Server Manager
	  (HTML) to you must log on with a valid administrator (or operator) account
	  for that remote computer. With previous releases you could create a session
	  to \\ServerName\IPC$ using a different user account to get access, this will
	  not work for IIS 4.0. If you want to access Internet Service Manager (HTML)
	  on a remote computer with a different account (that is, an account other than
	  the account you use to log on the local computer), you must enable Basic
	  Authentication and disable Windows NT Challenge/Response authentication on
	  the Directory Security property sheet, so that you will be prompted for
	  proper user account credentials.
	
	- In order for Internet Service Manager (HTML) to function properly, you must
	  set your browser's cache to refresh with every visit to an HTML page. In IE
	  4.01 you can set this by following these steps:
	
	  1. Select the "View" menu item.
	
	  2. Select "Internet Options".
	
	  3. On the "General" tab, click the "Settings" button.
	
	  4. Under "Check for newer versions of stored pages", select the "Every visit
	     to the page" option.
	
	- Some Internet Information Server virtual directories are configured in such a
	  way that they appear as non-virtual directories to the IIS Administration
	  Objects. This configuration prevents the Administration Objects objects from
	  being administered by means of Internet Service Manager (HTML). The following
	  are the affected virtual directories:
	
	  Iishelp/Ado
	  Iishelp/Adc
	  Iishelp/Msadc
	  Iishelp/Ics
	  Msadc
	  Iishelp/Sse/Sa
	  Iishelp/Sse/Uaexpress
	  Iishelp/Ics/I_cmak
	  Iishelp/Ics/I_cps
	  Iishelp/Ics/I_ias
	  CertSrv
	  CertQue
	  CertAdm
	  CertControl
	
	  A script called Fixcfg.vbs (located in Winnt\System32\Inetsrv\Adminsamples, by
	  default) will correct this problem.
	
	- When administering your Web server with Internet Service Manager (HTML)
	  through a proxy connection, you cannot use Windows NT Challenge/Response
	  authentication. Proxy servers will only allow your Web server to use Basic
	  authentication.
	
	- If you create a new Web site in Microsoft Management Console, Web site
	  Operators cannot remotely connect to that site with Internet Service Manager
	  (HTML) until you create a virtual directory called IISADMIN. (Note that users
	  designated as Administrators are able to remotely administer the site through
	  the Administrative Web Site without this virtual directory). If you create
	  the Web site by using Internet Service Manager (HTML), then your Web server
	  will automatically create the IISADMIN site because the server assumes that
	  you will want to remotely administer that site.
	
	  To create the IISADMIN virtual directory:
	  1. In Internet Service Manager, select the Web site you want your Operators
	     to remotely administer.
	
	  2. Right-click, select "New", then click "Virtual Directory".
	
	  3. In the "Alias" box, type in "IISADMIN", then click "Next".
	
	  4. Type "<DriveLetter>:\Winnt\System32\Inetsrv\Iisadmin" where you
	     replace DriveLetter with the letter of your local drive. (This physical
	     path is the same as the path for the Default Web Site's Iisadmin
	     directory.) Click "Next".
	
	  5. Select "Allow Read Access" and "Allow Script Access." Click "Next".
	
	  6. Click "Finish".
	
	  7. Select the new IISADMIN virtual directory for the Web site, and open its
	     property sheets.
	
	  8. Select "Directory Security" property sheet, and under "Anonymous Access"
	     and "Authentication Control", click "Edit".
	
	  9. Clear the "Allow Anonymous Access" check box.
	
	  10. Select either "Basic Authentication" or "Windows NT Challenge/Response
	     Authentication" and click "OK".
	
	Internet Server Application Programming Interface (ISAPI):
	
	- The configuration metabase property InProcessIsapiApps
	  (MD_IN_PROCESS_ISAPI_APPS) now permits entries of .dll names without
	  qualifying paths. An entry without a qualifying path will match any ISAPI
	  request that contains the .dll name regardless of the physical path specified
	  in the request. For example, the following would be a valid list for the
	  property: "D:\Winnt\System32\Inetsrv\Ssinc.dll"
	  "D:\Winnt\System32\Inetsrv\Httpodbc.dll" "Author.dll" "Shtml.dll"
	  "Admin.dll".
	
	- When debugging ISAPI applications, ISAPI filters, server components, or other
	  code you are writing to run on top of IIS, it may be useful to run IIS as a
	  process. Information about configuring IIS 4.0 to run as a process is
	  outlined in the product documentation. Additional instructions and two .reg
	  files that automate the process of switching IIS to run as a service or a
	  process have been added to the IIS 4.0 SDK.
	
	  To install the SDK
	
	  1. In IIS Setup dialog box, select Internet Information Server then click
	     "Show Subcomponents".
	
	  2. Select Documentation, click "Show Subcomponents", then click "SDK".
	
	  3. Click OK.
	
	  You can find the instructions in
	  Inetpub\Iissamples\Sdk\Components\IIS_as_process.txt. For more information,
	  the topic "Establishing a Debugging Environment" in the Advanced Web
	  Application Development section of the Internet Information Server
	  documentation describes how to set up an environment for debugging ISAPI
	  extensions.
	
	- The metabase identifier MD_ALLOW_PATH_INFO_FOR_SCRIPT_MAPPINGS is not
	  documented in the Metabase Identifier Reference in the Programmer's
	  Reference. The documentation for the corresponding automation metabase
	  property, AllowPathInfoForScriptMappings, in the Administration Property
	  Reference also applies to MD_ALLOW_PATH_INFO_FOR_SCRIPT_MAPPINGS. The user
	  type is IIS_MD_UT_SERVER.
	
	- In the Metabase Identifier Reference, which is part of Programmer's Reference
	  documentation for the metabase identifier MD_SCRIPT_MAPS, the constant
	  MD_SCRIPTMAPFLAG_SCRIPT is incorrectly identified as
	  MD_SCRIPTMAPFLAG_SCRIPT_ENGINE.
	
	- The two configuration metabase properties, AppAllowDebugging and
	  AppAllowClientDebug, can be set at the IIsWebDirectory key in addition to the
	  other keys specified in the documentation.
	
	Active Server Pages:
	
	- Properties set for the ASP Request, Response, and Server objects are valid
	  only during the processing of a request. For example, if you set a property
	  in the Global.asa, such as Response.Buffer = True, the property will apply
	  only to a single request and not to all requests.
	
	- If you stop the WWW service from Internet Service Manager while debugging a
	  script, then Internet Service Manager will not function until you resume
	  execution of the script you are debugging. Normally, if you stop the Web
	  service using Control Panel or the "net stop" command, scripts being debugged
	  with Microsoft Script Debugger are terminated. However, if you stop a Web
	  site from Internet Service Manager, then the site will stop operation if you
	  are currently debugging scripts that are running on the server you are
	  stopping. If you go to the Microsoft Script Debugger and select "Stop
	  Debugging" for scripts that you are debugging, then Internet Service Manager
	  will resume operation.
	
	- There are currently known problems with using PerlScript with ASP. If you are
	  running PerlScript from ActiveWare, contact ActiveWare for a new PerlScript
	  engine.
	
	- There is a mistake in the ASP documentation which states that the MapPath
	  method does not support relative path syntax, such as ./path or ../path. The
	  MapPath method will support relative path syntax only if the
	  EnableParentPaths metabase property is enabled. When the EnableParentPaths
	  property is not enabled, using the MapPath method with a relative path
	  results in an error.
	
	- When setting Windows NT permissions for a directory for which you intend to
	  use use anonymous or Windows NT Challenge/Response authentication, you must
	  assign the anonymous user account (IUSR_computername) or the application
	  owner account (IWAM_computername) Read permissions if the directory contains
	  an out-of-process application and a Global.asa. Failure to set the Read
	  permission may result in ASP ignoring the Global.asa file.
	
	  Similarly, for in-process applications contained in directories stored on a
	  network drive, you must make sure that the anonymous user account has Windows
	  NT Read permissions.
	
	- In Microsoft(R) Visual Basic or VBScript, if you call GetObject() to
	  instantiate an IIS Admin Object, and GetObject fails, the returned error code
	  is changed in ole32 from MkParseDisplayName() to a MK_E_SYNTAX error.
	
	- If you create or use components developed in Microsoft(R) Visual Basic(R) 5.0
	  (Enterprise or Professional Editions) for use with ASP, it is strongly
	  recommended that you upgrade to Visual Studio(TM) 97 Service Pack 2, both for
	  your development and server computers. You can download the Visual Studio 97
	  Service Pack 2 at http://www.msdn.microsoft.com/vstudio/sp/.
	
	- The Scripting.Dictionary object is erroneously marked as Both-threaded. It
	  should be marked as Apartment-threaded. To change this, use the Registry
	  Editor to open the following registry key:
	
	  HKEY_CLASSES_ROOT\ 
	 CLSID
	  \{EE09B103-97E0-11CF-978F-00A02463E06F}
	   \InprocServer32
	
	  Change the named value for ThreadingModel to Apartment. If you use the
	  Dictionary object at Application scope without making this change, corruption
	  of data may occur.
	
	Server Security:
	
	- Although Internet Service Manager will allow you to enable password
	  synchronization for a non-local anonymous user account, this is not a
	  supported configuration, and may cause all access to your Web or FTP server
	  to be denied. Password synchronization should only be used with anonymous
	  user accounts defined on the local computer. If your Web site relies on the
	  anonymous user being able to access network resources, you cannot use the
	  anonymous authentication password synchronization feature and you must
	  specify a valid password for the anonymous user.
	
	Exploration Air Sample Site Issues:
	
	- If you have not installed the Remote Data Service included with Microsoft
	  Data Access Components 1.5, then you will need to edit the Prefs.txt file
	  (located in Inetpub\IISSamples\ExAir\Benefits\Prefs.txt, by default) to
	  disable the Remote Data Service feature, which is used in the Benefits
	  application of the Exploration Air. Specifically, set the RDSAvailable change
	  from True to False.
	
	- When using the Secure Sockets Layer (SSL) feature for file uploading, the
	  Posting Acceptor component will correctly upload a file onto your Web server;
	  however, the redirect to Verify.asp will fail. This will have no functional
	  effect on the Posting Acceptor Component.
	
	- The Exploration Air sample site's Microsoft SQL Server database is configured
	  to use the default user ID (UID) and password (that is, UID=sa and no
	  password.) Other SQL configurations will not work.
	
	- The file upload component found in the Business Partners Only link will not
	  work if the directory for the file upload is not properly configured.
	  Following is a procedure you can use to to configure your system for file
	  upload:
	
	  1. In the IISSamples\ExAir\BusinessPartners directory, create a subdirectory
	     called Upload.
	
	  2. Click "Start", point to "Programs", point to "Windows NT 4.0 Option Pack",
	     point to "Internet Information Server", and then click "Internet Service
	     Manager".
	
	  3. In the left pane of "Internet Service Manager", click Internet Information
	     Server folder, then double-click your icon named as your server.
	
	  4. Double-click "Default Web Site", then navigate to the
	     "IISSamples/ExAir/Business Partners/Upload" virtual directory.
	
	  5. Right-click "Upload", and select "Properties". In the "Directory" property
	     sheet, under "Access Permissions", select "Write".
	
	  6. Under Permissions in "Application Settings", select "None". These settings
	     will allow the "Posting Acceptor" component to work properly.
	
	  7. Close the Internet Service Manager and retry file uploading.
	
	General:
	
	- In addition to versioning your Web server configuration, the backup and
	  restore feature can be used to restore a previous IIS configuration when a
	  problem occurs that can be fixed by uninstalling and then re-installing IIS.
	  However, this process will not work when a complete re-installation of the
	  operating system is required. If your computer encounters a problem that
	  requires you to reinstall the Windows NT 4.0 Option Pack, use the following
	  procedure to restore a previous configuration:
	
	  1. In left pane of "Internet Service Manager", click the Internet Information
	     Server folder, then select then icon with the name of your computer.
	
	  2. From the Internet Service Manager tool bar, click "Action", then select
	     "Backup/Restore Configuration".
	
	  3. In the "Configuration Backup/Restore" dialog box, click "Create Backup".
	
	  4. In the "Configuration Backup Name" dialog box, type a name for the backup
	     file. By default, the backup file will be stored in the
	     C:\Winnt\System32\Inetsrv\Metaback directory. Alternatively, the backup
	     file may be stored in the directory specified in the following registry
	     entry (that is, if you have created this entry):
	
	     HKEY_LOCAL_MACHINE\ 
	SOFTWARE
	 \Microsoft
	  \InetStp
	   \MetaBackup
	
	     Select the value BackupPath, which contains the name of the backup file you
	     created with Internet Service Manager.
	
	  5. Copy the file to a location outside of the Inetsrv subdirectory. Backup
	     files in the Metaback subdirectory are deleted during the uninstall.
	
	  6. Uninstall and then re-install the Windows NT 4.0 Option Pack.
	
	  7. Copy the backup file to the Metaback subdirectory
	     (C:\Winnt\System32\Inetsrv\Metaback\ , by default.)
	
	  8. In the "Configuration Backup Name" dialog box, select the backup file you
	     created, and then click "Restore". Although the restoration may fail, a
	     portion of your backed up configuration will be restored.
	
	  9. At a command-prompt type, "cscript.exe
	     C:\Winnt\System32\Inetsrv\Adminsamples\Adsutil.vbs enum w3svc". This
	     command will list several IIS Web service settings. From the settings
	     listed find the WamUserName and WAMUserPass evalues. These values
	     represent the the user ID and password that the Windows Application
	     Manager (WAM) uses to start out-of-process applications. During
	     re-installation, the password is reset in the User Manager.
	
	     NOTE: To use the Adsutil.vbs utility you must have installed the Windows
	     Script Host as part of the Windows NT 4.0 Option Pack installation.
	
	  10. Click "Start", point to "Administrative Tools" and click "User Manager
	     for Domains". Double-click the IWAM_<computername> user account.
	     Type the password retrieved from the previous step.
	
	  11. Click OK.
	
	  12. In the "Configuration Backup Name" dialog box, select the backup file you
	     created, and then click "Restore". Your configuration should now be fully
	     restored.
	
	  NOTE: If you change the identity of your out-of-process applications, then
	  those applications will revert back to the previous IWAM user name.
	
	- Uninstalling Microsoft SNA Server 3.08 removes the Microsoft ODBC
	  Administrator file (Odbcad32.exe). However, you can manually access the
	  functionality achieved by this doing the following:
	
	  1. From the "Start" menu, point to "Settings", then click "Control Panel".
	
	  2. Double-click the "ODBC" icon. With the "ODBC Data Source Administrator"
	     dialog box, you can create, edit, and view ODBC data sources, and carry
	     out other ODBC administrative tasks.
	
	- In the IIS documentation, the Monitoring Counters for Web Sites topic refers
	  to the Trace Requests/sec counter. This counter is not available, although
	  the Total Trace Requests counter is available.
	
	- You cannot execute the ADSI Configuration Restore function from within a Web
	  Server application (like Active Server Pages or CGI applications). Executing
	  Configuration Restore from a Web Server application will cause the server to
	  stop responding.
	
	- Microsoft Index Server Issues:
	  When you create a new Web site, the site is not indexed by default. You must
	  select the "Index this directory option" on the "Home Directory" property
	  sheet.
	
	- Windows NT 4.0 Enterprise Edition:
	  Important: The clustering features described in the Windows NT 4.0 Option Pack
	  documentation are available only with the Windows NT 4.0 Enterprise Edition
	  and are not part of this Option Pack. When installing IIS over the clustering
	  features of the Windows NT 4.0 Enterprise Edition, the IIS setup Wizard will
	  exit if the cluster is not installed and shared correctly. To ensure the best
	  IIS and cluster setup use the following steps:
	
	  1. Install the clustering features of the Windows NT 4.0 Enterprise Edition
	     on both nodes of the cluster, start the cluster service, and verify
	     operation.
	
	     NOTE: In order to install Internet Information Server on Windows NT
	     Enterprise Edition, the path to the Windows directory must be the same on
	     the two nodes of the cluster.
	
	  2. Use the Cluster Administrator to move the cluster disk resource into the
	     same group as the cluster Name resource.
	
	  3. Install IIS on one node and do not reboot. Stop at the dialog box saying
	     that IIS should be installed on the other node before proceeding.
	
	  4. Install IIS on the second node and proceed with restarting both nodes.
	
	     NOTE: During installation of the Windows NT 4.0 Option Pack on the first
	     node of an Enterprise cluster, a warning message indicating an error in
	     the IIS Server Instance resource type may appear on the second node.
	     Disregard this message. The installation will proceed normally after
	     completion of the second node installation.
	
	- Prior to running the iissync command-line utility to replicate the metabase
	  from your server to a target computer on a cluster, you must set the
	  replication share on the source computer in Transaction Server Explorer. Use
	  the following procedure:
	
	  1. In the left pane of Internet Service Manager, double-click the "Console
	     Root" folder, then double-click the "Microsoft Transaction Server", then
	     double-click the "Computers" folder.
	
	  2. Click the "My Computer" icon, open the "My Computer" property sheets, and
	     then select the "Options" property sheet.
	
	  3. Under "Replication", in the "Replication Share" box type the name of a
	     Windows NT shared directory accessible by the target computer.
	
	  4. Click OK.
	
	- Internet Information Server 3.0 supported a cluster resource type called IIS
	  Virtual Root. This resource type is no longer supported and has been replaced
	  in IIS 4.0 by the IIS Server Instance resource type. If instances of the
	  obsolete resource type are present following installation of IIS 4.0, use the
	  Cluster Administrator to delete the instances.
	
	- When installing IIS 4.0 on Windows NT Enterprise Edition with Microsoft
	  Message Queue Server already installed, in certain cases Setup will fail and
	  display the following error message:
	
	  MS Data Access components 1.5
	
	  Unable to register the following file: C:\Program Files\Common
	  Files\System\Ole db\Msdasql.dll
	
	  If this message appears, click OK and allow Setup to complete. When the "Setup
	  of World Wide Web Server" failed error message appears, click OK. Run IIS
	  Setup again and choose "Remove All", then reinstall IIS. The MS Data Access
	  components will install without setup failing.
	
	-------------------------------------------------------------------------------
	
	Providing Feedback:
	
	Peer-to-peer newsgroups are available to help you interact with other users of
	our products, including Microsoft Most Valuable Professionals (MVPs). You can
	use any newsreader software to access these newsgroups. Regardless of the
	newsreader or news client you are using, you may need to configure it to read
	the newsgroups. When prompted for News Server, specify msnews.microsoft.com. You
	do not need to enter an account name or password. Before posting to the
	newsgroups, please review the Microsoft Newsgroup Rules of Conduct. For more
	information about Microsoft newsgroups please see
	http://support.microsoft.com/isapi/gosupport.asp?target=/newsgroups/ and choose
	Internet Information Server.
	
	Newsgroups supporting the Windows NT Option Pack 4.0 will become available in the
	near future. You should refresh your newsgroup subscriptions often in order to
	find the latest newsgroup for this product.
	-------------------------------------------------------------------------------
	
	Microsoft Technical Support:
	
	If you have a technical question about Microsoft(R) Internet Information Server,
	use this online documentation or consult Help by clicking the Help button during
	a procedure. If you still have a question, Microsoft offers technical support
	and services ranging from self-help tools to direct assistance with a Microsoft
	Technical Support Professional.
	
	NOTE: The services and prices listed here are available in the United States and
	Canada only (see Technical Support Worldwide below).
	
	Self-Help Tools to Find Answers Yourself
	----------------------------------------
	
	Microsoft Technical Support Online: This innovative site uses the cutting-edge
	technology of Microsoft to help you access the most relevant technical
	information and resources to answer your support questions. Use the
	Troubleshooting Wizards to easily diagnose and answer technical questions. Or
	select technical articles, programming aids, or commonly asked questions from
	the Microsoft Knowledge Base of over 75,000 articles. Visit
	http://www.microsoft.com/support/ today and see how easy it is to find the
	answers you need.
	
	Direct Assistance with a Microsoft Technical Support Professional
	-----------------------------------------------------------------
	
	Pay-Per-Incident Support: If you still need answers to your technical questions,
	you can purchase Pay-Per-Incident Support. In the U.S. and Canada, for a fee of
	$195 US per incident, please call (800) 936-5900, 24 hours a day, seven days a
	week, including holidays.
	
	NOTE: Support fees for the (800)# calls will be billed to your VISA, MasterCard,
	or American Express credit card.
	
	Priority Annual Support: If you anticipate a high volume of support incidents, or
	need priority access to Microsoft Technical Support Professionals, you can
	purchase a Priority Annual Comprehensive Account. In the U.S. and Canada, for
	more information or to purchase an annual account at a cost of $1,695US per 10
	incidents, call (800) 936-3500, 24 hours a day, 7 days a week, including
	holidays. To submit an incident against an existing account, call (800)
	936-4900, 24 hours a day, 7 days a week, including holidays.
	
	Submitting questions via the Internet: In the U.S. and Canada, you can also
	submit your Pay-Per-Incident or Priority Annual support questions via the
	Internet with Microsoft Online Assisted Support. For more details, visit the
	following Web site: http://support.microsoft.com/support/webresponse.asp.
	
	Priority Plus: Microsoft Technical Support also offers special accounts for
	medium-sized businesses that require priority incident resolution, including
	business-critical support and access to targeted information to assist
	information-technology and Help desk professionals in support planning for
	smoother product deployment. For more information, in the U.S. and Canada,
	please call (800) 936-3500, 24 hours a day, seven days a week, including
	holidays.
	
	Priority Consult Line: Receive hourly consulting for support questions that fall
	outside of the traditional technical support realm. These include designing or
	planning for deployment, software development, code review, and implementation
	planning. The Consult Line covers all Microsoft products, including those
	Microsoft products used for developing Internet and Intranet solutions. For more
	information or to purchase hourly consulting services at $195US per hour
	(minimum one hour), please call (800) 936-5200, Monday through Friday, excluding
	holidays, 6:00 A.M. to 6:00 P.M. Pacific time.
	
	Additional Support Options:
	
	Professional Programs and Services: Microsoft Technical Support also offers
	professional support programs and services for large businesses that require a
	direct relationship with Microsoft. For more information, see the Technical
	Support section of the Help file, or visit Microsoft Technical Support Online at
	http://www.microsoft.com/support/.
	
	Text Telephone: Microsoft text telephone (TTY/TTD) services are available for the
	deaf or hard-of-hearing. In the United States, using a TTY/TTD modem, dial (425)
	635-4948. In Canada, using a TTY/TTD modem, dial (905) 568-9641.
	
	Technical Support Worldwide: Support services and prices may vary outside the
	United States and Canada. For information on support available outside the U.S.
	and Canada, contact the local Microsoft subsidiary in your area. For a list of
	worldwide Microsoft subsidiaries, see the Technical Support section of the Help
	file, or visit Microsoft Technical Support Online at
	http://www.microsoft.com/support/.
	
	NOTE: The services and prices listed here are available in the United States and
	Canada only. Support services may vary outside the U.S. and Canada. For more
	information on support in other locations, contact your local Microsoft
	subsidiary. Microsoft's support services are subject to Microsoft's then-current
	prices, terms, and conditions, which are subject to change without notice.
	-------------------------------------------------------------------------------
	
	Copyright Information:
	
	(C) 1997 Microsoft Corporation
	
	These materials are provided "as-is," for informational purposes only.
	
	Neither Microsoft nor its suppliers makes any warranty, express or implied with
	respect to the content of these materials or the accuracy of any information
	contained herein, including, without limitation, the implied warranties of
	merchantability or fitness for a particular purpose. Because some
	states/jurisdictions do not allow exclusions of implied warranties, the above
	limitation may not apply to you.
	
	Neither Microsoft nor its suppliers shall have any liability for any damages
	whatsoever including consequential, incidental, direct, indirect, special, and
	lost profits. Because some states/jurisdictions do not allow exclusions of
	implied warranties, the above limitation may not apply to you. In any event,
	Microsoft's and its suppliers' entire liability in any manner arising out of
	these materials, whether by tort, contract, or otherwise shall not exceed the
	suggested retail price of these materials.
	
	Additional query words: iis kbreadme readme iisread.htm iisread akz
	
	======================================================================
	Keywords          :  
	Technology        : kbiisSearch kbiis400
	Version           : :4.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
