# 8.10 Lab

### 1. Identify a cmdlet that produces a random number.

</br>Finding out the command.

```powershell
PS C:\Labs> Get-Command *random*
```

`output`

```
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Cmdlet          Get-Random                                         7.0.0.0    Microsoft.PowerShell.Utility
```

```powershell
PS C:\Labs> Get-Random
```

`output`

```
1973906388
```

---

### 2. Identify a cmdlet that displays the current date and time.

</br>
Finding out the command.

```powershell
PS C:\Labs> Get-Command  -Verb get -Noun *date*
```

`output:`

```

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-WindowsUpdateLog                               1.0.0.0    WindowsUpdate
Cmdlet          Get-Date                                           7.0.0.0    Microsoft.PowerShell.Utility
```

```powershell
PS C:\Labs> Get-Date
```

`output`

```
Thursday, 2 March 2023 10:38:25 pm
```

---

### 3. What type of object does the cmdlet from task 2 produce? (What is the TypeName of the object produced by the cmdlet?)

```powershell
PS C:\Labs> Get-Date | gm
```

`output`

```
TypeName: System.DateTime

Name                 MemberType     Definition
----                 ----------     ----------
Add                  Method         datetime Add(timespan value)
```

---

### 4. Using the cmdlet from task 2 and Select-Object, display only the current day of the week in a table like the following (caution: the output will right-align, so make sure your PowerShell window doesn’t have a horizontal scrollbar):

```
DayOfWeek
---------
   Monday
```

Find out the object property that we can use

```powershell
PS C:\Labs> Get-Date | Get-Member -Name *week*
```

`output:`

```
TypeName: System.DateTime

Name      MemberType Definition
----      ---------- ----------
DayOfWeek Property   System.DayOfWeek DayOfWeek {get;}
```

```powershell
PS C:\Labs> Get-Date | select DayOfWeek
```

`output:`

```
DayOfWeek
---------
 Thursday
```

---

### 5. Identify a cmdlet that will show you all the times in a directory.

```powershell
PS C:\Labs> Get-ChildItem | Sort-Object CreationTime | Select-Object Name,CreationTime
```

`output:`

```
Name               CreationTime
----               ------------
testing.ps1        26/02/2023 7:24:45 am
TestFolder         27/02/2023 12:49:06 am
processDetails.csv 27/02/2023 12:53:11 am
process.csv        27/02/2023 12:53:21 am
process.html       2/03/2023 9:31:12 pm
20                 2/03/2023 10:01:24 pm
```

---

### 6. Using the cmdlet from task 5, display all the times in the directory of your choice. Then extend the expression to sort the list by the time the items were created and display only the filename(s) and the date created. Remember that the column headers shown in a command’s default output aren’t necessarily the real property names—you need to look up the real property names to be sure.

```powershell
PS C:\Labs> Get-ChildItem | select Name, CreationTime | sort-Object CreationTime -Descending 
```

`output:`

```
Name               CreationTime
----               ------------
20                 2/03/2023 10:01:24 pm
process.html       2/03/2023 9:31:12 pm
process.csv        27/02/2023 12:53:21 am
processDetails.csv 27/02/2023 12:53:11 am
TestFolder         27/02/2023 12:49:06 am
testing.ps1        26/02/2023 7:24:45 am
```

---

### 7. Repeat task 6, but this time sort the items by the last write time; then display the filename, creation time, and the last write time. Save this in a CSV file and an HTML file.

```powershell
PS C:\Labs>  Get-ChildItem | select  Name,LastWritetime,CreationTime | sort-Object CreationTime -Descending | Out-File listFiles.html
```

```powershell
PS C:\Labs> Get-ChildItem | select  Name,LastWritetime,CreationTime | sort-Object CreationTime -Descending | export-CSV listFiles.csv
```
