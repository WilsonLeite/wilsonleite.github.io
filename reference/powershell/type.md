# Types - PowerShell

## Basic types

```powershell
# 32 bits signed integer => int => Int32
$myIntegerValue = 8
# 64 bits floating point => Double
$myDoubleValue = 5.5
# Text => String
$string = "12345"
$string = '67890'

#Floating Point
$fp = 10.6

# Decimal
$dec = 10.6D

# Boolean
$isTwoGreaterThanOne = 2 -gt 1
$yesPlease = $true
$noWay = $false

# Null value
$valueNotAssigned = $null
```

### Explicit types

We can cast a value to a specific type:

```powershell
$val = [Decimal]15.8
```

* Signed integers: [Byte], [Int16], [Int32], [Int64]. [Int] = Int32, [Long] = Int64
* Unsigned integers: [UInt16], [UInt32], [UInt64]
* Floating point: [Single], [Double], [Float] = Single
* Fixed point: [Decimal]

The Decimal type is 128 bits long and is represented internally as an integer and a scale = power of ten. For example, 1.50 = 15 * 10 ^ -1. This approach prevents rounding errors that may happen when using floting point numbers.

## Array

Arrays are a contiguous set of elements of a length defined when it is created. By default, the elements of an array are of _object_ type so they can have any value.

```powershell
$oneDimensionArray = "Hello", 42, $true

# Equivalent
$oneDimensionArray = New-Object 'object[]' 3
$oneDimensionArray[0] = "Hello"
$oneDimensionArray[1] = 42
$oneDimensionArray[2] = $true

# ERROR: Index is outside the bounds of the array
$oneDimensionArray[3] = "Something else"

# Array expression => @()

$oneDimensionArray = @("Hello", 42, $true)
$allRunningProcesses = @( Get-Process )

$arr = ,42 # only one element

# Range

$threeToFive = 3..5 # equivalent to 3,4,5

$fiveToThree = 5..3 # Descending

$max = 27
$everything = 1..$max
```

Multidimensional arrays:

```powershell
$bidimensionalArray = New-Object 'object[,]' 2,2
$bidimensionalArray[0,0] = "Hello"
$bidimensionalArray[0,1] = 42
$bidimensionalArray[1,0] = $true
```

Constrained types:

```powershell
$oneDimensionArray = [object[]]("Hello", 42, $true) # Object is the default type

$integerArray = [int[]](4, 8, 15, 16, 23, 42)

# Casting an array of objects into an array of integers

$integerArray = [int[]](0x4, "8", "0xF", 15.8D, 23.3, 42)

```

Concatenation:

```powershell
# Concatenating two arrays always results in a new array that is unconstrained even if both arrays are constrained by the same type

$arr = @(1..3) + @(4..7)

$arr += $(8..10)
```

## Hash Table

The Hashtable represents a collection of key/value pair objects.

```powershell
$h1 = @{ FirstName = "James"; LastName = "Anderson"; IDNum = 123 }

$h1.FirstName # designates the key FirstName
$h1["LastName"] # designates the associated value for key LastName

# The order of the Key/Value pairs is not guaranteed
# But the order of all Keys matches the order of all Values
$h1.Keys # gets the collection of keys
$h1.Values # gets the collection of values
$h1.Count # 3

$h1.Remove("IDNum") # Removes a pair by its key
$h1["Age"] = 25 # Adds a new pair

$h1["Debt"] = $null # Values can be anything, including null

# Keys can be of any type except $null
$h1[6] = "Six" 
$thisProcess = Get-Process -Id $pid
$h1[$thisProcess] = $pid

# Using new-line instead of ";"
$h2 = @{ 
    FirstName = "Tory"
    LastName = "Amos"
    IDNum = 21 
    }

$h3 = @{ }

$h4 = New-Object Hashtable

```
They can be concatenated as long as they don't have keys with the same name:

```powershell
$h5 = @{ Name="John" ; Age="12"}
$h6 = @{ Fruit="Banana" ; Color="Yellow" }

$h5 + $h6

Name                           Value
----                           -----
Fruit                          Banana
Color                          Yellow
Name                           John
Age                            12
```

## Script Block

A Script Block is a sequence of commands:

```powershell
# Separating commands with ";"
> $block1 = { cd $HOME ; dir }

> $block1
 cd $HOME ; dir

# Separating commands using new-line
> $block2 = {
    cd $HOME 
    dir 
}
```

The Script Block is typically provided as a parameter to a command but we can invoke it using & or . :

```powershell
> & $block1

> . $block1
```

We can specify input parameters:

```powershell
> $block3 = { Param($name)  echo "Hello $name!" }

# Multiple parameters

> $block4 = { 
    Param ($name, $age)
    Write-Output "$name is $age years old" 
}

> . $block4 Adeline 90
Adeline is 90 years old

# We can use parameter names in any order

> . $block4 -age 90 -name Adeline
Adeline is 90 years old

# We can omit parameters

> . $block4 -age 90
 is 90 years old

# Explicit types

> $block5 = { Param([int]$num1, [int]$num2)  Write-Output ($num1 * $num2) }
> . $block5 2 3
6
```
