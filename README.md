<p align="center">
<img width="600" alt="osTicket Logo" src="images/osTicket Logo.png" />

</p>

<h1>osTicket Configurations</h1>
This project demonstrates the configuration of core administrative components within an osTicket help desk environment. Building on the initial installation, the project focuses on organizing staff access, ticket routing, and service management by configuring roles, departments, teams, agents, users, service level agreements (SLAs), and help topics. The lab highlights how osTicket uses these components together to control permissions, separate responsibilities, prioritize issues, and support structured ticket workflows in a real-world support environment.<br />


<!--
<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)
-->

<h2>Environments and Technologies Used</h2>
<p align="left">
<img src="https://skillicons.dev/icons?i=azure,windows" />&nbsp;&nbsp;<img src="images/osticket-icon-dark.png" width="48"></p>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- osTicket

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>


**Key Actions**
- Configure roles to control agent permissions and access levels
- Create departments and teams to organize ticket ownership and collaboration
- Add agents and end users to simulate a real support environment
- Define SLAs and help topics to prioritize and route tickets automatically

> [!IMPORTANT]
> Each step includes written instructions followed by a corresponding screenshot.
<br>Expand the **See screenshots** section to view the images.


> [!NOTE] 
> This project builds upon a prior lab where the Azure environment, virtual machine, and osTicket were initially deployed. **ADD LINK HERE**

**Admin/Analyst/Agent Login Page:**
http://localhost/osTicket/scp/login.php 

**End Users osTicket URL:**
http://localhost/osTicket 

<h2>osTicket Configurations</h2> 

<h3>1. CONFIGURE ROLES</h3>
<p>Roles in osTicket group related permissions and are assigned to staff to control what actions they are allowed to perform, let's create a new role. Login to the Admin/Analyst/Agent page. You are currently viewing osTicket as an Agent, observe the Admin link in the top right and select it. From here, select the Agents tab, and select Roles. Select each role and observe each the Permission settings of each.

Select +Add New Role near the top-right of the Roles page. Name our Role "Super Admin", and in the Permissions tab, mark every checkbox in Tickets, Tasks, and Knowledgebase. Select Add Role.</p>

<details><summary>See screenshots</summary>
<img src="images/Step 1a.PNG" width="40%" > <img src="images/Step 1b.PNG" width="40%" >
</details> 

<h3>2. CONFIGURE DEPARTMENTS</h3>
<p>Departments are used for seperating tickets to their assigned departments and ticket visibility, think Help Desk vs SysAdmins vs Networking. 

Let's create a new department. In Admin Panel, Agents tab, select the Departments section. Select +Add New Department. For the Name, type SysAdmins.  Observe the settings and see different options that can be set. Near the top, select the Access tab and observe that we are able to assign Agents to the department if needed. Select Create Dept. We'll assign agents to the department later.</p>

<details><summary>See screenshots</summary>
<img src="images/Step 2a.PNG" width="40%" >
</details> 

<h3>3. CONFIGURE TEAMS</h3>
<p>Teams are used to group staff members from different departments who are responsible for a specific function. For example, in a banking environment, a team might be created for online banking support and include a system administrator, a network technician, and help desk staff working together to resolve related issues. 

Select Teams from the Agents tab, and select +Add New Team.  For the Name, type Online Banking. Observe the settings and see different options that can be set, along with ability to assign Agents. Select Create Team</p>

<details><summary>See screenshots</summary>
<img src="images/Step 3a.PNG" width="40%" >
</details> 


<h3>4. CONFIGURE AGENTS</h3>
<p>Agents are the support staff in osTicket who handle incoming tickets, communicate with users, and update ticket status based on their assigned roles, departments, and teams.

We will create two users. In the Agents tab, select the Agents section, and select +Add New Agent. Create Jane Doe, use any email, set Username: jane_admin select Set Password. Unmark the Send the agent a password reset email, set password as <code>Password123!</code>, unmark the Require password change at next logon checkbox and select Set. In Access tab, assign Jane to SysAdmin Department, Super Admins Role, and in Teams tab, assign to Online Banking Team and select Create. 

<details><summary>See screenshots</summary>
<img src="images/Step 4a.PNG" width="40%" >
</details> 

Create John Doe, username: john_user and set password to the same as Jane's for lab ease, and add user to Support Department, view only Role and select Create.

Before we leave the Admin panel, select the Settings tab, select Users section, and make sure we have the "Require registration and login to create tickets" checkbox unmarked.

<details><summary>See screenshots</summary>
<img src="images/Step 4b.PNG" width="40%" >
</details> 
</p>


<h3>5. CONFIGURE USERS</h3>
<p>To add end users, we need to switch to Agent Panel, select Users tab, select +Add User. Choose any email, for name enter Karen and select Add User. Remember the email as end users will use their email addresses to create tickets, which we'll do in the next lab.</p>

<details><summary>See screenshots</summary>
<img src="images/Step 5a.PNG" width="40%" >
</details> 

<h3>6. CONFIGURE SERVICE LEVEL AGREEMENTS (SLA)</h3>
<p>An SLA defines the expected response and resolution time for tickets based on priority or issue type.

Back to the Admin panel, select Manage tab, and select SLA section Select +Add New SLA Plan. Here we'll create three new SLA Plans. 
 - Sev-A (Grace period: 1 Hour, Schedule: 24/7)
 - Sev-B (Grace period: 4 Hour, Schedule: 24/7)
 - Sev-C (Grace period: 8 Hour, Schedule: Business Hours)
 
 > [!NOTE]
 > With SLAs, we can prioritize tickets by severity and business impact.</p>

<details><summary>See screenshots</summary>
<img src="images/Step 6a.PNG" width="30%" > <img src="images/Step 6b.PNG" width="30%" > <img src="images/Step 6c.PNG" width="30%" >
</details> 

<h3>7. CONFIGURE HELP TOPICS</h3>
<p>Help Topics help categorize incoming tickets and automatically route them to the appropriate department, priority, or workflow. Can be used by end users or agents.

In Admin panel, under Manage tab, select Help Topics section. Select +Add New Help Topics. Create some common topics.
 - Business Critical Outage - Parent Topic: Report a Problem
 - Personal Computer Issues - Parent Topic: Report a Problem
 - Equipment Request        - Parent Topic: General Inquiry
 - Password Reset           - Parent Topic: Report a Problem
 - Other                    - Parent Topic: General Inquiry
 </p>

<details><summary>See screenshots</summary>
<img src="images/Step 7.PNG" width="40%" >
</details> 
