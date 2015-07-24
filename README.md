deepsee-sysmon-dashboard
==============

A small set od DeepSee dashboards for selected system monitor metrics - data collected by %SYSMONMGR utility.


Installation
------------


1. Download Installer.cls.xml (from cls/kutac/monitor/utils folder in repository or releases page) into Caché manager directory.
2. Run in terminal (any namespace) under user with %All role: 

        do ##class(%Installer.Installer).InstallFromCommandLine(##class(%File).ManagerDirectory()_"Installer.cls.xml","Namespace={Namespace}")
        
    where:
  
        {Namespace} is a namespace you want to install to. If it does not exist it would be created automatically. If it does exist only kutac package would be overwritten. On this step installer would create (if needed) Namespace and corresponding database, download source code from GitHub and compile it, create required web application (named /cls/{Namespace}) if one does not exist (skipping web application creation process if one does exist), and map kutac package to %All namespace (which will be created if it does not exist).
        




