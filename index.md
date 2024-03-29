# Self-Service User Guide

## Overview
ETAIS self-service portal is a single entry point for provisioning and managing computational and storage resources
shared by ETAIS consortium members - UT, TTU, NICPB and HITSA - as well as public cloud providers. It is aimed at
research groups affiliated with Estonian research and development institutions from both public and private sector.

Self-service portal offers research groups a way to collaborate on using and sharing research infrastructure to
minimise bureaucracy of negotiating access, quotas and payments.

The main concepts are as follows:

![Overview](images/etais-structure.png)

* **Organization** is a standalone entity that represents a research group or a company. Organization is responsible for the 
actions of users connected to it in different [roles](#roles).
* **Project** is an entity within an organization that aggregates and isolates teams and resources.
* **Provider** is an entity that represents account in an external service provider.
  * **Private providers** - providers that are available and manageable within a specific organization.
  * **Shared providers** - global providers that are available for all organizations. This includes HPC, cloud and storage infrastructure from ETAIS consortium.
* **Resource** - an entity within a project and a provider. Represents cloud resource. Examples: virtual machine or volume in OpenStack, quota in batch processing queue.

ETAIS self-service portal is based on [Waldur](https://waldur.com) cloud brokerage platform. The latest documentation is available from
[docs.waldur.com](http://docs.waldur.com). Below are key aspects adapted for ETAIS deployment.

## Service Store

Service Store provides a common way to provision resources from both shared and private service providers.

The following resource types are offered at the moment:

* Virtual Private Cloud (VPC) - a pool of resources dedicated to a particular organization.
* Virtual Machines (requires pre-provisioned VPC) - a server with network connectivity for running customer payloads.
* Block Devices (requires pre-provisioned VPC) - persistent volumes for storage of the data.
* Batch (TBD) - access to Slurm-based processing farms.

### VPC Details
* Virtual Private Cloud (VPC) is a compute service that allows procuring and managing a pool of virtualized infrastructure
resources - like RAM, CPU, storage volumes and network resources - required to run virtual machines.
* VPC package does not limit VM count - it depends on VM flavors used and total resources available in a chosen package.
* VPC packages can be upgraded and downgraded at any moment.
* VPC packages are accounted daily based on the price of the largest resource package that was selected during the day.

## User accounts
ETAIS self-service portal supports user accounts coming from [TaaT](http://taat.edu.ee) federated identity system,
which allows to use home organisation accounts for login. Most of the larger education and research institutions in
Estonia are connected to TaaT already.

Alternatively, one can login using an account from [eduGAIN](https://www.geant.org/Services/Trust_identity_and_security/eduGAIN).

Self-Service Portal is available from: [https://minu.etais.ee](https://minu.etais.ee)

![Login](images/login.png)

> *NB! Users need to accept Terms of Service presented on the first login for account activation!*

## Workspaces
ETAIS self-service is built around the concept of workspaces. Workspace defines structural context for the 
user. Each workspace type shows information and possible actions relevant to the user in a certain role.
There are several workspace types available in the system:

* [Organization workspace](#organization workspace)
* [Project workspace](#project workspace)
* [User workspace](#user workspace)

## Roles
Users are connected to the organizations and their projects through roles. Users may have several roles, specific to
each workspace they have access to. Currently the following roles are available in the system:

* Organization owners (owners)
* Project managers (managers)
* System administrators (admins)

User roles are hierarchical in a way that organization owners can do everything that project managers and system administrators can do.

### Organization Owners
* Can access organization workspace.
* Can invite other users to participate in the organization.
* Can create and manage projects, including policies and cost limitations.
* Can manage resource providers and set their availability within projects.
* Can do everything that project managers and system administrators can do.

### Project Managers
* Can access project workspace when appointed by organization owner.
* Can manage project team from the users already connected to the organization.
* Can do everything that system administrators can do.

### System Administrators
* Can access project workspace if appointed by organization owner or project manager.
* Can provision and manage cloud resources.

## User workspace
User workspace is a personal profile management space. It allows to configure user notifications,
SSH public keys, update personal profile data etc.

![User workspace](images/user-dashboard.png)

Menu entries available within user workspace:

* **Dashboard**: listing all organizations and projects where user is participating
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

### Inviting a user
User workspace access and role management can be done on two separate levels:

* Organization workspace allows owners to invite users as organization members and to manage their project role assignments.
* Project workspace allows project managers to assign available organization members a role in their project.

Organization invites can be created by selecting "Team" from the organization workspace menu and clicking on "Invitations" management tab.

![Invites management tab](images/org-team-invite.png)

For creating a new invitation please click on "Invite user" button.

![Creating an invite](images/org-team-invite-create.png)

> *NB! By sending an invite to a user you also accredit this user to become an organization member! In order to complete
the joining process invited user needs to login with the URL provided in the invitation email.*  

"Invite user" form requires target user email address, initial project and role selection. Submit form by clicking on "Invite user" button.

![Invite creation form](images/org-team-invite-form.png)

## Project workspace
Project workspace provides tools and information required for day-to-day work and oversight over the managed IT infrastructure. Access is done via workspace selector in the top section of user interface.

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

> *NB! There are several Virtual Private Cloud providers available from the Service Store. You need to provision at least one VPC package
from suitable provider in order to be able to create virtual machines.*

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

### VPC Security Groups management

![Creating SecGroup - step 1](images/project-vpc-details.png)

![Creating SecGroup - step 2](images/project-vpc-secgroups.png)

![Creating SecGroup - step 3](images/project-vpc-secgroups-create.png)

![Creating SecGroup - step 4](images/project-vpc-secgroups-form.png)