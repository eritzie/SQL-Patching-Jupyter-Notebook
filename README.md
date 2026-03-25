# SQL Server Monthly Patching Runbook
A Jupyter notebook for Visual Studio Code that walks through the full monthly SQL Server patch cycle, from compliance checks through post-patch verification. Built on dbatools and kbupdate, with each step as a discrete, executable cell.

## Requirements

- Visual Studio Code with the PowerShell kernel, or JupyterLab
- PowerShell modules: dbatools, kbupdate
- Appropriate permissions on target SQL Server instances

## What It Does

The notebook steps through the patch cycle in order:

- Target selection — Define the SQL instances to patch (dev, test, or prod)
- Compliance check — Identify which instances are behind on CUs using Test-DbaBuild
- Patch download — Pull the needed CU files via kbupdate
- Pre-patch state capture — Record current service states and identify clustered instances
- Patching — Apply CUs to standalone instances
- Post-patch verification — Confirm patch level compliance, database online state, and error logs

## Notes

- Instance names and SQL Agent job lists are environment-specific and will need to be updated before use

## Related Tools

- dbatools documentation
- kbupdate on GitHub
