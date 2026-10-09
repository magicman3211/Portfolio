## Project Summary and Conclusions

### Purpose
This project demonstrates an end-to-end identity lifecycle (Joiner, Mover, Leaver) in Microsoft Entra ID. It uses Lifecycle Workflows to automate account and group changes, and Conditional Access to enforce the access requirements that apply at each stage. It was built in a trial Entra tenant as a hands-on learning project while I study for the SC-300 (Microsoft Identity and Access Administrator) certification.

### Approach and research
I researched the design using Microsoft documentation, video walkthroughs, and general web searches, including AI-assisted search. The workflows in this repository follow standard, documented patterns for each lifecycle stage. They are intentionally foundational. My aim was to build, test, and understand the core mechanics before attempting more advanced automation.

### Scope and test data
| Lifecycle stage | Test accounts |
|---|---|
| Joiners (new hires) | 15 |
| Movers (role changes) | 4 |
| Leavers (offboarding) | 4 |

Each account's progress through the lifecycle is documented with screenshots in the `screenshots-images` folder.

### Lifecycle design

| Stage | Trigger | Key tasks | Outcome |
|---|---|---|---|
| Pre-hire (day before start) | Time-based: `employeeHireDate` | Add user to groups (new hires); Enable user account | Account prepared and placed in the new hires group |
| Joiner (start date) | Time-based: `employeeHireDate`, 0 days | Generate Temporary Access Pass (TAP) and send email; Send welcome email | New hire can sign in and register their own authentication methods |
| Mover | Attribute change: `jobTitle`, scoped to titles starting with "Senior" | Remove from new hires group; Add to movers group; Revoke refresh tokens | Previous access removed, new access applied, user must re-authenticate |
| Leaver | [Add: trigger and tasks used] | [Add: for example, move to the leavers quarantine group and revoke sessions] | [Add: access blocked by Conditional Access] |

Group membership at each stage determines which Conditional Access policy applies. Lifecycle Workflows change who is in each group, and Conditional Access evaluates the user's groups at their next sign-in. [Add: a short list of your Conditional Access policies and the grant controls each one requires.]

### Design decisions
- **TAP generated on the start date.** Generating the pass the day before risked it expiring before the employee's first day.
- **Task order matters.** The TAP policy applies only to members of the new hires group, so the group assignment must complete before the TAP task runs. In my first runs the order was reversed and the TAP task failed.
- **Token revocation in the mover workflow.** Removing a user from a group does not end an existing session. Revoking refresh tokens forces a fresh sign-in, so Conditional Access re-evaluates against the new group membership.
- **Static groups for workflow tasks.** The group tasks in Lifecycle Workflows cannot target dynamic groups, so the role groups are assigned groups.

### Issues encountered and resolutions
| Issue | Cause | Resolution |
|---|---|---|
| TAP task failed with an authentication method policy error | The Temporary Access Pass method was not enabled for the users in scope, and the group assignment ran after the TAP task | Enabled TAP in Authentication methods, targeted the new hires group, and reordered tasks so group assignment runs first |
| TAP task failed with "mail attribute missing" | The email recipient accounts had no mail address set | Populated the mail attribute on the recipient accounts and reprocessed |
| Users not processed on the expected day | `employeeHireDate` is evaluated as a UTC timestamp and workflows run on a roughly three-hourly schedule, so the trigger did not match my local calendar day | Allowed for the UTC offset and the schedule interval when planning tests |
| Users shown as Canceled with no failed tasks | Per Microsoft documentation, this status applies when a workflow or its schedule is disabled. [Confirm this matches what happened in your tenant.] Canceled users cannot be reprocessed | Re-enabled the workflow and schedule, then used Run on demand |
| One test account showed errors | I signed in to the account before its onboarding workflow had run, which interfered with the process | Recorded in the screenshots; no change to the design was needed |

### Limitations and production considerations
- **Manual attribute changes.** In a production environment, an HR system would update attributes such as job title and hire date and drive these workflows. In this lab I made those changes manually.
- **One workflow per transition.** Because the group tasks use fixed group selections, each role transition needs its own workflow. Dynamic groups or a custom task extension would reduce this.
- **Least privilege.** The lab was administered with trial-tenant permissions. In production these duties would be split across narrower roles (for example Lifecycle Workflows Administrator, Authentication Policy Administrator, and Conditional Access Administrator), with privileged roles activated through Privileged Identity Management.
- **Licensing.** Lifecycle Workflows requires Microsoft Entra ID Governance (a trial licence was used).

### Future improvements
- Drive lifecycle events from an HR source or the Microsoft Graph API instead of manual edits
- Write a Python script using Microsoft Graph to read a user's current groups and swap them automatically on a role change
- Use dynamic groups or a custom task extension so mover workflows do not need a fixed old and new group
- Add access reviews and Privileged Identity Management to cover ongoing access governance

### Conclusion
This was my first portfolio project on GitHub. I am still developing my knowledge of Azure identity and access management, so these workflows are deliberately straightforward. I tested each stage with the test accounts above, refined the design after each issue, and documented the results with screenshots. The workflows performed as designed. As I gain professional experience, I expect to build on this foundation with more efficient and more fully automated approaches.
