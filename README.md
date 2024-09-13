# Active Directory User Management and Security Lab

The objective of this lab is to get familiar with Active Directory capabilities for User management, group policy, and security management.

In this lab we will create Organizational Units, Groups, and Users. Configure Group Policy to disable USB access and Removable Storage Access, and a group policy for a password policy and account lockout policy. 

Please note this lab builds off of an already created Windows Server 2022 VM with Active Directory installed!

Let's get started!


## Creating Organizational Units, Groups, and Users

Let's start off by creating new Organizational Units or OUs for short.

- Organizational Units are containers used to organize and structure objects within Active Directory, such as users, groups, and computers. OUs help administrators manage policies and permissions efficiently by grouping related objects under one unit.

Open up Active Directory, and right-click our domain. Hover over New and you will see the options we can choose from such as the Organizational Unit, Group, and User. For now click on Organizational Unit.

<img src="https://i.imgur.com/DjFchTE.png" height="70%" width="70%" alt="VirtualBox downloads"/>

We'll name our Organizational Units similar to what we might find in an actual enterprise environment, such as HR, IT, and Sales. Go ahead and name this first one as HR and Click OK when finished.

<img src="https://i.imgur.com/q1iXamJ.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Now that we have our first OU, just repeat the steps for two more OUs and name them IT and Sales.

Once we have created them, we can see under our domain name, we have 3 new OUs.

<img src="https://i.imgur.com/zBgVfqk.png" height="40%" width="40%" alt="VirtualBox downloads"/>

Let's move onto Users to populate these OUs.

- Users are individual accounts created for each person or service accessing resources within the network. User accounts control access to applications, files, and services based on the permissions assigned to them.

Right click on the IT OU and select New > User. A window will pop up allowing us to fill in the information for the new User. Let's name him John Doe and set the logon name to the first initial and then last name. Click Next when finished.

<img src="https://i.imgur.com/dEsSyHP.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Next we will set a password for John Doe. Here you can see there are multiple boxes we can check or uncheck to apply certain options to the account. For now we will leave them alone and maintain the default choices. Click Next, and then on the final menu click Finish if everything looks good.

<img src="https://i.imgur.com/snjN4Xc.png" height="70%" width="70%" alt="VirtualBox downloads"/>

<img src="https://i.imgur.com/ZN8ceav.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Now let's repeat the steps for a second user named Jane Smith. Once complete we will have 2 users in the IT OU.

<img src="https://i.imgur.com/yNEDiIs.png" height="40%" width="40%" alt="VirtualBox downloads"/>

Now that we have our Users, let's create a new Group for them to join!

- Groups: Groups are collections of users, computers, or other AD objects. They simplify management by allowing administrators to assign permissions or policies to multiple objects at once instead of handling each individually. There are two main types:

  - Security Groups: Control access to resources like files or systems.
  - Distribution Groups: Used for email distribution lists.

In the IT OU, right-click and slect New > Group. Create a Security Group and name it IT_Admins. Set the Group Scope to Global and Group type to Security.

<img src="https://i.imgur.com/pvKFT9y.png" height="70%" width="70%" alt="VirtualBox downloads"/>

<img src="https://i.imgur.com/T4kymbq.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Once the group has been created, right-click on IT_Admins, and select Properties in order to add Users to the Group.

<img src="https://i.imgur.com/9UD1QhH.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Type in the names you want to add, in our case it will be Jane Smith and John Doe. We can select Check Names to make sure the names are correct. Do the same for both users.

<img src="https://i.imgur.com/WhQJmQA.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Once added, we can check the IT_Admins Properties to make sure our Users have joined the group successfully.

<img src="https://i.imgur.com/RPPj7uw.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Let's move onto Group Policy!


## Configure Group Policy to Disable USB Access and Removeable Storage Access

Group Policy is a featured used to control the working environment of user accounts and computer accounts. It enables administrators to define security settings, software installations, password policies, desktop settings, and more across multiple users or computers in the network, ensuring consistency and security.

- Group Policy Objects or GPOs are collections of settings that administrators can apply to OUs, groups, or individual computers, and users. GPOs enforce rules such as password complexity, lockout thresholds, software restrictions, or system configurations without needing manual updates on each machine.

So why do we want to disable USB and Removable Storage access through a Group Policy?

- Blocking USBs and Storage Devices helps to stop unauthorized copying of sensitive company data or personal information onto portable drives. USBs and Drives can also carry malware that may infect the machine and move onto the network. Disabling both ensures for a safer environment.

First start off by searching for Group Policy Management in the Start menu and opening it. Once opened, right-click the IT OU in the console and select create a GPO in this Domain and Link it here. Name the policy Disable USB Access.

<img src="https://i.imgur.com/cAtynx6.png" height="70%" width="70%" alt="VirtualBox downloads"/>

<img src="https://i.imgur.com/hTfF031.png" height="40%" width="40%" alt="VirtualBox downloads"/>

Click OK when finished. Next we have to edit the GPO. Right-click the GPO and click Edit. 

Navigate to Computer Configuration > Policies > Administrative Templates > System > Removable Storage Access

Enable the All Removable Storage Classes: Deny all access

<img src="https://i.imgur.com/benctXJ.png" height="70%" width="70%" alt="VirtualBox downloads"/>

<img src="https://i.imgur.com/ptTgRLK.png" height="70%" width="70%" alt="VirtualBox downloads"/>

<img src="https://i.imgur.com/XvCWVVo.png" height="40%" width="40%" alt="VirtualBox downloads"/>

We have successfully created a Group Policy to deny Removable Storage Access! Let's now create one for our Password Policy and Account Lockout Policy.


## Password Policy and Account Lockout Policy

Creating a Password Policy and Account Lockout Policy helps improve security:

- Password Policy: Enforces rules like complexity, length, and expiration for user passwords. This ensures that users create strong, harder to guess passwords, reducing the chance of unauthorized access to sensitive systems or data.

- Account Lockout Policy: Locks a user account after a set number of incorrect login attempts. This prevents attackers from using brute-force methods to guess passwords, improving protection against attacks targeting user accounts. 

So to get started, open Group Policy Management and Create a new GPO by right-clicking the domain and selecting Create a GPO in this Domain, and Link it here.

<img src="https://i.imgur.com/NmQWFQO.png" height="40%" width="40%" alt="VirtualBox downloads"/>

Next, navigate to Computer Configuration > Policies > Windows Settings > Security Settings > Account Policies > Password Policy.

<img src="https://i.imgur.com/iA5NMCo.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Here we will confiugre multiple policies to create a well balanced password GPO. First we will click and edit the Minimum password length properties to be 8 characters. This means a minimum of 8 characters is needed for every password.

<img src="https://i.imgur.com/bOvIZ8S.png" height="70%" width="70%" alt="VirtualBox downloads"/>

<img src="https://i.imgur.com/U9e0DBh.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Next we will set a Maximum Password Age. This means every password will expire and need to be changed after every 60 days in our case.

<img src="https://i.imgur.com/nDuElcU.png" height="70%" width="70%" alt="VirtualBox downloads"/>

After some adjustments here is what we have for our Password policies:

<img src="https://i.imgur.com/jIiM8ui.png" height="70%" width="70%" alt="VirtualBox downloads"/>

We have enabled the following:

- Enforce password history - 0 passwords remembered: Users can reuse their previous passwords immediately, as no history of old passwords is kept.
- Maximum password age - 60 days: Users are required to change their passwords every 60 days.
- Minimum password age - 30 days: Users must keep a password for at least 30 days before changing it.
- Minimum password length - 8 characters: Passwords must be at least 8 characters long.
- Password must meet complexity requirements - Enabled: Passwords must include a combination of letters, numbers, and symbols to ensure they are harder to guess.

These policies help ensure password security by requiring regular updates and strong password criteria.

Now that we have completed the password policies, lets enable some Account Lockout Policies. Beneath the Password Policy selection in the left pane of the Group Policy Management Editor is the Account Lockout Policy. 

Here we can adjust the Account lockout duration, Account lockout threshold, and Reset account lockout counter after (a certain amount of time). 

<img src="https://i.imgur.com/90I2AXb.png" height="70%" width="70%" alt="VirtualBox downloads"/>

Here’s a simple explanation of the account lockout settings:

- Account lockout duration: The amount of time (in minutes) that a user’s account remains locked after too many failed login attempts. After this time, the account unlocks automatically.
- Account lockout threshold: The number of failed login attempts before the account gets locked. For example, if this is set to 5, the account will lock after 5 incorrect password attempts.
- Reset account lockout counter after: The time (in minutes) that must pass before the counter resets back to zero. If a user enters incorrect passwords over time, the counter will reset if they don’t reach the threshold within the set time.
  
These settings help protect against brute-force attacks by locking accounts after multiple failed attempts.


## Conclusion
We have successfully implemented user and group management, and enforced security policies through Group Policy to our Active Directory environment. This project replicates a real-world IT infrastructure used in businesses to manage user access and security across an organization. 
