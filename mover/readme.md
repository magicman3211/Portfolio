Mover<br>
**Create a new group for Movers**<br>
Groups > All Groups > New Group<br>
Group type > Security<br>
Group Name > group-lifecycle-movers <br>
Memebership Type > Assigned<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Group-lifecycle-movers.png?raw=true)<br>
<br>
**Now to Add a new lifecycle workflow for the movers**<br>
Goto ID Governance > lifecycle workflows > Create Workflow<br>
Select Mover template > enter workflow name > "Real-time employee job change" > Trigger ? On Demand<br>
Add Task > Remove all access package assignments for user<br>
Add Task > Add user to groups > group-lifecycle-movers<br>
Add Task > Send email to notify manager of user move (Alert manager to request updated access packages<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Workflow-lifecycle-movers.png?raw=true)<br>
<br>
