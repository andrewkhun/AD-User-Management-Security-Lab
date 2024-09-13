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

<img src="https://i.imgur.com/zBgVfqk.png" height="70%" width="70%" alt="VirtualBox downloads"/>
