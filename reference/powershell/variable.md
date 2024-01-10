# PowerShell - Variables

Variables in PowerShell are declared and used with a $ prefix:

``` PowerShell
$myValue = 123

echo $myValue
```

By default, variables are loosely typed. That means that they can receive a value of any [type](./type.md):

``` PowerShell
$myValue = 123
$myValue = "banana"
$myValue = 7..10
```

We can assign a _null_ value:
``` PowerShell
$myValue = $null
```

However, a variable can be declared using the _cast notation_: It constrains the variable type so values will always be converted to that type (or fail):

``` PowerShell
[int]$number = 8
$number = 1.8  # The floating number will be rounded to 2
$number = "12345"  # The string is converted to an integer.
$number = "Hello"  # Fail
```

Note that assigning $null to a numeric value will cast it to 0:

``` PowerShell
> [int]$number = 8
> $number = $null
> $number
0
```

We can assign items in an array to several variables at once:

``` PowerShell
# Maps 1 to 1
$a, $b, $c = 1, 2, 3

# $c receives an array with the last 3 values
$a, $b, $c = 1, 2, 3, 4, 5

# $c receives $null
$a, $b, $c = 1, 2
``` 

Use _Get-Variable_ to list the variables in the current context:

``` PowerShell
Get-Variable

Get-Variable my*
```
Note that both the parameter and the result variables don't use the _$_ prefix.

## Environment variables

They are always non-empty strings and are stored in the _$Env_ special variable. Assigning _$null_ or an empty string removes them.

### The Variable Syntax

The syntax to access them is $Env:_name_ like:

``` PowerShell
$Env:Path
```

### The Drive format

This format access the repository in a way similar to a drive:

``` PowerShell
# List all the environment variables
dir Env:

# Show the content of the HOMEDRIVE variable
dir Env:\HOMEDRIVE

Name                           Value
----                           -----
HOMEDRIVE                      C:
```

Other Item-oriented commands work as well:

``` PowerShell
Copy-Item -Path Env:\Foo -Destination Env:\Foo2 -PassThru
Set-Item -Path Env:\Foo2 -Value 'BAR'
Get-Item -Path Env:\Foo*
Remove-Item -Path Env:\Foo* -Verbose
```

### .NET Environment object

``` PowerShell
[Environment]::SetEnvironmentVariable('Foo', 'Bar', [System.EnvironmentVariableTarget]::User)
[Environment]::SetEnvironmentVariable('Foo','Bar', 'Machine')
[Environment]::GetEnvironmentVariable('Foo')
```
