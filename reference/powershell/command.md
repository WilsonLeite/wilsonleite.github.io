# PowerShell - Commands

## Invoking commands

PowerShell command naming convention is _Verb_-_Noun_. For example:

``` PowerShell
Get-Date
``` 

Parameters follow the -_name_ _value_ pattern:

``` PowerShell
Get-Process -Name powershell -ComputerName myComputer
``` 

Some parameters are positional, so their name can be omitted:

``` PowerShell
Get-Process powershell
``` 

Parameters of the _switch_ type don't receive values:

``` PowerShell
Get-Process -FileVersionInfo
``` 

Text parameters can be wrapped in single quotes:

``` PowerShell
Get-ChildItem 'C:\Program Files\'
``` 

Double quotes expand variable values:

``` PowerShell
PS C:\Windows\System32> echo "The current directory is $PWD"
The current directory is C:\Windows\System32
``` 

Some parameters accept an [array](./variable.md#arrays). They are comma-separated values:

``` PowerShell
Get-Process -Name powershell,cmd , explorer
``` 

It is possible to use [hash tables](./type.md) to provide values to commands. Note the @ prefix:

``` PowerShell
$params = @{ Name = "Get-*"; CommandType = "Function"}
Get-Command @params
``` 

## Exploring commands

Find commands and applications:

``` PowerShell
Get-Command *process

Get-Command notepad
``` 

Get help on commands:

``` PowerShell
Get-Help Get-Process

Get-Help Get-Process -Full

Get-Help Get-Process -Detailed

Get-Help Get-Process -Examples

Get-Help Get-Process -Online

# Requires be running on the Windows graphic interface
Get-Help Get-Process -ShowWindow
``` 

``` PowerShell
``` 

``` PowerShell
``` 



* Get-Member?



<< Pipes, parameter arrays, hash parameters >>
<< See more examples below >>

### Command results

Typically a set of objects.

* Get-Member

### Multiple-lines

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

