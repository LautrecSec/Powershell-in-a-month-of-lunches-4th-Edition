# 10.9 Lab

<p>
Once again, we’ve covered a lot of important concepts in a short amount of time. 
The best way to cement your new knowledge is to put it to immediate use.
We recommend doing the following tasks in order, 
because they build on each other to help remind you what you’ve learned and to help you find practical ways to use that knowledge.
</p>
<p>
To make this a bit trickier, we’re going to force you to consider how to use the Az.Accounts module (which is included in the Az module we installed in section 10.6). This should work on any macOS or Ubuntu machine:
</p>

- The `Get-AzSubscription` command has the `-SubscriptionName` parameter; running `Get-AzSubscription -SubscriptionName MySubscriptionName` retrieves the subscription with the name MySubscriptionName from your account.
- The `Selecet-AZSubscription` command has the `-Subscription` parameter; running `Select-AzSubscription -Subscription MySubscriptionName` sets the subscription in the context that most commands in the Az.\* module use to determine the subscription to use.
- The `Get-AzContext` command can be used to determine which subscription is selected.

## 1. Would the following command work to retrieve a list of commands from modules that start with Microsoft.\* on the current machine? Why or why not? Write an explanation, similar to the ones we provided earlier in this chapter.

```powerShell
Get-Command -Module (Get-Module -ListAvailable -Name Microsoft.* |
Select-Object -ExpandProperty name)
```

Yes, it works:

`Get-Module -ListAvailable -Name Microsoft._`: This command gets a list of all available modules whose names start with `"Microsoft._"`.

`Select-Object -ExpandProperty name`: This command selects only the name property of the modules returned by the previous command and expands the results into a single list of strings.

The result of step 2 is then piped as input to `Get-Command` which retrieves all the commands available in the modules passed to it.

So, in summary, the command first retrieves a list of modules whose names start with `"Microsoft.\*"`, selects the name property of each module and expands the results into a single list of strings.

Finally, it retrieves all the commands available in the selected modules using Get-Command.

---

## 2. Would this alternative command work to retrieve the list of commands from the same modules? Why or why not? Write an explanation, similar to the ones we provided earlier in this chapter.

```powerShell
Get-Module -ListAvailable -Name Microsoft.* | Get-Command
```

No, it doesn't work:

`Get-module` is producing objects of the type `ModuleInfoGrouping` and `Get-command` needs a type of System.String

## 3. Would this set the subscription in the Azure context? Consider if `Get- AzSubcription` retrieves multiple subscriptions.

```powershell
Get-AzSubscription | Select-AzSubscription
```

It seems working. As I have 3 subscriptions it's selecting the last one.
If I run `Get-AzContext` I can see that selected the last subscription.

---

## 4. Write a command that uses pipeline parameter binding to retrieve the first subscription and set that in the Azure context. Don’t use parentheses.

```powershell
PS C:\Labs> Get-AzSubscription | Select-Object -First 1 | Set-AzContext
```

---

## 5. Write a command that uses pipeline parameter binding to retrieve the first subscription and set that in the Azure context. Don’t use pipeline input; instead, use a parenthetical command (a command in parentheses).

```powershell
PS C:\Labs> Set-AzContext (Get-AzSubscription | Select-Object -First 1)
```

---

## 6. Sometimes someone forgets to add a pipeline parameter binding to a cmdlet. For example, would the following command work to set the subscription in the Azure context? Write an explanation, similar to the ones we provided earlier in this chapter.

```
'mySubscriptionName' | Select-AzSubscription
```

It doesn't work because `Select-AzSubscription` cmdlet expects an object of type `Microsoft.Azure.Commands.Profile.Models.PSAzureSubscription` as input, rather than a string value.
