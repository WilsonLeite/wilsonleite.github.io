# Versions of PowerShell

## Products

There are two similar products with similar names. However, not all commands are available in both products and some commands can have different parameters, causing different behaviors.

### Windows PowerShell

This is the older version of the product and typically ships with Windows. It is based on .Net Framework. It can be run from the Start Menu, Windows Terminal, and Command Prompt by invoking _PowerShell.exe_.

This version runs only on Windows and supports more Windows-specific commands or parameters. 

The latest (and final) version is 5.1:

```powershell
PS C:\> $PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.19041.3693

``` 

Microsoft still supports it, but it is no longer improving it.

### PowerShell

This is the new version based on .Net Core - Nowadays just called _.Net_. It runs on Windows, Linux, and Mac.

It typically does not come installed on Windows. There are several ways to [install](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell) it, but one of the simpler ways to install it on Windows is:

```batchfile
C:\> winget install --id Microsoft.PowerShell
``` 

Once installed, it can be run from the Start Menu, Windows Terminal, and Command Prompt by invoking _pwsh.exe_.

This product (at the time of this writing) is under active development.
