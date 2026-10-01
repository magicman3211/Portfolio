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
