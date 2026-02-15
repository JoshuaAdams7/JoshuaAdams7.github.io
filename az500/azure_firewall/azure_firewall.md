---
layout: default
---

# Tasks

# Resource group creation

First, we need to create a resource group to house all the resources required for this example. 

* Go to portal.azure.com.
* Resource groups.
* Click on Create.

![Admin Role Check](./admin_role_check.png)

* Select a subscription.
* Enter a name for the resource groupselect a region.
* Review + create.
* Click on Create.

![Admin Role Check](./admin_role_check.png)

# Virtual network creation

Next, we need to deploy a virtual network. 

* Go to portal.azure.com.
* Virtual networks.
* Click on Create.

![Admin Role Check](./admin_role_check.png)

* Select a subscription.
* Select the resource group created earlier.
* Select the same region as above.
* Enter a name for the virtual network.
* Click on the IP Addresses tab.

![Admin Role Check](./admin_role_check.png)

* Click on the initial default subnet name.
* Change the subnet purpose to Azure firewall.
* Update the IP address range as needed.
* Click on Save.

![Admin Role Check](./admin_role_check.png)

* Click on Add a subnet.
* Enter a name for the subnet.
* Update the IP address range as needed.
* Click on Add.

![Admin Role Check](./admin_role_check.png)

* Click on Review + create.
* Click on Create.

# Creating a VM

* Go to portal.azure.com.
* Virtual machines.
* Create.
* Virtual machine.

![Admin Role Check](./admin_role_check.png)

* Under the basics tab, select the resource group from earlier.
* Enter a name for the VM.
* Select the same region as above.
* Select an image to be deployed.
* Define the VM size.

![Admin Role Check](./admin_role_check.png)

![Admin Role Check](./admin_role_check.png)

* Choose the username and password for the administrator account attached to the VM.
* Select None for the Public inbound ports option.

![Admin Role Check](./admin_role_check.png)

* Click on the Networking tab.
* Select the virtual network that was created earlier.
* Select the appropriate subnet.
* Change the Public IP option to None.

![Admin Role Check](./admin_role_check.png)

Optionally, you can click to open the Management tab and enable the auto-shutdown feature, which may help to prevent higher costs.

![Admin Role Check](./admin_role_check.png)

* Click on the Monitoring tab.
* Select the Disable option next to Boot diagnostics.

![Admin Role Check](./admin_role_check.png)

* Click on Review.
* Create.
* Create.

After deployment of the VM has been completed, click on Go to resource and make a note of the Private IP attached to it.

![Admin Role Check](./admin_role_check.png)

# Creating a Firewall

# Testing

# Resources

