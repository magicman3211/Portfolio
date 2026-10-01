**<ins>Only do this Initial steps to setup Leaver Actions/Policies</ins>**<br>
<br>
**<ins>Create a new group for Leavers</ins>**<br>
Groups > All Groups > New Group<br>
Group type > Security<br>
Group Name > group-lifecycle-leavers-quarantine<br>
Memebership Type > Assigned<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/group-lifecycle-leavers-group.png?raw=true)<br>
<br>
**<ins>Now to Implement Conditional Access Policy for Leavers</ins>**<br>
Conditional Access > Create new policy > name > "CA-JML-Leaver-Quarantine-HardBlock"<br>
Assignments > Users > Include > user and groups > group-lifecycle-leavers-quarantine > exclude > break-glass Accounts<br>
Target resources > Include > All cloud Apps<br>
Conditions > Leave default (applies to all device platforms, locations, and client types)<br>
Access controls > Grant > Block Access<br>
Enable Policy > On<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/CA-JML-Leaver-Quarantine-HardBlock.png?raw=true)<br>
<br>
**<ins>Now to Add a new lifecycle workflow for the Leavers</ins>**<br>
Goto ID Governance > lifecycle workflows > Create Workflow<br>
Select Offboard an Employee template > enter workflow name > "Offboard an Employee" > Trigger > Time Based Attribute<br>
Scoping & Trigger > employeeLeaveDateTime > Trigger type > Time Based > 0 days
Add Task > Disable User Account<br>
Add Task > Revoke all refresh tokens for user<br>
Add Task > Remove user from all groups >> remove user from all teams<br>
Add Task > Send email to notify manager of user move (Alert manager to request updated access packages)<br>
Add Task > Add user to group > group-lifecycle-leavers-quarantine<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Config-Lifecycle-Workflow-Leaver-Offboarding.png?raw=true)<br>
<br>
<br>
**<ins>Now one of the last steps is Offboarding any devices of the employee</ins>**<br>
<br>
Option A: Managed Devices (Corporate-Owned)<br>
Navigate to Microsoft Intune admin center > Devices > All devices > Select employee device.
Wipe: Issues a full factory reset (best for devices being reassigned or returned).
Autopilot Cleanup: If reassigning, delete the Windows Autopilot hardware hash assignment or re-tag the device profile.
