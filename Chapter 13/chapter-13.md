# 13.10 Lab
## 1. Make a one-to-one connection with a remote computer (or with localhost if you have only one computer). Launch your favorite text editor. What happens?
---
## 2. Using `Invoke-ScriptBlock`, retrieve a list of processes currently running from one or two remote computers (it’s okay to use `localhost` twice if you have only one computer). Format the results as a wide list. (Hint: It’s okay to retrieve results and have the formatting occur on your computer—don’t include the `Format-` cmdlets in the commands that are invoked remotely.)
---
## 3. Use `Invoke-ScriptBlock` to get a list of the top 10 processes for virtual memory (VM) usage. Target one or two remote computers, if you can; if you have only one computer, target `localhost` twice.
---
## 4. Create a text file that contains three computer names, with one name per line. It’s okay to use the same computer name, or `localhost`, three times if you have access to only one computer. Then use `Invoke-ScriptBlock` to retrieve the 10 newest files from the home directory (~).
---
## 5. Using `Invoke-ScriptBlock`, query one or more remote computers to display the property `PSVersion` from the `$PSVersionTable` variable. (Hint: This requires you to get the property of an item.)
