# Project Blueprint: [Project ##] - [Project Name]
 
> **How to read this template**
>
> - **Required** fields must be filled in. **Optional** fields can be skipped, or marked `N/A` with a one-line reason.
> - Each section shows **when** to complete it:
>   - `Before review`: complete before you ask for an architecture review.
>   - `Draft before review`: write a first version before the review, then update it while you build.
>   - `During / after build`: fill in while you implement or once you finish.
> - Replace every `[placeholder]` and delete the guiding-question blocks once a section is done.
> - **Never commit sensitive data.** Redact AWS account IDs, access keys, ARNs that contain your account number, public IPs you own, and email addresses. Use `123456789012` or `<ACCOUNT_ID>` in examples and screenshots.
 
---
 
## Document Info
 
| Field | Value |
|---|---|
| Project number and name (Required) | [Project ## - Name] |
| Status (Required) | [Planning / In Review / Approved / Implementing / Testing / Completed] |
| Blueprint version (Required) | [v0.1] |
| Start date / Target completion (Required) | [YYYY-MM-DD] / [YYYY-MM-DD] |
| AWS Region (Required) | [e.g., region code] |
| Builds on (Optional) | [Previous project(s) this extends, or "None"] |
| Related CCP exam domains (Optional) | [Cloud Concepts / Security and Compliance / Cloud Technology and Services / Billing, Pricing, and Support] |
| GitHub folder (Optional) | [Link or path] |
 
---
 
## 1. Project Overview
`Required` · `Before review`
 
> Guiding questions:
> - In two or three sentences, what are you building?
> - Who or what would use this in the real world?
> - What new AWS skill or concept does this project add compared to your previous one?
 
**Summary:** [Short description]
 
**Real-world use case:** [Who would use this and why]
 
**New skills this project introduces:** [List]
 
---
 
## 2. Problem Statement
`Required` · `Before review`
 
> Guiding questions:
> - What problem or need does this project address?
> - What happens if this problem is not solved (risk, cost, downtime, manual effort)?
> - Is the problem realistic for a company of any size, or only for a specific scenario? Say which.
 
[Describe the problem in plain language. Avoid naming AWS services here; focus on the need, not the solution.]
 
---
 
## 3. Project Objectives
`Required` · `Before review`
 
> Guiding questions:
> - What must be true when this project is finished?
> - Is each objective specific and checkable? ("Learn VPCs" is too vague. "Build a VPC where only the web tier is reachable from the internet" is checkable.)
> - Separate what the **system** should achieve from what **you** want to learn.
 
**System objectives**
1. [Objective]
2. [Objective]

**Learning objectives**
1. [Concept or skill you want to understand]
2. [Concept or skill]
---
 
## 4. Functional Requirements
`Required` · `Before review`
 
> Guiding questions:
> - What must the system **do**? Think in actions: "accepts", "stores", "routes", "blocks", "notifies".
> - Can each requirement be tested? If you cannot think of a test for it, rewrite it.
> - Give each requirement an ID so you can link it to tests in Section 13.
 
| ID | Requirement | Priority |
|---|---|---|
| FR-1 | [The system must...] | [Must / Should / Could] |
| FR-2 | [The system must...] | [Must / Should / Could] |
 
---
 
## 5. Non-Functional Requirements
`Required` · `Before review` (pick only the categories that apply)
 
> Guiding questions:
> - How well must the system work, not just what it does?
> - Which of these actually matter for this project's scope? Do not add availability targets to a single-instance learning lab just to fill the table.
> - Is each requirement measurable?
 
| ID | Category | Requirement | How it will be measured |
|---|---|---|---|
| NFR-1 | Security | [e.g., No resource in a private subnet has a public IP] | [Method] |
| NFR-2 | Cost | [e.g., Total cost stays under $X for the project] | [Billing dashboard / Budgets] |
| NFR-3 | [Availability / Performance / Scalability / Maintainability / Recoverability] | [Requirement] | [Method] |
 
---
 
## 6. Project Scope and Limitations
`Required` · `Before review`
 
> Guiding questions:
> - What is clearly **in** this project?
> - What are you deliberately leaving **out**, and why (cost, complexity, saved for a later project)?
> - What assumptions are you making (e.g., single Region, manual console setup, no custom domain)?
> - What known limitation would you need to fix before this could run in production?
 
**In scope**
- [Item]

**Out of scope (and why)**
- [Item]: [Reason]

**Assumptions**
- [Assumption]

**Known limitations**
- [Limitation]
---
 
## 7. Proposed AWS Services and Their Responsibilities
`Required` · `Before review`
 
> Guiding questions:
> - For each service: what is its single job in this design?
> - Why this service and not an alternative? (e.g., why this compute option over another; why this storage type over another)
> - Is any service here only because it looks impressive? If so, remove it.
> - Does any service run all the time and charge per hour even when idle?
 
| AWS Service / Component | Responsibility in this project | Why this choice (alternative considered) | Cost note (see Section 10) |
|---|---|---|---|
| [Service] | [What it does here] | [Reason] / [Alternative] | [Free Tier / charges] |
| [Service] | [What it does here] | [Reason] / [Alternative] | [Free Tier / charges] |
 
---
 
## 8. System Workflow and Communication Flow
`Required` · `Before review`
 
> Guiding questions:
> - Walk through a single request or event from start to finish. What touches it, in what order?
> - Which traffic is **allowed**, and which must be **blocked**? Blocked flows are as important as allowed ones.
> - Which ports and protocols are needed? Is any port open wider than necessary?
> - Where does traffic cross a boundary (internet to VPC, public subnet to private subnet, service to service)?
 
**Step-by-step flow**
1. [Actor/source] sends [what] to [component]
2. [Component] [does what] and forwards to [component]
3. [...]

**Traffic rules**

| Source | Destination | Protocol / Port | Path (e.g., IGW, NAT, endpoint, internal) | Allowed or Blocked | Enforced by |
|---|---|---|---|---|---|
| [Source] | [Destination] | [TCP 443] | [Path] | [Allowed] | [Security group / NACL / IAM policy / route table] |
| [Source] | [Destination] | [Protocol/Port] | [Path] | [Blocked] | [Control] |
 
**Admin / management access** (Required if you manage any instances or resources directly)
- How will you access resources for administration? [e.g., Session Manager, bastion host, console only]
- Why this method? [Reason]
---
 
## 9. Security Requirements
`Required` · `Before review`
 
> For each item, state what you will do, or write `N/A: [reason]`. Not every item applies to every project.
 
### 9.1 Identity and Access (IAM)
- [ ] Root account not used for this project; MFA enabled on root and on your IAM user
- [ ] Which IAM users, roles, or policies will this project create? [List]
- [ ] Do AWS services access other services through **roles**, not stored access keys? [How]
- [ ] Least privilege: which permissions does each role actually need? Avoid `*` actions and `*` resources unless you can justify them. [Notes]
### 9.2 Network Security
- [ ] Which resources are publicly reachable, and why must they be? [List]
- [ ] Security group rules reference specific ports and sources (or other security groups), not `0.0.0.0/0`, unless the resource is meant to be public. [Notes]
- [ ] NACLs: used or left at default? Why? [Notes]
- [ ] No SSH/RDP open to the whole internet. [Approach]
### 9.3 Data Protection and Encryption
- [ ] What data is stored, and how sensitive is it? [Notes]
- [ ] Encryption at rest: [Enabled how / N/A]
- [ ] Encryption in transit: [HTTPS/TLS where / N/A]
- [ ] Public access blocked on storage unless intentionally public. [Notes]
### 9.4 Secrets Management
- [ ] Where will passwords, keys, or connection strings live? (Never in code, user data scripts, or GitHub.) [Approach]
- [ ] `.gitignore` covers credential files, `.env`, Terraform state, key pairs. [Confirmed]
### 9.5 Logging and Monitoring (Optional for early projects)
- [ ] CloudTrail enabled for the account? [Yes / No]
- [ ] Any alarms, logs, or flow logs for this project? [List / N/A]
### 9.6 Known Security Gaps
- [Anything you are knowingly leaving insecure for scope reasons, and what the production fix would be]
---
 
## 10. Cost Constraints and Considerations
`Required` · `Before review`
 
> Rule: never assume something is free because it has a Free Tier. Check the pricing page and your account's Free Tier usage before building.
 
### 10.1 Budget
| Field | Value |
|---|---|
| Account plan (Required) | [Free plan / Paid plan] |
| Credits remaining at project start (Required) | [$ amount, from Billing console] |
| Maximum spend allowed for this project (Required) | [$ amount] |
| AWS Budgets alert configured (Required) | [Yes: threshold $X / No] |
 
### 10.2 Cost Breakdown
| Service / Resource | Pricing model (per hour, per GB, per request) | Free Tier coverage (Always Free / Free plan credits / 12-month / None) | Estimated cost for project duration | Hidden-charge risk |
|---|---|---|---|---|
| [Resource] | [Model] | [Coverage] | [$] | [e.g., charges while idle, data transfer, public IPv4, NAT gateway hours, snapshots left behind] |
 
**Estimation method:** [AWS Pricing Calculator / pricing page / Free Tier dashboard]
 
**Cheaper alternatives considered:** [Alternative and trade-off]
 
### 10.3 Cleanup Plan
> Guiding questions:
> - What order must resources be deleted in (dependencies)?
> - What is easy to forget (Elastic IPs, NAT gateways, EBS volumes, snapshots, log groups, S3 objects)?
> - Will you tear down after each session, or keep it running? What does keeping it running cost per day?
 
| Order | Resource to delete | Verified deleted (date) |
|---|---|---|
| 1 | [Resource] | [ ] |
| 2 | [Resource] | [ ] |
 
- [ ] Checked Billing and Cost Explorer 24 to 48 hours after cleanup for leftover charges
- [ ] Final actual cost recorded: [$ amount]
---
 
## 11. Proposed Architecture Diagram
`Required` · `Before review`
 
> You create this diagram yourself. Export it as PNG or SVG and store the editable source file too (e.g., `.drawio`).
 
![Architecture diagram](./diagrams/[project-name]-architecture-v1.png)
 
| Field | Value |
|---|---|
| Diagram tool | [e.g., draw.io, Excalidraw, Lucidchart] |
| Diagram version | [v1] |
| Source file | [./diagrams/[file].drawio] |
 
**Diagram checklist** (include whatever applies to this project)
- [ ] Region and Availability Zone(s) shown
- [ ] VPC, subnets, and their CIDR ranges labeled
- [ ] Public vs private boundaries clear
- [ ] Gateways, route paths, and endpoints shown
- [ ] Security boundaries (security groups) indicated
- [ ] Arrows show traffic direction and match Section 8
- [ ] Official AWS architecture icons used
- [ ] No real account IDs, IPs, or ARNs

**Diagram explanation:** [Walk through the diagram in a short paragraph. Someone who only reads this should understand how the parts connect.]
 
---
 
## 12. Implementation Milestones
`Draft before review` · update `During build`
 
> Guiding questions:
> - What are the logical build stages? Each should end in something you can verify.
> - Where are good checkpoints to stop, test, and (if needed) ask for a review?
> - Which milestones create billable resources? Plan cleanup around them.
 
| # | Milestone | Deliverable / evidence | Done when | Status |
|---|---|---|---|---|
| M1 | [e.g., Base setup] | [Screenshot, CLI output, config file] | [Verifiable condition] | [Not started / In progress / Done] |
| M2 | [Milestone] | [Evidence] | [Condition] | [Status] |
| M3 | [Milestone] | [Evidence] | [Condition] | [Status] |
 
---
 
## 13. Testing and Acceptance Criteria
Test plan: `Before review` · Results: `During / after build`
 
> Guiding questions:
> - Does every functional requirement (FR) and important non-functional requirement (NFR) have at least one test?
> - Do you have **negative tests** that prove things are blocked when they should be?
> - What evidence will you save (redacted screenshots, command output)?
 
| Test ID | Requirement | What is tested | Method (steps or command) | Expected result | Actual result | Pass / Fail |
|---|---|---|---|---|---|---|
| T-1 | FR-1 | [Behavior] | [How] | [Expected] | [Fill in during testing] | [ ] |
| T-2 | NFR-1 | [Negative test: something should be blocked] | [How] | [Blocked / denied] | [Fill in] | [ ] |
 
**Acceptance criteria** (the project is complete only when all are checked)
- [ ] All "Must" functional requirements pass their tests
- [ ] Security requirements in Section 9 are implemented or their gaps are documented
- [ ] Actual cost stays within the budget in Section 10
- [ ] Cleanup is completed and verified (unless intentionally kept running, with reason)
- [ ] Design Change Log (Appendix A) is up to date
- [ ] You can explain every component and decision without notes
- [ ] [Project-specific criterion]
---
 
## 14. Risks and Potential Failure Points
`Draft before review` · update `During build`
 
> Guiding questions:
> - What single component, if it fails, breaks the whole system?
> - What mistakes could cost money or expose data (open security group, public bucket, forgotten resource)?
> - Which risks are acceptable for a learning project, and which are not?
 
| Risk / failure point | Type (Availability / Security / Cost / Operational) | Likelihood (L/M/H) | Impact (L/M/H) | Mitigation or accepted? | How you would detect it |
|---|---|---|---|---|---|
| [Risk] | [Type] | [L/M/H] | [L/M/H] | [Action / "Accepted: reason"] | [Detection] |
 
---
 
## 15. Future Improvements
`Optional before review` · finalize `After build`
 
> Guiding questions:
> - What would you change to make this production-ready?
> - Which limitations from Section 6 or gaps from Section 9.6 should be fixed next?
> - What from this project should carry into the next one?
 
| Improvement | Why it matters | Carry into next project? |
|---|---|---|
| [Improvement] | [Benefit] | [Yes: Project ## / Later / No] |
 
---
 
## Appendix A: Design Change Log
`During / after build` · Required
 
> Record every meaningful difference between the approved design and what you actually built. These entries are good material for the "Mistakes and Improvements" section of your README and for interview stories.
 
| Date | Section affected | Planned (approved design) | Actual (what was built) | Reason for change | Impact (security / cost / scope) | Diagram updated? |
|---|---|---|---|---|---|---|
| [YYYY-MM-DD] | [e.g., 8] | [Planned] | [Actual] | [Why] | [Impact] | [Yes: v2 / No] |
 
## Appendix B: Architecture Review Record
`Before / during review` · Required
 
| Review round | Date | Blueprint / diagram version | Critical issues | Recommended improvements | Outcome |
|---|---|---|---|---|---|
| 1 | [YYYY-MM-DD] | [v0.1 / v1] | [Summary] | [Summary] | [Revise / Approved to implement] |
 