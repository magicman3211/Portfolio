**<ins>Only do this Initial steps to setup Joiner Actions/Policies</ins>**<br>
<br>

![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/group-lifecycle-new-hires.png?raw=true)<br>
<br>

Go to Entra ID Admin Center > Authentication methods > Policies > Temporary Access Pass<br>
Set Enable to **Yes**<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Temp-access-pass-settings.png?raw=true)<br>
<br>
**And target new group > group-lifecycle-new-hires**<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/target-group-lifecycle-new%20hires.png?raw=true)<br>
<br>

And in configure tab, Require one-time use: Yes (terminates once user registers passwordless/MFA)<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/target-group-lifecycle-new%20hires-one-time-pass.png?raw=true)<br>
<br>
Next we need to create a conditional access policy<br>
Name > CA-JML-Joiner-MFA-Registration-Enforcement<br>
Groups we include are our group > group-lifecycle-new-hires<br>
Target Resources > Under User Actions > we make sure to select > Register Security Information<br>
Conditions > Network: Include Any location, Exclude Trusted / Named Corporate IP Ranges (if strict on-prem/managed network onboarding is required; otherwise leave default).<br>
Access Controls > Grant > Select Grant Access > Access Controls > Select Grant access > <br>
Check Require authentication strength > Select Phishing-resistant MFA (or custom strength specifying Temporary Access Pass / FIDO2) <br>
Enable policy: On (or Report-only for initial validation)<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/CA-JML-Joiner-MFA-Registration-Enforcement.png?raw=true)<br>
<br>

Next we need to Isolate Enterprise Apps during Onboarding with a CA Policy<br>
Name > CA-JML-Joiner-Quarantine-EntApps<br>
Users > Include specific group > group-lifecycle-new-hires >> Exclude Break-Glass Accounts<br>
Target Resources > Select Cloud Apps > All Cloud Apps >> Exclude > Microsoft Intune Enrollment > Microsoft Authentication Broker<br>
Conditions > Device Platforms: Any > Client Apps > Browser, Mobile apps and Desktop Clients<br>
Access Controls > Grant > Select Grant > Block access >> Alernative Select Grant Access > check Require device to be marked as compliant<br>
Enable Policy > On<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/CA-JML-Joiner-Quarantine-EntApps.png?raw=true)<br>
<br>
<br>
**<ins>Next Step if we want to Automate the Joiner Process (Lifecycle Workflow)</ins>**<br>
For Days/Weeks before employee offically starts with company<br>
<br>
Create workflow > select Onboard pre-hire employee template<br>
Trigger type > Time Based Attribute >> Days from Event > 1<br>
Scope Property > userType > Operator > equal > Value "Member"<br>
<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Config-Lifecycle-Workflow-Joiner.png?raw=true)<br>
<br>
Make sure the following tasks are enabled<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Lifecycle-workflow-joiner-group.png?raw=true)<br>
<br>
Now for the day when the employee strarts, We create another Lifecycle Workflow<br>
Create workflow > select Onboard new hire employee template<br>
Trigger type > Time Based Attribute >> Days from Event > 0<br>
<br>
![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Config-Lifecycle-Workflow-Joiner-Enable-tasks-2nd-workflow.png?raw=true)<br>
<br>



