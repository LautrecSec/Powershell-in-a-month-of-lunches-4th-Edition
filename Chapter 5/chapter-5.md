# 5.6 Lab

### 1. Create a new directory called Labs

```powershell
PS C:\Users\rodri.LAPTOP-UTLDGGR2> New-Item -Path c:\Labs -ItemType Directory
```

---

### 2. Create a zero-length file named /Labs/Test.txt (use New-Item).

```powershell
PS C:\Labs> New-Item -Path C:\Labs -Name test.txt -ItemType file
```

---

### 3. Is it possible to use Set-Item to change the contents of /Labs/Test.txt to -TESTING? Or do you get an error? If you get an error, why?

It's not supported by the FileSystem

---

### 4. Using the Environment provider, display the value of the system environment variable PATH.

```powershell
PS C:\Labs> Get-Item env:PATH
```

`output:`

```

Name                           Value
----                           -----
Path                           C:\Program Files (x86)\VMware\VMware Player\bin\;C:\Python310\Scripts\;C:\Python310\;C:\Program Files\Microsoft\jdk-11.0.12.7-hotspot\bin;C:\Windows\system3...
```

---

### 5. Use help to determine what the differences are between the -Filter, -Include, and -Exclude parameters of Get-ChildItem.

Getting the full documentation for Get-ChildItem

```powershell
get-help Get-ChildItem -Detailed
```

`-Filter:`Is applied before the command retrieves the items.  
`-Include:`Specifies the items to include in the output. Is applied after the command retrieves the items.  
`-Include:`Specifies the items to exclude from output.