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

* Go to portal.azure.com.
* Firewalls.
* Create.

![Admin Role Check](./admin_role_check.png)

* Select the resource group that was created earlier.
* Enter a name for the firewall.
* Select the same region as above.
* Select the Standard SKU option.

![Admin Role Check](./admin_role_check.png)

* Select the Use Firewall rules (classic) to manage this firewall option next to Firewall management.
* Select the Use existing option next to Choose a virtual network and select the virtual network that was created earlier.
* Create a new Public IP.
* Uncheck the box next to Enable Firewall Management NIC.

![Admin Role Check](./admin_role_check.png)

* Click on Review.
* Create.
* Create. 

After the firewall has been deployed, click on Go to resource and make a note of both the private and public IP addresses.

![Admin Role Check](./admin_role_check.png)

Note: You can click on the link provided to locate the public IP address. 

Next, we need to set up a default route. 

* Go to portal.azure.com.
* Route Tables.
* Create.

![Admin Role Check](./admin_role_check.png)

* Select the resource group that was created earlier.
* Enter a name for the route table.
* Select the same region as above.
* Click on Create + review.
* Create.

![Admin Role Check](./admin_role_check.png)

After deployment, click on Go to resource. 

* Navigate to the Subnets tab.
* Associate.

![Admin Role Check](./admin_role_check.png)

* Select the virtual network that was created earlier.
* Select the subnet that contains the VM.
* Click on OK.

![Admin Role Check](./admin_role_check.png)

* Navigate to the Routes tab.
* Add.

![Admin Role Check](./admin_role_check.png)

* Enter a name for the route.
* Select IP Addresses as the Destination type.
* Enter 0.0.0.0/0 as the CIDR range.
* Select Virtual appliance as the Next hop type.
* Enter the private IP address of the firewall.
* Click on Add.

![Admin Role Check](./admin_role_check.png)

* Navigate back to the firewall.
* Settings tab > Rules (classic).
* Application rule collection tab.
* Add application rule collection.

![Admin Role Check](./admin_role_check.png)

* Enter a name for the rule collection.
* Enter a priority number.
* Select Allow next to Action.
* Entera name for the Target FQDN.
* Select IP address for Source type.
* Enter the network address of the subnet containing the VM for Source.
* Enter http, https for port.
* Enter www.google.com for Target FQDNs.
* Elick on Add.

![Admin Role Check](./admin_role_check.png)

Next, we need to allow access to external DNS servers. 

* Navigate back to the firewall.
* Settings tab.
* Rules (classic).
* Network rule collection tab.
* Add network rule collection.

![Admin Role Check](./admin_role_check.png)

* Enter a name for the rule collection.
* Enter a priority number.
* Select Allow next to Action.
* Enter a name for the IP Address.
* Select UPD for Protocol.
* Select IP address for source.
* Select IP address for Destination type.
* Enter 209.244.0.3,209.244.0.4 for Destination Addresses.
* Enter 53 for Destination port.
* Click on Add.

![Admin Role Check](./admin_role_check.png)

Next, we need to set up a NAT rule to allow remote desktop connectivity to the VM. 

* Navigate back to the firewall.
* Settings tab > Rules (classic).
* NAT rule collection.
* Add NAT rule collection.

![Admin Role Check](./admin_role_check.png)

* Enter a name for the rule collection.
* Enter a priority number.
* Enter a name for the rule.
* Select TCP for Protocol.
* Enter * for source.
* Enter the firewall’s public IP address for Destination address.
* Enter 3389 for Destination Port.
* Enter the VM’s private IP address for Translated address.
* Enter 3389 for Translated port.
* Click on Add.

![Admin Role Check](./admin_role_check.png)

Next, we need to update the primary and secondary DNS addresses for the VM. 

* Navigate to the VM.
* Network Settings.
* Click on the NIC link.

![Admin Role Check](./admin_role_check.png)

* Navigate to the DNS servers tab.
* Select the Custom radio button under DNS servers.
* Enter 209.244.0.3 and 209.244.0.4.
* Save.

![Admin Role Check](./admin_role_check.png)

Note: If the VM is still running, restart it.

# Testing

Now we need to test that the firewall works as expected. 

* On your local machine, hit Win Key + R.
* Type in mstsc, then hit enter.
* Enter the public IP address of the firewall.
* Enter the username associated with the VM created earlier.
* Click on Connect.

![Admin Role Check](./admin_role_check.png)

* Once connected to the VM, open Edge or another browser.
* Try to navigate to www.google.com.
* Try to navigate to another address and note that due to there being no rule match, the action is denied.

![Admin Role Check](./admin_role_check.png)

![Admin Role Check](./admin_role_check.png)

# Resources

