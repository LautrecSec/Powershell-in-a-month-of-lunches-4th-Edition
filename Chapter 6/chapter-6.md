# 6.7 Lab

### 1. Create two similar, but different, text files. Try comparing them by using `Compare-Object`. </br>Run something like this: `Compare-Object -Reference (Get-Content File1.txt) -Difference (Get-Content File2.txt)`. </br>If the files have only one line of text that’s different, the command should work.

```powershell
PS C:\Labs> "file number 1" | out-file MyFile1.txt
PS C:\Labs> "file number 2" | out-file MyFile2.txt
PS C:\Labs> Compare-Object .\MyFile1.txt .\MyFile2.txt
```

`output:`

```

InputObject   SideIndicator
-----------   -------------
.\MyFile2.txt =>
.\MyFile1.txt <=
```

---

### 2. What happens if you run Get-Command | Export-CSV commands.CSV | Out-File from the console? Why does that happen?

```powershell
PS C:\Labs> New-Item -Path C:\Labs -Name test.txt -ItemType file
```

`output:`

```

Out-File : Cannot process argument because the value of argument "path" is null. Change the value of argument "path" to a
non-null value.
At line:1 char:41
+ Get-Command | Export-CSV commands.CSV | Out-File
+                                         ~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Out-File], PSArgumentNullException
    + FullyQualifiedErrorId : ArgumentNull,Microsoft.PowerShell.Commands.OutFileCommand
```

---

### 3. Apart from getting one or more jobs and piping them to Stop-Job, what other means does Stop-Job provide for you </br>to specify the job or jobs you want to stop? Is it possible to stop a job without using Get-Job at all?

```powershell
PS Stop-job Name
```

---

### 4. What if you want to create a pipe-delimited file instead of a CSV file? You’d still use the Export-CSV command, but what parameters would you specify?

```powershell
PS C:\Labs> get-process| Export-CSV process.CSV -Delimiter "|"
```

---

### 5. How do you include the type information in the # comment line at the top of an exported CSV file?

</br>
It doesn't work in PS 5.1

```powershell
PS C:\Labs> Get-Process | Export-Csv processDetails.csv  -IncludeTypeInformation
```

---

### 6. Export-Clixml and Export-CSV both modify the system because they can create and overwrite files. </br> What parameter would prevent them from overwriting an existing file? </br> What parameter would ask whether you were sure before proceeding to write the output file?

&nbsp;

You can use the `Compare-Object` parameter. This parameter prevents the cmdlets from overwriting an existing file with the same name as the output file.
</br>If the file already exists, the cmdlets will generate an error message instead of overwriting the file.

```powershell
PS C:\Labs> Get-Process | Export-Csv process.csv -NoClobber
```

&nbsp;
Note that the -Confirm parameter is not available for `Export-Clixml`. However, you can use the `-WhatIf` parameter instead.

---

### 7. The operating system maintains several regional settings, which include a default list separator. </br> On US systems, that separator is a comma. How can you tell Export-CSV to use the system’s default separator rather than a comma?

```powershell
PS C:\Labs> Get-Process | Export-Csv process.csv  -UseCulture
```
