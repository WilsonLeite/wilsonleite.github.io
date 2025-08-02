# .NET MAUI

References:

* https://www.youtube.com/playlist?list=PLdo4fOcmZ0oUBAdL2NwBpDs32zwGqb9DY

## Project creation

Use the _.NET MAUI App_ template ib Visual Studio.

### Creating a Windows-only project

* Edit the project file

* Replace the target framework

```XML
<-- Replace this ->

<TargetFrameworks>net9.0-android;net9.0-ios;net9.0-maccatalyst</TargetFrameworks>
<TargetFrameworks Condition="$([MSBuild]::IsOSPlatform('windows'))">$(TargetFrameworks);net9.0-windows10.0.19041.0</TargetFrameworks>

<-- for this ->

<TargetFramework>net9.0-windows10.0.19041.0</TargetFramework>

```

* Remove the SupportedOSPlatformVersion tags for the other platforms

```xml

<-- Replace this ->

<SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'ios'">15.0</SupportedOSPlatformVersion>
<SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'maccatalyst'">15.0</SupportedOSPlatformVersion>
<SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'android'">21.0</SupportedOSPlatformVersion>
<SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'windows'">10.0.17763.0</SupportedOSPlatformVersion>
<TargetPlatformMinVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'windows'">10.0.17763.0</TargetPlatformMinVersion>
<SupportedOSPlatformVersion Condition="$([MSBuild]::GetTargetPlatformIdentifier('$(TargetFramework)')) == 'tizen'">6.5</SupportedOSPlatformVersion>

<-- for this ->

<SupportedOSPlatformVersion>10.0.17763.0</SupportedOSPlatformVersion>
<TargetPlatformMinVersion>10.0.17763.0</TargetPlatformMinVersion>

```

* Remove the folders for the non-Windows targets under the _Platforms_ folder

## How-tos

* [MVVM](./mvvm.md)
