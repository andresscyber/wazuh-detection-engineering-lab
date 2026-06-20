# Detection 01 - PowerShell Executed SecEdit

## Objective

Detect PowerShell execution used to launch the Windows Security Configuration Editor (SecEdit).

## Data Source

- Sysmon Event ID 1 (Process Creation)

## Detection Logic

Parent Wazuh Rule:
- 92027
- Powershell process spawned powershell instance

Custom Rule:
- 100100

Condition:
- Process command line contains "secedit"

## MITRE ATT&CK

Technique:
- T1059.001 - PowerShell

Tactic:
- Execution

## Validation

Executed:

powershell secedit /export /cfg C:\Windows\Temp\secpol.cfg

Result:

Custom detection generated successfully.

## Severity

Level 12