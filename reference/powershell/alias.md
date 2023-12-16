# PowerShell - Aliases

PowerShell support command aliases - they provide a short version of the command name that does not follow the format convention. For example, echo is an alias for Write-Output:

``` PowerShell
echo Hello!

Write-Output Hello!
``` 

We can list the current aliases by using the _alias_ command, that is itself an alias for the _Get-Alias_ command.

``` PowerShell
alias

Get-Alias
``` 

We can filter the aliases by Name (default) or Definition. We can also use wildcards:

``` PowerShell
> alias -Name cd
> alias cd

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           cd -> Set-Location


> alias *dir

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           chdir -> Set-Location
Alias           dir -> Get-ChildItem
Alias           rmdir -> Remove-Item

> alias -Definition *alias

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           epal -> Export-Alias
Alias           gal -> Get-Alias
Alias           nal -> New-Alias
Alias           sal -> Set-Alias

``` 

<< How is alias mapped to get-alias? >>
<< Create another page for alias management, including scopes >>

The commands can also have an implicit alias. For example, in Windows PowerShell Import-Module can be invoked as ipmo.
