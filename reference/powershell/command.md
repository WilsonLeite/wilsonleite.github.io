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

## Exploring commands

* Get-Command
* Get-Help



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

