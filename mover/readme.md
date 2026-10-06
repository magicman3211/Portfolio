**<ins>Create a new group for Movers</ins>**<br>
Groups > All Groups > New Group<br>
Group type > Security<br>
Group Name > group-lifecycle-movers <br>
Memebership Type > Assigned<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Group-lifecycle-movers.png?raw=true)<br>
<br>
**<ins>Now to Add a new lifecycle workflow for the movers</ins>**<br>
Goto ID Governance > lifecycle workflows > Create Workflow<br>
Select Mover template > enter workflow name > "Employee job profile change" > Trigger ? On Demand<br>
Add Task > Remove user from selected groups > group-lifecycle-new-hires<br>
Add Task > Add user to groups > group-lifecycle-movers<br>
Add Task > Revoke all refresh tokens for user<br>
Add Task > Remove all access package assignments for user<br>
Add Task > Send email to notify manager of user move (Alert manager to request updated access packages)<br>
(**Note request to new access packages arent included here as I dont have any packages assigned**)<br>
<br>
<br>
![image_1](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Workflow-lifecycle-movers-1.png?raw=true)<br>
![image_2](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Workflow-lifecycle-movers-tasks-1.png?raw=true)<br>
<br>
**<ins>Now to Implement Conditional Access Policy for Movers</ins>**<br>
Conditional Access > Create new policy > name > "CA-JML-Mover-RoleTransition"<br>
Assignments > Users > Include > user and groups > group-lifecycle-movers > exclude > break-glass Accounts<br>
Target resources > Include ? All cloud Apps<br>
Client Apps > Configue > Yes > Browser, Mobile Apps & Desktop clients
Access controls > Grant > require multifactor authentication <br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/CA-JML-Mover-RoleTransition.png?raw=true)<br>
<br>
