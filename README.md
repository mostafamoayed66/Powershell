<picture>
  <source media="(min-width:650px)" srcset="./Powershell_MindMap.png">
  <source media="(min-width:465px)" srcset="./Powershell_MindMap.png">
  <img src="./Powershell_MindMap.png" alt="Flowers" style="width:auto;">
</picture>

## Powershell
The Explanation about Powershell. PowerShell Quick Start and Essentials

[Powershell_MindMap.md](https://github.com/user-attachments/files/24392265/Powershell_MindMap.md)# PowerShell Quick Start and Essentials

## 🖥️ Introduction and Setup

PowerShell is both a command line shell and a scripting language designed by Microsoft.

Accessible by typing "powershell" in the search bar.

Font size and environment customization improve readability.

PowerShell version can be checked using the $PSVersionTable.PSVersion variable.

Execution policies control script running permissions; commonly set to "RemoteSigned" for running custom scripts.

PowerShell ISE (Integrated Scripting Environment) is a built-in editor ideal for writing and testing scripts.

## ⚙️ Basic Commands and Script Writing

Commandlets (cmdlets) follow a verb-noun format, e.g., Write-Host.

Tab completion and arrow keys aid command recall and typing efficiency.

Writing first scripts involves commands like Write-Host "Hello World".

Comments use # and are ignored during execution.

Parameters modify cmdlet behavior, e.g., Write-Host -NoNewline.

Get-Command lists available cmdlets; modules group related cmdlets for specific tasks.

## 🔄 Data Handling: Variables, Arrays, Hash Tables, and Objects

Variables start with $, e.g., $faveCharacter = "SpongeBob".

PowerShell supports various data types: strings, integers, doubles, and booleans.

Everything in PowerShell is an object with properties and methods, discoverable via Get-Member.

Arrays hold ordered collections, accessed by zero-based indices.

Hash tables store key-value pairs, manipulated using methods like .Add(), .Remove(), and direct property access.

## 🔁 Control Structures: Conditionals and Loops

Conditionals use if, else if, and else blocks to control flow.

Comparison operators include -eq (equals), -ge (greater or equal), and -le (less or equal).

switch statements provide a cleaner way to evaluate multiple conditions.

### Loops include:for loops: iterate with initialization, condition, and increment.foreach loops: iterate over collections directly.while loops: execute while condition is true.do-while loops: execute at least once before condition check.

for loops: iterate with initialization, condition, and increment.

foreach loops: iterate over collections directly.

while loops: execute while condition is true.

do-while loops: execute at least once before condition check.

## 🛠️ Advanced Scripting: Functions, Error Handling, and File Management

Functions encapsulate reusable code blocks, defined with function Name { }.

Parameters can be defined inside functions with [CmdletBinding()] and param() to create advanced functions.

Error handling uses try { } catch { } blocks to manage exceptions gracefully.

### File operations include:New-Item for creating files/folders.Copy-Item, Move-Item, and Remove-Item for file manipulation.Test-Path to verify file or folder existence.Rename-Item to change file names.

New-Item for creating files/folders.

Copy-Item, Move-Item, and Remove-Item for file manipulation.

Test-Path to verify file or folder existence.

### More Information and Tutorial
https://www.tutorialspoint.com/powershell/index.htm
Rename-Item to change file names.

## 🏢 Working with Active Directory (AD)

Import AD module using Import-Module ActiveDirectory.

Retrieve user info with Get-ADUser -Identity username.

Modify user attributes with Set-ADUser.

Add or remove users from groups via Add-ADGroupMember and Remove-ADGroupMember.

Create new users with New-ADUser, supplying necessary details like Name, GivenName, Surname, SamAccountName, UserPrincipalName, and OU path.

Passwords require conversion to a secure string using ConvertTo-SecureString.

AD manipulations can be scripted for automation in enterprise environments.

## Get-SystemProcessInformation

Use NtQuerySystemInformation::SystemProcessInformation to get a detailed list of processes and process properties. On close inspection you will find that many process monitors such as Sysinternals Process Explorer or Process Hacker use this information class (in addition to SystemPerformanceInformation, SystemProcessorPerformanceInformation and SystemProcessorCycleTimeInformation).

``` bash
# Return full process listing
C:\PS> Get-SystemProcessInformation

# Return only specific PID
C:\PS> Get-SystemProcessInformation -ProcID 1336

PID                        : 1336
InheritedFromPID           : 1020
ImageName                  : svchost.exe
Priority                   : 8
CreateTime                 : 0d:9h:8m:47s
UserCPU                    : 0d:0h:0m:0s
KernelCPU                  : 0d:0h:0m:0s
ThreadCount                : 12
HandleCount                : 387
PageFaults                 : 7655
SessionId                  : 0
PageDirectoryBase          : 3821568
PeakVirtualSize            : 2097249.796875 MB
VirtualSize                : 2097240.796875 MB
PeakWorkingSetSize         : 11.65625 MB
WorkingSetSize             : 6.2109375 MB
QuotaPeakPagedPoolUsage    : 0.175910949707031 MB
QuotaPagedPoolUsage        : 0.167121887207031 MB
QuotaPeakNonPagedPoolUsage : 0.0151519775390625 MB
QuotaNonPagedPoolUsage     : 0.0137710571289063 MB
PagefileUsage              : 3.64453125 MB
PeakPagefileUsage          : 4.14453125 MB
PrivatePageCount           : 3.64453125 MB
ReadOperationCount         : 0
WriteOperationCount        : 0
OtherOperationCount        : 223
ReadTransferCount          : 0
WriteTransferCount         : 0
OtherTransferCount         : 25010

# Possibly returns multiple processes
# eg: notepad.exe & notepad++.exe
C:\PS> Get-SystemProcessInformation -ProcName note

```
