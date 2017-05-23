# Self-Service User Guide

## Overview
Self-Service Portal implements One-Stop-Shop for users in order to procure and manage cloud based resources delivered from multiple providers. It also enables users to participate in multiple roles, linked to multiple structural units, like organizations and their projects. For example, single user can act as Organization-A owner and also as Organization-B Project-X system administrator. Switching structual contexts and user roles is based on workspaces concept. 
![Overview](images/homeport-interactions.png)

Usually, each organization has multiple projects, and each project has multiple resources, managed by multiple users in different roles. Organizations are also structural units who can receive and pay resource usage bills. Projects are Organization sub-containers for grouping together provisioned resources, managing users and project level policies -- as a dedicated project workspace. Resource providers are managed at organization level and can be made available within multiple projects.


### Workspaces
Workspaces define and limit structural context for the user. They also implement management views and enforce access rights, depending on the user role attached. There are several workspace types available in the system:

* [Organization workspace](#organization-workspace)
* [Project workspace](#project-workspace)
* [User (profile) workspace](#user-workspace)

### Roles
Users are connected to the organizations and their projects through roles. Users may have several roles, specific to each workspace they have been credited access to. Currently the following roles are available in the system:

* Organization owners (owner)
* Project managers (manager)
* System administators (admin)

User roles are hierarchical - ie organization owners can do everything that project managers and system administrators can do.

#### Organization Owners
* Can access organization workspace
* Can invite and accredit other users to participate in the Organization (ie to become an organization member)
* Can manage organization members access to project workspaces 
* Can manage projects
* Can manage resource providers and set their availability within projects
* Can order resources from Service Store
* Can do everything that project managers and system administrators can do

#### Project Managers
* Can access project workspace if appointed by organization owner
* Can manage project team, limited to organization Members
* Can order resources from Service Store
* Can do everything that system administrators can do

#### System Administrators
* Can access project workspace if appointed by organization owner or project manager
* Can provision and manage cloud resources
  
### Service Store
Brokered services are enlisted in the Service Store catalog, made available for browsing and resource provisioning.  

#### VPC Service
* Virtual Private Cloud aka VPC is a compute service that allows you to procure and manage a pool of virtualized infrastructure resources - like RAM, CPU, storage volumes and network resources - required to run virtual machines
* VPC package does not limit VM count - in reality it depends on VM flavors used and total resources available within currently selected VPC package
* Smallest available VPC resource package is Starter.Small, offering 10 vCPU cores, 20GB RAM and 200GB of storage - allowing to create up to 10 VMs (limited by vCPUs in this case)
* VPC packages can be upgraded and downgraded at any moment
* VPC packages are accounted daily - based on the price of the largest resource package that was selected on that day
* Technically VPC represents Openstack Tenant (in single location)

## Account registration and login
Accepted user authentication methods are:

*  internal, password based accounts
*  federated TAAT accounts (http://taat.edu.ee/)

Self-Service Portal is available from: [https://minu.etais.ee](https://minu.etais.ee)


![Login](images/login.png)

> *NB! Users need to accept Terms of Service presented on the first login for account activation!*

## User workspace
User workspace is a personal account profile management space, presented after first login. It allows to configure user notifications, SSH public keys, update personal profile data, etc. 

![User workspace](images/user-dashboard.png)

Menu entries available within user workspace:

* **Dashboard**: listing all organizations and their projects where user is participating, in appointed roles
* **Audit logs**: listing events related to user
* **SSH keys**: managing public SSH keys for the user
* **Notifications**: managing notifications for the user
* **Manage**: editing and updating user profile details

### Accessing user workspace

Access is done by clicking on user avatar and selecting one of the entries from a pop-up menu.

![User profile link](images/user-profile-link.png)

## Organization and project workspace selector
Navigation between different organization and project workspaces are done with the help of the workspace selector available in the header row.

![Workspace selector button](images/workspace-selector-button.png)

### Selecting organization workspace
![Organization workspace selection](images/workspace-selector-org-selection.png)

### Selecting project workspace
![Project workspace selection](images/workspace-selector-project-selection.png)

## Organization workspace
Organization workspace allows to manage projects, subscriptions to resource providers and organization members. It is also intended to provide summary, accounting and auditing information regarding organization, projects and providers. To be able to access organization workspace, you need to have a organization owner role.

![Organization workspace](images/org-dashboard.png)

Menu entries available within organization workspace:

* **Dashboard**: overview of managed resources and projects
* **Providers**: resource providers management (system and provisioned providers)
* **Projects**: projects management
* **Service store**: catalog of resources and providers, available for provisioning 
* **Analytics**: resource usage reports
* **Audit logs**: event logs related to organization, its projects and resources
* **Team**: management of organization members and their project/role accreditations
* **Accounting**: resource usage accounting information
* **Manage**: management of organization details

### Adding a project
Projects can be added by selecting "Projects" from the menu and clicking on "Add project" button. 

![Adding a project](images/project-add.png)

"Create project" form requires you to enter project name and optionally project description. If you need to attach security class label for the project you should select one from the list presented. Submit form by clicking on "Add project" button.

![Create project form](images/project-add-form.png)

### Inviting and accrediting users
User workspace access and role management can be done on two separate levels:

* Organization workspace allows owners to invite and accredit users as organization members and to manage their project/role assignment(s)
* Project workspace allows project managers to select users from available organization members into project team and to assign a project role 

Organization invites can be created by selecting "Team" from the organization workspace menu and clicking on "Invitations" management tab.

![Invites management tab](images/org-team-invite.png)

For creating a new invitation please click on "Invite user" button.

![Creating an invite](images/org-team-invite-create.png)

> *NB! By sending an invite to a user you also accredit this user to become an organization member! In order to complete the joining process target user needs to login with the URL provided in the invitation.*  

"Invite user" form requires target user email address, initial project and role selection. Submit form by clicking on "Invite user" button.

![Invite creation form](images/org-team-invite-form.png)

## Project workspace
Project workspace provides tools and information required for day-to-day work and oversight over the managed IT infrastructure. Access is done via workspace selector in top section of user interface.

![Project workspace](images/project-dashboard.png)

Menu entries available within project dashboard:

* **Dashboard**: overview of project resources and latest events
* **Service store**: catalog of resources and providers, available for provisioning
* **Resources**: provisioned resource listings and management views by resource category (VMs, Private Clouds, Storage, etc.)
* **Audit logs**: event logs related to project and its resources
* **Team**: project team management

### Adding a VPC
Virtual Private Cloud resource package can be added by selecting "Resources" and "Private Clouds" from the menu and clicking on "Add private cloud" button.

![Add VPC](images/project-vpc-add.png)

> *NB! There are several Virtual Private Cloud providers available from the Service Store. You need to provision at least one VPC package from suitable provider in order to be able to create virtual machines.*

![Selecting VPC provider](images/project-vpc-add-provider-select.png)

![Adding VPC provider - step 1](images/project-vpc-add-form-step1.png)

![Adding VPC provider - step 2](images/project-vpc-add-form-step2.png)

![Adding VPC provider - step 3](images/project-vpc-add-form-step3.png)

### Adding a VM

![Adding VM - step 1](images/project-vm-add-form-step1.png)

![Adding VM - step 2](images/project-vm-add-form-step2.png)

![Adding VM - step 3](images/project-vm-add-form-step3.png)

![Adding VM - step 4](images/project-vm-add-form-step4.png)

![Adding VM - step 5](images/project-vm-add-form-step5.png)

![Adding VM - step 6](images/project-vm-add-form-step6.png)

![Adding VM - step 7](images/project-vm-add-form-step7.png)

![Adding VM - step 8](images/project-vm-add-form-step8.png)

![Adding VM - step 9](images/project-vm-add-form-step9.png)

### Security Groups management
