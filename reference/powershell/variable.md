# PowerShell - Variables (I)

Variables in PowerShell are declared and used with a $ prefix:

```powershell
PS C:\> $myValue = 123

PS C:\> echo $myValue
123
```

By default, variables are loosely typed. That means that they can receive a value of any [type](./type.md):

```powershell
PS C:\> $myValue = 123
PS C:\> $myValue = "banana"
PS C:\> $myValue = 7..10
```

We can assign a _null_ value:
```powershell
PS C:\> $myValue = $null
```

We can assign items from an [array](./type.md#Array) into several variables at once:

```powershell
# Maps 1 to 1
PS C:\> $a, $b, $c = 1, 2, 3

# $c receives an array with the last 3 values
PS C:\> $a, $b, $c = 1, 2, 3, 4, 5

# $c receives $null
PS C:\> $a, $b, $c = 1, 2
``` 

Use _Get-Variable_ to list the variables in the current context:

```powershell
PS C:\> Get-Variable

PS C:\> Get-Variable my*
```
Note that both the parameter and the result variables don't use the _$_ prefix.

## Environment variables

They are always non-empty strings and are stored in the _$Env_ special variable. Assigning _$null_ or an empty string removes them.

### The Variable Syntax

The syntax to access them is $Env:_name_ like:

```powershell
PS C:\> $Env:Path
```

### The Drive format

This format access the repository in a way similar to a drive:

```powershell
# List all the environment variables
PS C:\> Get-ChildItem Env:

# Using the dir alias
PS C:\> dir Env:

# Show the content of the HOMEDRIVE variable
PS C:\> dir Env:\HOMEDRIVE

Name                           Value
----                           -----
HOMEDRIVE                      C:
```

Other *-Item commands work as well:

```powershell
PS C:\> Copy-Item -Path Env:\Foo -Destination Env:\Foo2 -PassThru
PS C:\> Set-Item -Path Env:\Foo2 -Value 'BAR'
PS C:\> Get-Item -Path Env:\Foo*
PS C:\> Remove-Item -Path Env:\Foo* -Verbose
```

### .NET Environment object

```powershell
[Environment]::SetEnvironmentVariable('Foo', 'Bar', [System.EnvironmentVariableTarget]::User)
[Environment]::SetEnvironmentVariable('Foo','Bar', 'Machine')
[Environment]::GetEnvironmentVariable('Foo')
```
