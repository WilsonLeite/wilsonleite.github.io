# PowerShell

## Products

There are two similar products with similar names. However, not all commands are available in both products and some commands can have different parameters, causing different behaviors.

### Windows PowerShell

This is the older version of the product and typically ships with Windows. It is based on .Net Framework. It can be run from the Start Menu, Windows Terminal, and Command Prompt by invoking _PowerShell.exe_.

This version runs only on Windows and supports more Windows specific commands or parameters. 

The latest (and final) version is 5.1:

``` PowerShell
> $PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.19041.3693

``` 

Microsoft still supports it, but it is no longer improving it.

### PowerShell

This is the new version based on .Net Core. It runs on Windows, Linux, and Mac. It is based on .Net Core - Nowadays just called _.Net_. 

It typically does not come installed on Windows. There are several ways to install it, but one of the simpler ways to install it on Windows is:

``` PowerShell
winget install --id Microsoft.PowerShell
``` 

Once installed, it can be run from the Start Menu, Windows Terminal, and Command Prompt by invoking _pwsh.exe_.

This product (at the time of this writing) is under active development.

## Invoking commands

PowerShell command naming convention is _Verb_-_Noun_. For example:

``` PowerShell
Get-Date
``` 

Parameters follow the -_name_ _value_ pattern:

``` PowerShell
Get-Process -Name powershell -ComputerName myComputer
``` 

Parameters of the _switch_ type don't receive values:

``` PowerShell
Get-Process -FileVersionInfo
``` 

Some parameters accept an array. They are comma-separated values:

``` PowerShell
Get-Process -Name powershell,cmd
``` 

Some parameters are positional, so their name can be omitted:

``` PowerShell
Get-Process powershell
``` 

<< See more examples below >>

## Aliases

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

## Command results

Typically a set of objects.

* Get-Member

## Writing and reading files

Out-File
Export-Csv

## Exploring commands

* Get-Command
* Get-Help

## Filtering

* Select-Object
* Where-Object

## Formating

* Format-Table
* Format-List
* Out-GridView

## Using pipes

* Basic Usage
* $_.*
* << see common parameters >> 
    * using different names, preserving results after multiple pipes


### Multiple-lines commands

The line-break after the pipe will allow continuing the command in the next line

``` PowerShell
$data = Get-Service |
where-Object Status -eq 'Stopped' |
select-object Name,Status

$data | out-file .\services.txt
$data | export-csv .\services.csv

# Load the file content and dump it in the console
get-content .\services.csv

$importData = import-csv -Path .\services.csv

```

## Variables


## Sequential Scripts

* Write-Output
* Write-Host
* Write-Debug

## Conditional logic

## Functions

## Classes

## Desired state

<!--
### Notes

Get-Help about_CommonParameters

winget

Windows Sandbox

PowerShell for Linq users

-->
