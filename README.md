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
