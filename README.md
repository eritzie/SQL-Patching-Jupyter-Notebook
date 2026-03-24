# SQL-Patching-Jupyter-Notebook
A PowerShell-based SQL Server monthly patching runbook built as a Jupyter notebook for Visual Studio Code. Automates patch compliance checks, service management, CU downloads, standalone and FCI patching, post-patch verification, and SQL Agent job execution using dbatools and kbupdate.

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
- Service shutdown — Stop and disable SQL Engine and Agent on standalone instances
- Patching — Apply CUs to standalone instances; manual steps noted for FCIs
- FCI handling — Failover clustered instances, patch the passive node, failover back, patch the original primary
- Service restart — Re-enable and start Engine, then Agent
- Post-patch verification — Confirm patch level compliance, database online state, and error logs
- SQL Agent job execution — Run scheduled nightly jobs displaced by the maintenance window

## Notes

- Clustered instances (FCI) require manual failover steps; the notebook marks these explicitly
- Replication tracer token testing is included as a manual step post-restart
- Instance names and SQL Agent job lists are environment-specific and will need to be updated before use

## Related Tools

- dbatools documentation
- kbupdate on GitHub
