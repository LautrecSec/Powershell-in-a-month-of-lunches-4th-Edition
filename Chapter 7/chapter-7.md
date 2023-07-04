# 7.7 Lab

### 1. Browse the PowerShell Gallery. Find a module or two that you think sounds interesting and install it.

```powershell
PS C:\Labs> Install-Module -Name ConnectWiseAutomateAgent
Install-Module -Name PSLANScan
```

---

### 2. Browse the available commands for the module you just downloaded.

```powershell
get-command -Module ConnectWiseAutomateAgent
```

`output:`

```

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           ConvertFrom-LTSecurity                             0.1.2.0    ConnectWiseAutomateAgent
Alias           ConvertTo-LTSecurity                               0.1.2.0    ConnectWiseAutomateAgent
Alias           Get-LTErrors                                       0.1.2.0    ConnectWiseAutomateAgent
Alias           Get-LTLogging                                      0.1.2.0    ConnectWiseAutomateAgent
Alias           Get-LTProbeErrors                                  0.1.2.0    ConnectWiseAutomateAgent
Alias           Get-LTProxy                                        0.1.2.0    ConnectWiseAutomateAgent
Alias           Get-LTServiceInfo                                  0.1.2.0    ConnectWiseAutomateAgent
Alias           Get-LTServiceInfoBackup                            0.1.2.0    ConnectWiseAutomateAgent
Alias           Get-LTServiceSettings                              0.1.2.0    ConnectWiseAutomateAgent
Alias           Hide-LTAddRemove                                   0.1.2.0    ConnectWiseAutomateAgent
Alias           Install-LTService                                  0.1.2.0    ConnectWiseAutomateAgent
Alias           Invoke-LTServiceCommand                            0.1.2.0    ConnectWiseAutomateAgent
Alias           New-LTServiceBackup                                0.1.2.0    ConnectWiseAutomateAgent
Alias           Redo-LTService                                     0.1.2.0    ConnectWiseAutomateAgent
Alias           Reinstall-CWAA                                     0.1.2.0    ConnectWiseAutomateAgent
Alias           Reinstall-LTService                                0.1.2.0    ConnectWiseAutomateAgent
Alias           Rename-LTAddRemove                                 0.1.2.0    ConnectWiseAutomateAgent
Alias           Reset-LTService                                    0.1.2.0    ConnectWiseAutomateAgent
Alias           Restart-LTService                                  0.1.2.0    ConnectWiseAutomateAgent
Alias           Set-LTLogging                                      0.1.2.0    ConnectWiseAutomateAgent
Alias           Set-LTProxy                                        0.1.2.0    ConnectWiseAutomateAgent
Alias           Show-LTAddRemove                                   0.1.2.0    ConnectWiseAutomateAgent
Alias           Start-LTService                                    0.1.2.0    ConnectWiseAutomateAgent
Alias           Stop-LTService                                     0.1.2.0    ConnectWiseAutomateAgent
Alias           Test-LTPorts                                       0.1.2.0    ConnectWiseAutomateAgent
Alias           Uninstall-LTService                                0.1.2.0    ConnectWiseAutomateAgent
Alias           Update-LTService                                   0.1.2.0    ConnectWiseAutomateAgent
Function        ConvertFrom-CWAASecurity                           0.1.2.0    ConnectWiseAutomateAgent
Function        ConvertTo-CWAASecurity                             0.1.2.0    ConnectWiseAutomateAgent
Function        Get-CWAAError                                      0.1.2.0    ConnectWiseAutomateAgent
Function        Get-CWAAInfo                                       0.1.2.0    ConnectWiseAutomateAgent
Function        Get-CWAAInfoBackup                                 0.1.2.0    ConnectWiseAutomateAgent
Function        Get-CWAALogLevel                                   0.1.2.0    ConnectWiseAutomateAgent
Function        Get-CWAAProbeError                                 0.1.2.0    ConnectWiseAutomateAgent
Function        Get-CWAAProxy                                      0.1.2.0    ConnectWiseAutomateAgent
Function        Get-CWAASettings                                   0.1.2.0    ConnectWiseAutomateAgent
Function        Hide-CWAAAddRemove                                 0.1.2.0    ConnectWiseAutomateAgent
Function        Install-CWAA                                       0.1.2.0    ConnectWiseAutomateAgent
Function        Invoke-CWAACommand                                 0.1.2.0    ConnectWiseAutomateAgent
Function        New-CWAABackup                                     0.1.2.0    ConnectWiseAutomateAgent
Function        Redo-CWAA                                          0.1.2.0    ConnectWiseAutomateAgent
Function        Rename-CWAAAddRemove                               0.1.2.0    ConnectWiseAutomateAgent
Function        Reset-CWAA                                         0.1.2.0    ConnectWiseAutomateAgent
Function        Restart-CWAA                                       0.1.2.0    ConnectWiseAutomateAgent
Function        Set-CWAALogLevel                                   0.1.2.0    ConnectWiseAutomateAgent
Function        Set-CWAAProxy                                      0.1.2.0    ConnectWiseAutomateAgent
Function        Show-CWAAAddRemove                                 0.1.2.0    ConnectWiseAutomateAgent
Function        Start-CWAA                                         0.1.2.0    ConnectWiseAutomateAgent
Function        Stop-CWAA                                          0.1.2.0    ConnectWiseAutomateAgent
Function        Test-CWAAPort                                      0.1.2.0    ConnectWiseAutomateAgent
Function        Uninstall-CWAA                                     0.1.2.0    ConnectWiseAutomateAgent
Function        Update-CWAA                                        0.1.2.0    ConnectWiseAutomateAgent
```

```powershell
PS C:\Labs> Get-Command -module PSLANScan
```

`output`

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Find-LANHosts                                      1.2.0      PSLANScan
Function        Get-IPs                                            1.2.0      PSLANScan
```

---

### 3. Use the commands from section 7.2 to find and install (if needed) the latest-version module by Microsoft for working with archives that contain the command `Compress-Archive`.

```powershell
Find-Module -Command Compress-Archive | Install-Module -Force

```

---

### 4. Import the module you just installed.

&nbsp;
First, List all modules to see the full name of the module.

```powershell
PS C:\Labs> Get-Module
```

`output:`

```
ModuleType Version    PreRelease Name                                ExportedCommands
---------- -------    ---------- ----                                ----------------
Binary     7.0.0.0               CimCmdlets                          {Get-CimAssociatedInstance, Get-CimClass, Get-CimInstanc…
Script     0.1.2.0               ConnectWiseAutomateAgent            {ConvertFrom-CWAASecurity, ConvertTo-CWAASecurity, Get-C…
Manifest   1.2.5                 Microsoft.PowerShell.Archive        {Compress-Archive, Expand-Archive}
Manifest   7.0.0.0               Microsoft.PowerShell.Management     {Add-Content, Clear-Content, Clear-Item, Clear-ItemPrope…
Manifest   7.0.0.0               Microsoft.PowerShell.Security       {ConvertFrom-SecureString, ConvertTo-SecureString, Get-A…
Manifest   7.0.0.0               Microsoft.PowerShell.Utility        {Add-Member, Add-Type, Clear-Variable, Compare-Object…}
Manifest   2.0.0.0               NetAdapter                          {Disable-NetAdapter, Disable-NetAdapterBinding, Disable-…
Manifest   1.0.0.0               NetTCPIP                            {Find-NetRoute, Get-NetCompartment, Get-NetIPAddress, Ge…
Script     1.4.8.1               PackageManagement                   {Find-Package, Find-PackageProvider, Get-Package, Get-Pa…
Script     0.2.0                 PowerShellEditorServices.Commands   {Clear-Host, ConvertFrom-ScriptExtent, ConvertTo-ScriptE…
Binary     0.2.0                 PowerShellEditorServices.VSCode     {Close-VSCodeHtmlContentView, New-VSCodeHtmlContentView,…
Script     2.2.5                 PowerShellGet                       {Find-Command, Find-DscResource, Find-Module, Find-RoleC…
Manifest   1.2.0                 PSLANScan                           {Find-LANHosts, Get-IPs}
Script     2.2.6                 PSReadLine                          {Get-PSReadLineKeyHandler, Get-PSReadLineOption, Remove-…
```

&nbsp;
Then you can import it.

```powershell
PS C:\Labs> Import-Module Microsoft.PowerShell.Archive
```

---

### 5. Create a Tests folder for the next step with 10 files in it, and name it ~/TestFolder.

</br>
Creating a TestFolder

```powershell
PS C:\Labs> New-Item -ItemType Directory -Name TestFolder
```

Creating the 10 files in the TestFolder.

```powershell
PS C:\Labs> 1..10 | ForEach-Object {New-Item -ItemType File -Name ("/TestFolder/$_.txt" -f $_)}
```

`output:`

```
Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---          27/02/2023 12:40 am              0 1.txt
-a---          27/02/2023 12:40 am              0 2.txt
-a---          27/02/2023 12:40 am              0 3.txt
-a---          27/02/2023 12:40 am              0 4.txt
-a---          27/02/2023 12:40 am              0 5.txt
-a---          27/02/2023 12:40 am              0 6.txt
-a---          27/02/2023 12:40 am              0 7.txt
-a---          27/02/2023 12:40 am              0 8.txt
-a---          27/02/2023 12:40 am              0 9.txt
-a---          27/02/2023 12:40 am              0 10.txt
```

---

### 6. Compress-Archive ~/TestFolder/\* -DestinationPath ~/TestFolder.zip

```powershell
PS C:\Labs> Compress-Archive ~/TestFolder/* -DestinationPath ~/TestFolder.zip
```

---

### 7. Expand-Archive ~/TestFolder.zip -DestinationPath ~/TestFolder2

```powershell
PS C:\Labs> Expand-Archive ~/TestFolder.zip -DestinationPath ~/TestFolder2
```
