# Creating a Custom Project Template for Visual Studio 2022

The way to go is creating a template NuGet package base on a compilable project. In a Nutshell:
- Create a project based on an existing template
- Create a _template.json_ file
- Test it locally
- Create the NuGet package

The advantage of this approach is we can run the project locally and then "templatize" it using the _template.json_ file. In the older approach, we would have a compilable version and a template version of the same project where the template has placeholder variables. 

Visual Studio does provide a way to export the current project as a template but that does not seem to work. 

## Installed templates

### Standard templates

The basic templates are typically at:

```
%ProgramFiles%\Microsoft Visual Studio\2022\<edition>\Common7\IDE\ProjectTemplates\<Language>\<Locale ID>

%ProgramFiles%\Microsoft Visual Studio\2022\<edition>\Common7\IDE\ItemTemplates\<Language>\<Locale ID>
```

### Extension templates

Some templates are installed as Extensions and reside in their respective folders. For example, WinUI 3 templates are part of the _Windows App SDK C# VS2022 Templates_ extension:

```
C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\IDE\Extensions\tkq5tv0c.mpl\ProjectTemplates\CSharp\1033
```

Note that the extension id (tkq5tv0c.mpl) will change for each installation.

### User templates

The user-installed templates are typically at:

```
%USERPROFILE%\Documents\Visual Studio 2022\Templates\ProjectTemplates

%USERPROFILE%\Documents\Visual Studio 2022\Templates\ItemTemplates
```

but the exact location can be configured in Visual Studio at:

- Tools > Options... > Projects and Solutions > Locations

## Create a template based on an existing template

1. Create a project based on an existing template

2. Create a _.template.config_ folder and then the _template.json_ file inside of it

3. Prevent the _template.json_ file to be copied to the output folder in a build

Open the .csproj file and add the following tag inside the _Project_ tag:

```xml
  <!--#if (IncludeTemplateConfig)-->
	<ItemGroup>
		<None Include=".template.config\template.json" />
	</ItemGroup>
  <!--#endif-->
```

4. Edit the _template.json_ file

Example for the WinUi3Net8Unpackaged.csproj project:

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Your Name",
  "classifications": [ "Common", "WinUI" ],
  "name": "WinUI .Net 8 Unpackaged",
  "description": "A WinUI 3 Unpackaged project for .Net 8",
  "identity": "YourName.WinUI.Net8.Unpackaged",
  "shortName": "winui8Unpackaged",
  "tags": {
    "type": "project",
    "platform": "Windows",
    "language": "C#"
  },
  "sourceName": "WinUi3Net8Unpackaged",
  "defaultName": "WinUIApp1",
  "symbols": {
    "IncludeTemplateConfig": {
      "type": "parameter",
      "datatype": "bool",
      "defaultValue": "false"
    }
  },
  "guids": [ "55c835af-1150-4b01-92f7-66c80b153377" ],
  "preferNameDirectory": true
}
```

The _sourceName_ should be the name of the template project. It will be replaced by the name the user will choose when creating a project. Typically, it is the name of the .csproj file and also the namespace used in files in the root level.

The _IncludeTemplateConfig_ symbol will prevent the creation of the tag in the .csproj file.

The Guid in the _guids_ list will cause those guids to be replaced by new ones when a project is created. In this case, the value comes from the _Package.appxmanifest_ file, Package > Identity > Name tag.

Also see the [official](https://github.com/dotnet/templating/wiki/Reference-for-template.json) Reference.

## Test the package locally

Publishing:

```sh
# To install a new package
dotnet new install "<template project path>"

# Get the command to uninstall it
dotnet new uninstall
# and replace the ' for "
```

Installing:

```sh
# Replace {shortName} for the value of the shortName parameter in the template.json file
# -n => Project name
# -o => Output folder
dotnet new {shortName} -n MyExampleApp -o MyOutputFolder
```

## Create the NuGet package

Create the .nuspec file one directory above:

```xml
<?xml version="1.0" encoding="utf-8"?>
<package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
  <metadata>
    <id>WilsonLeite.WinUI.Net8.Unpackaged</id>
    <version>1.0.0</version>
    <description>A WinUI 3 Unpackaged project template for .NET 8</description>
    <authors>Wilson Leite</authors>
    <owners>Wilson Leite</owners>
    <requireLicenseAcceptance>false</requireLicenseAcceptance>
    <license type="expression">MIT</license>
    <projectUrl>https://github.com/WilsonLeite/Stuff</projectUrl>
    <tags>WinUI Template NET8 Unpackaged dotnet-new</tags>
    <packageTypes>
      <packageType name="Template" />
    </packageTypes>
    <summary>WinUI 3 Unpackaged project template for .NET 8 applications</summary>
    <releaseNotes>Initial release of WinUI 3 Unpackaged template for .NET 8</releaseNotes>
    <copyright>Copyright © Wilson Leite 2025</copyright>
    <language>en-US</language>
  </metadata>
  <files>
    <file src="WinUi3Net8Unpackaged\**\*" target="content" exclude="WinUi3Net8Unpackaged\bin\**;WinUi3Net8Unpackaged\obj\**;WinUi3Net8Unpackaged\*.user" />
  </files>
</package>
```

Replace  _WinUi3Net8Unpackaged_ with the name of the template project folder.

Create the package:

```sh
nuget pack WinUi3Net8Unpackaged.nuspec
```

## Install the package

Run the following command to install the template from your NuGet package:

```sh
dotnet new install WilsonLeite.WinUI.Net8.Unpackaged.1.0.0.nupkg
```

## References

- https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/
- https://github.com/sayedihashimi/template-sample
- https://learn.microsoft.com/en-us/visualstudio/ide/creating-project-and-item-templates?view=vs-2022
