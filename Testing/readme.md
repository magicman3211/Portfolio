**This section will be a showcase of the Joiner,Mover,Leaver process in action with test users with outcomes**<br>
For the test data, I generated names, job titles and Departments with AI, an this is the data Im using for testing purposes<br>
I chose to do it manually this time, so I can see all the processes as I enter the details, and that the bulk csv file has no field for start date<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Test-user-data-input.png?raw=true)<br>
<br>
<br>
**<ins>Joiner Process</ins>**<br>
<br>
Now that I have everyone Entered, I have an start date of two days time, So in 1 day the pre-employement lifecycle-workflow will initiate<br>
<br>
Image shows a successful import (Onboard pre-hire Employees - Workflow)<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Post-onbbard-pre-hire-employee-part-1.png?raw=true)<br>
<br>
<br>
And a workflow history showing a successful import of all tasks in this workflow, below<br>
Completing Pre-Hire of Employees<br>****
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Post-onbbard-pre-hire-employee-part-2.png?raw=true)<br>
<br>
<br>
<br>
Now for day of hire Employees<br>
Image shows successful import (Onboard new hire Employees)<br>
Note To Self - James Thornton had errors, because I mistakenly logged into his account before hire date onboarding process<br>
<br>
![Image 1](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Post-Onboard-new-hire-employee-1.png?raw=true)
<br>
<br>
And a workflow history showing a successful import of all tasks in this workflow, below<br>
<br>
![Image 2](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Post-Onboard-new-hire-employee-2.png?raw=true)<br>
<br>
<br>
James Thornton error occured because after pre-hire workflow, I signed in to his account, then when onboard new hire workflow ran, it had already triggered Generate TAP (which is a one off use)<br>
<br>
![Image 3](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/James-Thornton-error.png?raw=true)<br>
<br>
<br>
**<ins>Mover Process</ins>**<br>
<br>
The Mover Process has 1 manual task, that is in Change of Job Title to a "Senior" Postition<br>
<br>
The 4 Employees moving to Senior Roles will be:<br>
Aisha Patel<br>
Carlos Mendez<br>
David O'Conner<br>
Hannah Schmidt<br>
<br>
<br>
![worflow-history](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Lifecycle-workflow-employee-job-profile-change-workflow-history.png?raw=true)<br>
![workflow-task](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Lifecycle-workflow-employee-job-profile-change-workflow-history-task-view.png?raw=true)<br>
<br>
<br>
**<ins>Leaver Process</ins>**
<br>
<br>
The Leaver Process is purely a manual trigger event<br>
<br>
The 4 Epployees Leaving the Business will be:<br>
Elana Rostova<br>
Liam Vance<Br>
Marcus Chen<br>
Sarah Jenkins<br>
<br>
<br>
Realtime employee termination lifecycle workflow > Run On-Demand > Select above employees<br>
<br>
![image3](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Real-time-employee-termination-workflow-history.png?raw=true)<br>
<br>
<br>
The following screenshot show quarantined users now in a group of their own that are disabled users<br>
<br>
![quarintined_users](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/group-lifecycle-leavers-quarantined%20users.png?raw=true)<br>
<br>
