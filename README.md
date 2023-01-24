# vb365excludeusers
Script to exclude from VB365 backup jobs users with a particular MS365 license
Microsoft makes the "Teams Exploratory" license available to companies,
which allows MS365 users to try Teams features for 1 year without consuming a paid Teams license.

Even if the user does not have a mailbox, they are automatically assigned an Exchange Online license.
This "experience" can be started by users on their own, unless the tenant admin disables the option.
 
Problem
If the Veeam Backup for Microsoft 365 administrator has placed the entire organization or groups containing users who (even later) have enabled the "Teams Explorator" license in a mailbox backup job, one Veeam license is consumed for each of these users who, in reality, may not have initially had even a mailbox available.
 
Workarounds
I created a simple PowerShell script that examines the users involved in a backup job, checks if they are associated with a "Teams Exploratory" type license and, if so, inserts them among the exceptions.
