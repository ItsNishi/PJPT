# PowerView

PowerShell tool for AD enumeration. Part of PowerSploit.

## Loading PowerView

```powershell
# Bypass execution policy
powershell -ep bypass

# Load the module
. .\PowerView.ps1
```

## Domain Enumeration

```powershell
# Basic domain info
Get-NetDomain

# Domain controllers
Get-NetDomainController

# Domain policy (password policy, lockout threshold)
Get-DomainPolicy
(Get-DomainPolicy)."SystemAccess"
```

## User Enumeration

```powershell
# All domain users
Get-NetUser

# Specific properties
Get-NetUser | Select-Object cn, samaccountname, description

# Check for passwords in description fields
Get-NetUser | Select-Object samaccountname, description | Where-Object {$_.description -ne $null}

# Find logged-in users
Get-NetLoggedon -ComputerName TARGET
```

## Group Enumeration

```powershell
# All groups
Get-NetGroup

# Domain Admins
Get-NetGroup -GroupName "Domain Admins"

# Group members
Get-NetGroupMember -GroupName "Domain Admins"
```

## Computer Enumeration

```powershell
# All domain computers
Get-NetComputer

# Detailed info
Get-NetComputer -FullData

# Specific properties
Get-NetComputer -FullData | Select-Object cn, operatingsystem, dnshostname
```

## Share Enumeration

```powershell
# Find shares (noisy -- touches every machine)
Invoke-ShareFinder

# Find files in shares
Invoke-FileFinder
```

## GPO Enumeration

```powershell
# All GPOs
Get-NetGPO

# Readable format
Get-NetGPO | Select-Object displayname, whenchanged
```

**Note:** PowerView is commonly flagged by AV/EDR. Consider obfuscation or using SharpView (C# port) as an alternative.
