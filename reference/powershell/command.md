# PowerShell - Commands

## Invoking commands

PowerShell command naming convention is _Verb_-_Noun_. For example:

```powershell
PS C:\> Get-Date
``` 

Parameters follow the -_name_ _value_ pattern:

```powershell
PS C:\> Get-Process -Name powershell -ComputerName myComputer
``` 

Some parameters are positional, so their name can be omitted:

```powershell
PS C:\> Get-Process powershell
``` 

Parameters of the _switch_ type don't receive values:

```powershell
PS C:\> Get-Process -FileVersionInfo
``` 

Text parameters can be wrapped in single quotes:

```powershell
PS C:\> Get-ChildItem 'C:\Program Files\'
``` 

Double quotes expand variable values:

```powershell
PS C:\Windows\System32> echo "The current directory is $PWD"
The current directory is C:\Windows\System32
``` 

Some parameters accept an [array](./variable.md#arrays). They are comma-separated values:

```powershell
PS C:\> Get-Process -Name powershell,cmd , explorer
``` 

It is possible to use [hash tables](./type.md) to provide values to commands. Note the @ prefix:

```powershell
PS C:\> $params = @{ Name = "Get-*"; CommandType = "Function"}
PS C:\> Get-Command @params
``` 

## Exploring commands

Find commands and applications:

```powershell
PS C:\> Get-Command *process

PS C:\> Get-Command notepad
``` 

Get help on commands:

```powershell
PS C:\> Get-Help Get-Process

PS C:\> Get-Help Get-Process -Full

PS C:\> Get-Help Get-Process -Detailed

PS C:\> Get-Help Get-Process -Examples

PS C:\> Get-Help Get-Process -Online

# Requires be running on the Windows graphic interface
PS C:\> Get-Help Get-Process -ShowWindow
``` 

See also:
* Concatenating commands using [pipes](./pipe.md).
