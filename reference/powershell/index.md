# PowerShell

## Invoking commands

PowerShell command naming convention is _Verb_-_Noun_. For example:

``` PowerShell
Get-Date
``` 

### Aliases

PowerShell support command aliases - they provide a short version of the command name that does not follow the format convention. For example, echo is an alias for Write-Output:

``` PowerShell
echo Hello!

Write-Output Hello!
``` 
<< Where do they come from? How are they stored? Can we manage them? Can they be local to the current session? >>

We can list the current aliases by using the _alias_ command, that is itself an alias for the _Get-Alias_ command.

``` PowerShell
alias

Get-Alias
``` 

The commands can also have an implicit alias. For example, in Windows PowerShell Import-Module can be invoked as ipmo.


``` PowerShell

``` 


Command line

The line-break after the pipe will allow continuing the command in the next line
<< why? >>

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





<!--
### Notes

Get-Help about_CommonParameters

winget

Windows Sandbox

PowerShell for Linq users

-->
