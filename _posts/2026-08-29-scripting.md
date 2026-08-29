---
layout: post
title: Scripting
excerpt_separator:  <!--more-->
---

Over the years working in IT Operations and System Administration, I've built up scripting skills with Bash and Powershell that come in handy day to day. Here's a rundown of the areas I rely on most.

## PowerShell

### PowerShell Data Types

| Type | Description |
| --- | --- |
| `[string]` | Text data |
| `[int]` | 32-bit whole number |
| `[long]` | 64-bit whole number |
| `[double]` | Double-precision floating-point number |
| `[decimal]` | High-precision decimal number, useful for currency |
| `[bool]` | Boolean value (`$true` or `$false`) |
| `[datetime]` | Date and time value |
| `[array]` | Ordered collection of items |
| `[hashtable]` | Collection of key/value pairs |
| `[PSCustomObject]` | Custom object with user-defined properties |

### PowerShell Conditionals

PowerShell uses `if`, `elseif`, and `else` blocks to control the flow of a script based on a condition.

```powershell
$diskSpaceGB = 15

if ($diskSpaceGB -lt 10) {
    Write-Host "Warning: Low disk space"
} elseif ($diskSpaceGB -lt 50) {
    Write-Host "Disk space is okay, but keep an eye on it"
} else {
    Write-Host "Plenty of disk space available"
}
```

### PowerShell Loops

PowerShell supports several loop types, including `foreach` for iterating over a collection and `while` for repeating while a condition holds true.

```powershell
$servers = @("web01", "web02", "db01")

foreach ($server in $servers) {
    Write-Host "Checking status of $server"
}

$attempt = 1
while ($attempt -le 3) {
    Write-Host "Attempt $attempt"
    $attempt++
}
```

### PowerShell Functions

Functions let you package up reusable logic with the `function` keyword, and can accept parameters.

```powershell
function Get-DiskStatus {
    param (
        [int]$DiskSpaceGB
    )

    if ($DiskSpaceGB -lt 10) {
        return "Warning: Low disk space"
    }

    return "Disk space is okay"
}

Get-DiskStatus -DiskSpaceGB 5
```

## Bash

### Bash Data Types

Bash doesn't enforce strict data types the way PowerShell does - by default, everything is treated as a string - but variables can still be declared or used to behave like the following types.

| Type | Description |
| --- | --- |
| String | Text data, the default type for all variables |
| Integer | Whole number, declared with `declare -i` for arithmetic context |
| Array | Ordered, indexed collection of values (`declare -a`) |
| Associative Array | Collection of key/value pairs (`declare -A`) |
| Boolean | No native type - simulated using exit status (`0` = true, non-zero = false) |

### Bash Conditionals

Bash uses `if`, `elif`, and `else` blocks with `[[ ]]` test expressions to control the flow of a script based on a condition.

```bash
diskSpaceGB=15

if [[ $diskSpaceGB -lt 10 ]]; then
    echo "Warning: Low disk space"
elif [[ $diskSpaceGB -lt 50 ]]; then
    echo "Disk space is okay, but keep an eye on it"
else
    echo "Plenty of disk space available"
fi
```

### Bash Loops

Bash supports several loop types, including `for` for iterating over a list and `while` for repeating while a condition holds true.

```bash
servers=("web01" "web02" "db01")

for server in "${servers[@]}"; do
    echo "Checking status of $server"
done

attempt=1
while [[ $attempt -le 3 ]]; do
    echo "Attempt $attempt"
    ((attempt++))
done
```

### Bash Functions

Functions let you package up reusable logic, and can accept arguments through the positional parameters `$1`, `$2`, etc.

```bash
get_disk_status() {
    local disk_space_gb=$1

    if [[ $disk_space_gb -lt 10 ]]; then
        echo "Warning: Low disk space"
    else
        echo "Disk space is okay"
    fi
}

get_disk_status 5
```
