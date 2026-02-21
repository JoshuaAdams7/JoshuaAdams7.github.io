---
layout: default
---

# Network security Groups

In this scenario, we want to be able to configure an inbound rule attached to a Network Security Group (NSG) to allow web traffic.

# Technologies

* Virtual Networks.
* Virtual Machines.
* Network Security Groups (NSG)

# Setting up a VM

First, we need to create a resource group to house all the resources required. 

Go to portal.azure.com > virtual machines > create > virtual machine.

![Resource Group](./resource_group.png)

Select an appropriate subscription > click on Create new under Resource group, enter a name for the new resource group and click on OK > enter a name for the VM > select the region used above > select an appropriate image for the VM – in this case, Windows Server was used > enter appropriate credentials for the admin account associated with the VM > select None next to Public inbound ports.

![Resource Group](./resource_group.png)

![Resource Group](./resource_group.png)

Click on the Networking tab > leave the default Virtual network and Sunet configuration select Create new for Public IP and leave the defaults.

![Resource Group](./resource_group.png)

Note: You can optionally click on the Management tab and enable the auto shutdown feature.

![Resource Group](./resource_group.png)

Click on Monitoring > select Disable for the Boot diagnostics feature.

![Resource Group](./resource_group.png)

Click on Review + create > click on Create.

After the resources have finished being provisioned, click on Go to resource > click on Connect > Connect. 

![Resource Group](./resource_group.png)

Click on Check access under Connection prerequisites.

![Resource Group](./resource_group.png)

Connectivity via port 3389 (RDP) is currently blocked because we didn’t configure this when setting up the VM. 

Click on the Network settings menu item > click on Create port rule > click on Inbound port rule. 

![Resource Group](./resource_group.png)

Select My IP address as the Source > enter * for the Source port range > selecy Any for Destination > select Custom for Service (although you could select RDP) > enter 3389 for the Destination port range > select TCP for the Protocol > select Allow for the Action > enter a priority number > enter a name for the rule > click on Save.

![Resource Group](./resource_group.png)

Go back to the Connect menu item > click on Check access and you should now see that port 3389 is accessible.

![Resource Group](./resource_group.png)

Click on Download RDP File > open the RDP file > click on Connect > enter the password for the administrator account associated with the VM > click Yes on the warning message box. 

![Resource Group](./resource_group.png)

# Installing IIS on the VM

Next, we need to set up the IIS role on the newly created VM.

Open Server Manager > click on Dashboard > click on Add roles and features.

![Resource Group](./resource_group.png)

Click Next on the Before you begin screen > select the Role-based or feature-based installation radio button > click on Next.

![Resource Group](./resource_group.png)

Click the Select a server from the server pool radio button > click on Next.

![Resource Group](./resource_group.png)

Select the Web Server (IIS) checkbox on the Server Roles screen.

![Resource Group](./resource_group.png)

In the Add Roles and Features Wizard popup box, click on the Include management tools checkbox > click on Add Features.

![Resource Group](./resource_group.png)

Click Next on both the Server Roles, Features, Web Server Role (IIS) and Role Services screens > click on Install on the Confirmation screen.

![Resource Group](./resource_group.png)

Once you see the Installation succeeded on... message, click on Close.

![Resource Group](./resource_group.png)

Reopen the Add roles and features menu > repeat the above steps up to the Server Roles screen > select the IIS 6 Management Compatibility checkbox > click Next through the screens and eventually click on Install on the Confirmation screen.

![Resource Group](./resource_group.png)

![Resource Group](./resource_group.png)

As before, click on Close after installation has finished. 

Open up a web browser on the VM and navigate to http://localhost/.

![Resource Group](./resource_group.png)

Repeat the above process but try navigating to http://<public-ip-for-vm>.

![Resource Group](./resource_group.png)

# Adding an Inbound NSG Rule for Web (Port 80) Traffic

Next, we need to...

Go to portal.azure.com > navigate back to the VM > make a note of the VM’s private IP address under Network settings. 

![Resource Group](./resource_group.png)

Click on Create port rule > click on Inbound port rule > select service tag as the Source > select Internet the Source service tag > enter * for the Source port range > select IP Addresses as the Destination > enter the private IP address of the VM > select Custom for Service > enter 80 for Destination port range > select TCP for Protocol > select Allow for the Action > enter a priority number > enter a name for the rule > click on Add.

![Resource Group](./resource_group.png)

Now, if we repeat the process of trying to navigate to http://<public-ip-for-vm>, it will work due to the new rule that was created. 

![Resource Group](./resource_group.png)

# Resources

* [Microsoft Azure Security Engineer Associate (AZ-500) Professional Certificate](https://www.coursera.org/professional-certificates/microsoft-azure-security-engineer-associate)

