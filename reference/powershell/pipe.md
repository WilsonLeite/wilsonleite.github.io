# PowerShell - Pipes

## Using pipes

* Basic Usage
* $_.*
* << see common parameters >> 
    * using different names, preserving results after multiple pipes

* Get-Member?

## Filtering

* Select-Object
* Where-Object

<< group >>

## Formating

* Format-Table
* Format-List
* Out-GridView



* Get-Member?

### PassThru

The _-PassThru_ option retuns a value that otherwise would not be returned:

<< Pipes, parameter arrays, hash parameters >>
<< See more examples below >>

### Command results

Typically a set of objects.

* Get-Member

### Multiple-lines

The line-break after the pipe will allow continuing the command in the next line

```powershell
$data = Get-Service |
where-Object Status -eq 'Stopped' |
select-object Name,Status

$data | out-file .\services.txt
$data | export-csv .\services.csv

# Load the file content and dump it in the console
get-content .\services.csv

$importData = import-csv -Path .\services.csv

```


