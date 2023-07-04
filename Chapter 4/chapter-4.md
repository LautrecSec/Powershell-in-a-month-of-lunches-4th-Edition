# 4.10 Lab

### 1. Display a list of running processes.

```powershell
PS> Get-Process
```

---

### 2.Test the connection to google.com or bing.com without using an external command like ping.

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> Test-Connection google.com

```

`output:`

```
Source        Destination     IPV4Address      IPV6Address                              Bytes    Time(ms)
------        -----------     -----------      -----------                              -----    --------
DEVMACHINE    google.com      172.217.24.46                                             32       28
DEVMACHINE    google.com      172.217.24.46                                             32       31
DEVMACHINE    google.com      172.217.24.46                                             32       28
DEVMACHINE    google.com      172.217.24.46                                             32       29
```

---

### 3. Display a list of all commands that are of the cmdlet type. (This is tricky—we’ve shown you Get-Command, but you need to read the help to find out how to narrow down the list as we’ve asked.)

```powershell
Get-Command -Type cmdlet
```

---

### 4. Display a list of all aliases.

```powershell
Get-Alias
```

---

### 5. Make a new alias, so you can run ntst to run netstat from a PowerShell prompt

```powershell
New-Alias -Name ntst -Value netstat
```

---

### 6. Display a list of processes that begin with the letter p. Again, read the help for the necessary command—and don’t forget that the asterisk (\*) is a near-universal wildcard in PowerShell.

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> Get-Process -Name p*
```

`output:`

```
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName
-------  ------    -----      -----     ------     --  -- -----------
    890      68   367608     397508      97.48  24920   1 powershell_ise
    736      38    11592      17236      39.09   6448   1 PowerToys
    219      12    18728       1880      72.44   8916   1 PowerToys.AlwaysOnTop
    795      40    23092       4968      17.66   8924   1 PowerToys.Awake
    496      62    71920      19264      47.75   8960   1 PowerToys.ColorPickerUI
    303      20   157476       5900   1,773.30   8988   1 PowerToys.FancyZones
    143       9    16208       1032       3.34   9012   1 PowerToys.KeyboardManagerEngine
   1133     107   163628      20032      89.41   9052   1 PowerToys.PowerLauncher
    236      28    25724      13772              6892   0 PresentationFontCache
```

---

### 7. Make a new folder (aka directory) using the New-Item cmdlet with the name of MyFolder1. Then do it again and call it MyFolder2. Use Help if you’re not familiar with New-Item.

Creating a new folder call Myfolder1.

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> New-Item -Name Myfolder1 -Path c:\PowerShell -ItemType Directory
```

`output:`

```
 Directory: C:\PowerShell


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        21/02/2023   6:57 am                Myfolder1
```

Creating a directory called Myfolder2

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> New-Item -Name Myfolder2 -Path c:\PowerShell -ItemType Directory
```

`output:`

```
 Directory: C:\PowerShell


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        21/02/2023   6:59 am                Myfolder2
```

---

### 8. Remove the folders from step 7 in a single command. Use Get-Command to find a similar cmdlet to what we used in step 7. and don’t forget that the asterisk (\*) is a near-universal wildcard in PowerShell.

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> Remove-Item C:\PowerShell\*.*
```
