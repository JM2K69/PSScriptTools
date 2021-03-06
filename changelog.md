# Change Log for PSScriptTools

## v2.4.0

+ Made datagrid in `ConvertTo-WPFGrid` read-only (Issue #38)
+ Modified datagrid in `ConvertTo-WPFGrid` to better handle resizing (Issue #36)
+ Modified statusbar in `ConvertTo-WPFGrid` to better handle resizing (Issue #37)
+ Modified form in `ConvertTo-WPFGrid` to better fit in the screen and not exceed the screen area (Issue #39)
+ Added parameter to allow usage of local variables in `ConvertTo-WPFGrid` (Issue #35)
+ Help updates
+ Reorganized `README.md`

## v2.3.0

+ Fixed bug in `ConvertTo-WPFGrid` that wasn't updating last update time. (Issue #30)
+ Modified `ConvertTo-WPFGrid` to allow user to load their profile scripts into the runspace. (Issue #29)
+ Modified auto sizing code in `ConvertTo-WPFGrid`
+ Modified `ConvertTo-WPFGrid` to automatically display scroll bars when necessary.
+ Modified `New-PSFormatXML` to display a warning on invalid property names. (Issue #33)
+ Added `Get-myTimeInfo`, `ConvertTo-UTCTime` and `ConvertFrom-UTCTime` (Issue #31)
+ help updates
+ Updated `README.md`

## v2.2.0

+ Code revisions in `ConvertTo-WPFGrid` (Issue #27)
+ Updated `Get-ParameterInfo` to reflect dynamic parameters (Issue #28)
+ Updated `Get-PSLocation` to better reflect locations and use a custom format file.
+ Updated `Get-WindowsVersion` with custom type for format file. Also better handling of non-Windows platforms.
+ Updated `Get-WindowsVersionString` to include the computername.
+ Updated `New-WPFMessageBox` to gracefully exit if running on PowerShell Core.
+ Updated `Test-ExpressionForm` to gracefully exit if running on PowerShell Core.
+ Updated `New-RandomFilename` to better reflect locations using `[environment]`
+ Modified manifest to be more aware of PSEdition and only load compatible commands.
+ Help updates
+ Updated `README.md`

## v2.1.0

+ Added parameter to allow user to specify a type name with `New-PSFormatXML` (Issue #26)
+ Added `Get-ParameterInfo` command with an alias of `gpi`
+ Updated help for `Optimize-Text`
+ Help updates
+ Updated `README.md`

## v2.0.0

+ Added `New-PSFormatXml` and its alias `nfx`
+ Raised minimum PowerShell version to 5.1
+ Modified manifest to support both `Desktop` and `Core`
+ Added `Remove-Runspace`
+ Modified `ConvertTo-WPFGrid` to autosize the display and support an automatic refresh
+ Modified `ConvertTo-WPFGrid` to use a runspace (Issue #22)
+ Updated `README.md`
+ Updated help documentation
+ Raised version number to reflect a number of potentially breaking changes.

## v1.8.1

+ minor corrections to `Compare-Module` (Issue #21)

## v1.8.0

+ fixed typo in `Write-Detail` (Thanks @AndrewPla)
+ Added `Compare-Module` function (Issue #19)
+ Added `Get-WindowsVersion` function (Issue #20)
+ Added `Get-WindowsVersionString` function
+ Updated `README.md`
+ Updated module manifest
+ reorganized module
+ Updated Pester test for `Test-Expression`
+ Updated external help file

## v1.7.0

+ Added `New-WPFMessagebox` function. (Issue #11)
+ Added alias `nmb` for `New-WPFMessageBox`
+ Added icon files for WPF Message box
+ Updated `README.md`

## v1.6.0

+ Added `Optimize-Text` and its alias `ot`
+ Added `Show-Tree`
+ Help and documentation updates

## v1.5.1

+ code cleanup for the published module in the PowerShell Gallery

## v1.5.0

+ Added `Select-First` and its alias `first`
+ Added `Select-Last` and its alias `last`
+ Added `Get-MyVariable` and its alias `gmv`
+ Added `New-PSDriveHere` and its alias `npsd`
+ Updated `README.md`

## v1.4.0

+ Added hashtable tools
+ Updated `README.md`
+ minor code cleanup

## v1.3.0

+ Fixed documentation errors for `Out-ConditionalColor` (Issue #13)
+ Added alias definitions to functions
+ Added my `Test-Expression` commands (Issue #14)
+ Added my `Find-CimClass` function (Issue #16)
+ Added my `ConvertTo-Markdown` function (Issue #17)
+ Added `ConvertTo-WPFGrid` (Issue #15)
+ help cleanup and updates
+ Code cleanup and formatting

## v1.2.0

+ Updated `Write-Detail`
+ Updated README

## v1.1.0

+ Cleaned up ToDo code (Issue #12)
+ Updated README
+ Help cleanup

## v1.0.1

+ fixed version number mistake
+ updated README.md

## v1.0.0

+ initial release to the PowerShell Gallery

## v0.5.0

+ Added `Get-PSLocation` function (Issue #4)
+ Added `Get-PowerShellEngine` function (Issue #5)
+ Added `Out-More` and alias `om` (Issue #10)
+ Added icon to manifest
+ Added `Invoke-InputBox` and alias `ibx`
+ Added code to insert ToDo comments for the ISE and VSCode (Issue #7)
+ Updated README
+ Updated documentation

## v0.4.0

+ Added `Copy-Command` (Issue #2)
+ Updated `Copy-Command` to open new file in the ISE or VSCode
+ Added Format functions (Issue #3)
+ Updated help
+ Added new sample files

## v0.3.0

+ Added help documentation
+ Updated README
+ Added samples
+ Reverted `Get-PSWho` to not trim when using -AsString
+ Added code to `New-CustomFileName` to preserve case for non-placeholders
+ Modified `Out-VerboseTee` to turn on VerboseTee

## v0.2.0

+ Modified verbose output to use Write-Detail
+ Expanded aliases to full cmdlet names
+ Modified `Get-PSWho` to trim when using -AsString
+ Added `Out-ConditionalColor`
+ Added `Get-RandomFileName`
+ Added `New-CustomFileName`

## v0.1.0

+ initial module