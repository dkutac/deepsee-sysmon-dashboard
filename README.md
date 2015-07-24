deepsee-sysmon-dashboard
==============

A small set od DeepSee dashboards for selected system monitor metrics - data collected by %SYSMONMGR utility.


Installation
------------


1. Download Installer.cls.xml (from cls/kutac/monitor/utils folder in repository or releases page) into Caché manager directory.
2. Run in terminal (any namespace) under user with %All role: 

        do ##class(%Installer.Installer).InstallFromCommandLine(##class(%File).ManagerDirectory()_"Installer.cls.xml","Namespace={Namespace}")
        
    where:
  
        {Namespace} is a namespace you want to install to. If it does not exist it would be created automatically. If it does exist only kutac package would be overwritten. If {Namespace} is not defined, then SYSMON namespace will be created. 
    On this step installer would create (if needed) Namespace and corresponding database, download source code from GitHub and compile it, create required web application (named /cls/{Namespace}) if one does not exist (skipping web application creation process if one does exist), and map kutac package to %All namespace (which will be created if it does not exist).
        
        
Installation without fs access to server
-----------
1. Download Installer.cls.xml (from deepsee-sysmon-dashboards folder in repository or releases page) into Caché Studio (any namespace)
2. Run in terminal (any namespace) under user with %All role: 

        set pVars("Namespace")="{Namespace}"
        do ##class(kutac.monitor.utils.Installer).setup(.pVars)

    where: 
    
        {Namespace} is a namespace you want to install to. If it does not exist it would be created automatically. If it does exist only kutac package would be overwritten. If {Namespace} is not defined, then SYSMON namespace will be created. 
    On this step installer would create (if needed) Namespace and corresponding database, download source code from GitHub and compile it, create required web application (named /cls/{Namespace}) if one does not exist (skipping web application creation process if one does exist), and map kutac package to %All namespace (which will be created if it does not exist).
    
Offline Installation
-----------------

1. Download zip and unpack it.
2. Run in terminal (any namespace) under user with %All role:

        do ##class(%Installer.Installer).InstallFromCommandLine("{SourceDir}cls\kutac\monitor\utils\Installer.cls.xml","Namespace={Namespace},SourceDir={SourceDir}")

On this step installer would create (if needed) Namespace and corresponding database, import source code and compile it, create required web application (named /cls/{Namespace}) if one does not exist (skipping web application creation process if one does exist), and map kutac package to %All namespace (which will be created if it does not exist).

Default Settings
----------------

After mapping kutac package to %All namespace, namespaces %SYS and {Namespace} will be defined as startup namespaces for monitor. Then, the installer activates in the namespace %SYS" following monitor classes:

* %Monitor.System.HistoryPerf
* %Monitor.System.Diskspace
* %Monitor.System.License
* %Monitor.System.Processes
* %Monitor.System.HistorySys
* %Monitor.System.Freespace
* %Monitor.System.LockTable
* %Monitor.System.Routines

The next step is starting monitor. Your namespace will appear in the list of accessible namespaces for DeepSee and you can see different dashboards there. However, if you open User Portal in the DeepSee immediately after installing, you will notice that all dashboards will be empty. You need to wait a little time, because the installer runs the task for rebuilding cubes in 1 minute after installing. This task will run every 3 hours for updating information for monitor dashboards.




