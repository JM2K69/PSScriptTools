---
external help file: PSScriptTools-help.xml
Module Name: PSScriptTools
online version:
schema: 2.0.0
---

# ConvertTo-WPFGrid

## SYNOPSIS

Send command output to an interactive WPF-based grid.

## SYNTAX

### input (Default)

```yaml
ConvertTo-WPFGrid [[-Title] <String>] [[-Timeout] <Int32>] [-Refresh] [-UseLocalVariable <String[]>]
 [-UseProfile] [<CommonParameters>]
```

### Input

```yaml
ConvertTo-WPFGrid [[-InputObject] <PSObject>] [[-Title] <String>] [[-Timeout] <Int32>] [-Refresh]
 [-UseLocalVariable <String[]>] [-UseProfile] [<CommonParameters>]
```

### scriptblock

```yaml
ConvertTo-WPFGrid [-Scriptblock <ScriptBlock>] [[-Title] <String>] [[-Timeout] <Int32>] [-Refresh]
 [-UseLocalVariable <String[]>] [-UseProfile] [<CommonParameters>]
```

## DESCRIPTION

This command is an alternative to Out-Gridview. It works much the same way. Run a PowerShell command and pipe it to this command. The output will be displayed in an auto-sized data grid. You can click on column headings to sort. You can resize columns and you can re-order columns. You will want to be selective about which properties you pipe through to this command. See examples.

You can specify a timeout value which will automatically close the form. If you specify a timeout and the Refresh parameter, then the contents of the datagrid will automatically refreshed using the timeout value as an integer. This will only work when you pipe a PowerShell expression to ConvertTo-WPFGrid as one command. This will fail if you break the command in the PowerShell ISE or use a nested prompt. Beginning with v2.4.0 the form now has a Refresh button which will automatically refresh the datagrid.

Because the grid is running in a new background runspace, it does not automatically inherit anything from your current session. However, you can use the -UserProfile parameter which will load your user profile scripts into the runspace. You can also specify a list of locally defined variables to be used in the form.

This command runs the WPF grid in a new runspace so your PowerShell prompt will not be blocked. However, after closing the form you may be left with the runspace. You can use Remove-Runspace to clean up or wait until you restart PowerShell.

## EXAMPLES

### EXAMPLE 1

```powershell
PS C:\> get-process | sort-object WS -Descending | Select-object -first 20 ID,Name,WS,VM,PM,Handles,StartTime | Convertto-WPFGrid -Refresh -timeout 20 -Title "Top Processes"
```

Get the top 20 processes based on the value of the WorkingSet property and display selected properties in the WPF Grid. The contents will automatically refresh every 20 seconds. You will need to manually close the form.

### EXAMPLE 2

```powershell
PS C:\> $vmhost = "CHI-HVR2"
PS C:\> Get-VM -computername $VMHost | Select Name,State,Uptime,
@{Name="AssignedMB";Expression={$_.MemoryAssigned/1mb -as [int]}},
@{Name="DemandMB";Expression={$_.MemoryDemand/1mb -as [int]}} |
ConvertTo-WPFGrid -title "VM Report $VMHost" -timeout 30 -refresh -uselocalvariable VMHost
```

Get Hyper-V virtual machine information and refresh every 30 seconds. Because the command is using a locally defined variable it is also being used in the form. Note that this would be written as one long pipelined expression. It is formatted here for the sake of the help documentation.

### EXAMPLE 3

```powershell
PS C:\> Get-VMData -host CHI-HVR2 | ConvertTo-WPFGrid -title "VM Data" -refresh -timeout 60 -useprofile
```

This example uses a hypothetical command that might be defined in a PowerShell profile script. ConvertTo-WPFGrid will load the profile scripts so that the data can be updated every 60 seconds.

## PARAMETERS

### -InputObject

Typically the results of a PowerShell command or expression. You should select the specific properties you wish to display.

```yaml
Type: PSObject
Parameter Sets: Input
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Title

Specify a title for your form.

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: ConvertTo-WPFGrid
Accept pipeline input: False
Accept wildcard characters: False
```

### -Timeout

By default the grid will remain displayed until you manually close it. But you can specify a timeout interval in seconds. The minimum accepted value is 5 seconds. If you use this parameter with -Refresh, then the datagrid will be refreshed with results of the PowerShell expression you piped to ConvertTo-WPFGrid.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -Refresh

If you specify this parameter and a Timeout value, this command will refresh the datagrid with the PowerShell expression piped into ConvertTo-WPFGrid. This will only work if you are using this command at the end of a pipelined expression. See examples.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseProfile

Load your PowerShell profiles into the background runspace.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: profile

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Scriptblock

Enter a scriptblock that will generate data to be populated in the form

```yaml
Type: ScriptBlock
Parameter Sets: scriptblock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseLocalVariable

Load locally defined variables into the background runspace

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: var

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see about_CommonParameters (http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### [PSObject]

## OUTPUTS

### None

## NOTES

Learn more about PowerShell: http://jdhitsolutions.com/blog/essential-powershell-resources/

## RELATED LINKS

[Out-GridView]()

[ConvertTo-HTML]()

[ConvertTo-Markdown](./ConvertTo-Markdown.md)