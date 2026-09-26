Azure Entra ID – Joiner / Mover / Leaver (JML) Identity Lifecycle Automation

A hands-on lab demonstrating identity lifecycle management (joiner, mover, leaver) in Microsoft Entra ID using security groups and Conditional Access (CA) policies to enforce tiered access controls as an employee's role changes.

![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Joiner-mover-leaver-lifecycle.jpeg?raw=true)

## Table of contents:<br>
Overview<br>
Architecture<br>
Environment setup<br>
<br>
Lifecycle walkthrough:<br>
- Joiner – new hire onboarding<br>
- Established – mid-level device compliance<br>
- Mover – promotion to senior level<br>
- Leaver – retirement / offboarding<br>
<br>
Conditional Access policy matrix<br>
Known limitations & production notes<br>
What I'd automate next<br>
<br>
<br>


** OVERVIEW:<br>
Built a small-scale Entra ID lab to test end-to-end identity lifecycle management. It maps out how dynamic group memberships and Conditional Access policies hand off controls automatically as someone joins, moves up within the company, and eventually exits.

Why this lab: Proves hands-on execution of core IAM workflows. Instead of just studying policies on paper, it builds out the mechanics—group-driven access control, layered Conditional Access, and automated JML transitions—that day-to-day identity and cloud security admins rely on.

![image_alt](https://github.com/magicman3211/Portfolio/blob/main/screenshots-images/Entra-admin-centre.png?raw=true)

ARCHITECTURE:
