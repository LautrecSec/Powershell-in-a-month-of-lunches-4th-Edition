# 11.11 Lab

## 1. Display a table of processes that includes only the process names, IDs, and whether they’re responding to Windows (the Responding property has that information). Have the table take up as little horizontal room as possible, but don’t allow any information to be truncated.

```powershell
PS C:\Labs> Get-Process | Format-Table Name,ID,Responding -Wrap
```

`output:`

````
Name                               Id Responding
----                               -- ----------
ApplicationFrameHost            14120       True
AsusAppService                  21936       True
AsusLinkNear                      528       True
AsusLinkRemote                  15936       True
AsusOptimization                21988       True
AsusOptimizationStartupTask     19584
```powerShell
PS C:\Labs> Get-Process | Format-Table Name,ID, @{name='Virtual';e={$_.vm/1MB}}, @{name='Physical';e={$_.workingset/1MB}}
```      True
````

---

## 2. Display a table of processes that includes the process names and IDs. Also include columns for virtual and physical memory usage, expressing those values in megabytes (MB).

```powerShell
PS C:\Labs> Get-Process | Format-Table Name,ID, @{name='Virtual';e={$_.vm/1MB}}, @{name='Physical';e={$_.workingset/1MB}}
```

`output:`

```
Name                               Id    Virtual Physical
----                               --    ------- --------
ApplicationFrameHost            14120 2101491.73    37.14
AsusAppService                  21936    4245.43    22.29
AsusLinkNear                      528 2101363.05    16.69
AsusLinkRemote                  15936      58.90    12.28
```

---

## 3. Use `Get-Module` to get a list of loaded modules. Format the output as a table that includes, in this order, the module name and the version. The column headers must be ModuleName and ModuleVersion.

```powershell
PS C:\Labs> get-module | format-table @{name='ModuleName';expression={$_.name}},@{name='ModuleVersion';expression={$_.Version}}
```

`output:`

```
ModuleName                            ModuleVersion
----------                            -------------
az                                    9.4.0
Az.Accounts                           2.11.2
Az.Advisor                            2.0.0
Az.Aks                                5.3.0
Az.AnalysisServices                   1.1.4
```

---

## 4. Use `Get-AzStorageAccount` and `Get-AzStorageContainer` to display all of your storage containers so that a separate table is displayed for storage containers that are accessible to the public and storage containers that are not. (Hint: Piping is your friend . . . use a `-GroupBy` parameter.)

```powershell
PS C:\Labs> Get-AzStorageAccount | Get-AzStorageContainer | Format-Table -GroupBy PublicAccess
```

---

## 5 . Display a four-column-wide list of all directories in the home directory.

```powershell
PS C:\Labs> Get-ChildItem | Format-wide -Column 4
```

`output:`

```
 Directory: C:\Labs

TestFolder                                              20                                                     allfiles.html                                          credscan.json
credscan.yml                                            listFiles.csv                                          listFiles.html                                         password.xml
process.csv                                             process.html                                           processDetails.csv                                     ps.txt
testing.ps1
```

---

## 6. Create a formatted list of all .dll files in `$pshome`, displaying the name, version information, and file size. PowerShell uses the `Length` property, but to make it clearer, your output should show `Size`

```powershell
PS C:\Labs> Get-ChildItem $pshome/*.dll | Format-List Name,VersionInfo,@{Name="Size";Expression={$_.length}}
```

`output:`

```
Name        : msquic.dll
VersionInfo : File:             C:\Program Files\PowerShell\7\msquic.dll
              InternalName:     msquic
              OriginalFilename: msquic.dll
              FileVersion:      2.1.1.293818
              FileDescription:  Microsoft® QUIC Library
              Product:          Microsoft® QUIC
              ProductVersion:   2.1.1.293818-official
              Debug:            False
              Patched:          False
              PreRelease:       False
              PrivateBuild:     False
              SpecialBuild:     False
              Language:         English (United States)

Size        : 534416
```
