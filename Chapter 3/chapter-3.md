# 3.8 Lab

### 1. Run Update-Help, and ensure that it completes without errors so that you have a copy of the help on your local computer. You need an internet connection.

```powershell
PS> update-help -force
```

---

### 2. Can you find any cmdlets capable of converting other cmdlets’ output into HTML?

```powershell
help html
```

`output:`

```
NAME
 ConvertTo-Html

SYNOPSIS
 Converts .NET objects into HTML that can be displayed in a Web browser.
```

---

### 3. Are there any cmdlets that can redirect output into a file?

```powershell
Get-Command -Noun file, output
```

`output:`

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Out-File                                           3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Unblock-File                                       3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Write-Output                                       3.1.0.0    Microsoft.PowerShell.Utility
```

After the command, I can see which command would bee.
In this case, it seems that the command is `out-file`

```powershell
help out-file
```

`output:`

```
NAME
Out-File

SYNOPSIS
Sends output to a file.
```

---

### 4. How many cmdlets are available for working with processes? (Hint: Remember that cmdlets all use a singular noun.)

```powershell
Get-Command -Noun Process
```

`output:`

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Debug-Process                                      3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Get-Process                                        3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Start-Process                                      3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Stop-Process                                       3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Wait-Process                                       3.1.0.0    Microsoft.PowerShell.Management
```

To count the number of cmdlets available we can pipe the output to the `Measure-Object` cmdlet and specify the `-Line` parameter.

```powershell
Get-Command *process | Measure-Object -Line
```

`output:`

```
Lines Words Characters Property
----- ----- ---------- --------
11
```

---

### 5. What cmdlet might you use to set to a PowerShell breakpoint? (Hint: PowerShell-specific nouns are often prefixed with PS.)

```powershell
PS C:\Labs> help *breakpoint
```

`output:`

```
Name                              Category  Module                    Synopsis
----                              --------  ------                    --------
Disable-PSBreakpoint              Cmdlet    Microsoft.PowerShell.U... Disables the breakpoints in the current console.
Enable-PSBreakpoint               Cmdlet    Microsoft.PowerShell.U... Enables the breakpoints in the current console.
Get-PSBreakpoint                  Cmdlet    Microsoft.PowerShell.U... Gets the breakpoints that are set in the current se...
Remove-PSBreakpoint               Cmdlet    Microsoft.PowerShell.U... Deletes breakpoints from the current console.
Set-PSBreakpoint                  Cmdlet    Microsoft.PowerShell.U... Sets a breakpoint on a line, command, or variable.
```

The command must be `Set-PSBreakpoint `

```powershell
PS C:\Labs> help Set-PSBreakpoint
```

`output:`

```
NAME
    Set-PSBreakpoint

SYNOPSIS
    Sets a breakpoint on a line, command, or variable.
```

---

### 6. You’ve learned that aliases are nicknames for cmdlets. What cmdlets are available to create, modify, export, or import aliases?

```powershell
Get-Command -Noun alias
```

`output:`

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Export-Alias                                       3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Get-Alias                                          3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Import-Alias                                       3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          New-Alias                                          3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Set-Alias                                          3.1.0.0    Microsoft.PowerShell.Utility
```

---

### 7. Is there a way to keep a transcript of everything you type in the shell, and save that transcript to a text file?

```powershell
Get-Command -noun  transcript
```

`output:`

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Start-Transcript                                   3.0.0.0    Microsoft.PowerShell.Host
Cmdlet          Stop-Transcript                                    3.0.0.0    Microsoft.PowerShell.Host
```

You can create a new transcript file named "transcript.txt" in the C:\ directory, and any commands you type in the PowerShell prompt will be saved to this file.

```powershell
Start-Transcript -Path C:\transcript.txt
```

When you're done, use the command `Stop-Transcript` to stop the transcript and save it to the file.

```powershell
Stop-Transcript
```

---

### 8. Getting all processes can be overwhelming. How can you get processes by the name of the process?

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> get-process -Name powershell
```

`output:`

```
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
   1039      61   193148     226600       8.59  24920   1 powershell_ise
```

---

### 9. Is there a way to tell Get-Process to tell you the user who started the process?

Finding out what command to use

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> help get-process -parameter *username*
```

`output:`

```
-IncludeUserName <System.Management.Automation.SwitchParameter>
    Indicates that the UserName value of the Process object is returned with results of the command.

    Required?                    true
    Position?                    named
    Default value                False
    Accept pipeline input?       False
    Accept wildcard characters?  false
```

Testing:

```powershell
get-process -Name powershell* -IncludeUserNam
```

`output:`

```
Handles      WS(K)   CPU(s)     Id UserName               ProcessName
-------      -----   ------     -- --------               -----------
    710      84100     0.75   6396 DEVMACHINE\rodri       powershell
    922     292496    26.66  24920 DEVMACHINE\rodri       powershell_ise
```

---

### 10. Is there a way to run a command on a remote host? (Hint: Invoke is the verb for running something now.)

```powershell
help Invoke-Command –Parameter computername
```

---

### 11. Examine the help file for the Out-File cmdlet. The files created by this cmdlet default to a width of how many characters? Is there a parameter that would enable you to change that width?

```powershell
Help Out-File –Parameter Width
```

`output:`

```

-Width <System.Int32>
    Specifies the number of characters in each line of output. Any additional characters are truncated, not wrapped. If this parameter is not used, the width is determined by the
    characteristics of the host. The default for the PowerShell console is 80 characters. If you want to control the width for all invocations of `Out-File` as well as the redirection
    operators (`>` and `>>`), set `$PSDefaultParameterValues['out-file:width'] = 2000` before using `Out-File`.

    Required?                    false
    Position?                    named
    Default value                None
    Accept pipeline input?       False
    Accept wildcard characters?  false
```

---

### 12. By default, Out-File overwrites any existing file that has the same filename as what you specify. Is there a parameter that would prevent the cmdlet from overwriting an existing file?

```powershell
Get-Process | Out-File -FilePath "C:\Processes.txt" -NoClobber

```

---

### 13. How could you see a list of all aliases defined in PowerShell?

```powershell
Get-Alias
```

---

### 14 . Using both an alias and abbreviated parameter names, what is the shortest command line you could type to retrieve a list of commands with the word process in the name?

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> Gcm -na *process*
```

`output:`

```

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           Start-ASRSwitchProcessServerJob                    0.2.4      AzureRM.RecoveryServices.SiteRecovery
Function        Get-AppvVirtualProcess                             1.0.0.0    AppvClient
Function        Start-AppvVirtualProcess                           1.0.0.0    AppvClient
Cmdlet          ConvertTo-ProcessMitigationPolicy                  1.0.12     ProcessMitigations
Cmdlet          Debug-Process                                      3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Enter-PSHostProcess                                3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Exit-PSHostProcess                                 3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Get-ComputeProcess                                 1.0.0.0    HostComputeService
Cmdlet          Get-Process                                        3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Get-ProcessMitigation                              1.0.12     ProcessMitigations
Cmdlet          Get-PSHostProcessInfo                              3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Get-VMProcessor                                    2.0.0.0    Hyper-V
Cmdlet          Set-ProcessMitigation                              1.0.12     ProcessMitigations
Cmdlet          Set-VMProcessor                                    2.0.0.0    Hyper-V
Cmdlet          Start-AzureRmRecoveryServicesAsrSwitchProcessSe... 0.2.4      AzureRM.RecoveryServices.SiteRecovery
Cmdlet          Start-Process                                      3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Stop-ComputeProcess                                1.0.0.0    HostComputeService
Cmdlet          Stop-Process                                       3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Wait-Process                                       3.1.0.0    Microsoft.PowerShell.Management
Application     qprocess.exe                                       10.0.19... C:\Windows\system32\qprocess.exe
```

---

### 15. How many cmdlets are available that can deal with generic objects? (Hint: Remember to use a singular noun like object rather than a plural one like objects.)

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> Get-Command –Noun object
```

`output:`

```

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Compare-Object                                     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          ForEach-Object                                     3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Group-Object                                       3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Measure-Object                                     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          New-Object                                         3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Select-Object                                      3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Sort-Object                                        3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object                                         3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Where-Object                                       3.0.0.0    Microsoft.PowerShell.Core
```

---

### 16. This chapter briefly mentioned arrays. What help topic could tell you more about them?

```powershell
help *array*
```

---
