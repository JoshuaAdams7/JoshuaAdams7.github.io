---
layout: default
---

# Azure Firewall Manager

In this scenario, we want to be able to prevent access to web addresses not on the approved list.

# Technologies

* Virtual Networks.
* Virtual Network Peering.
* Virtual Machines.
* Azure Firewall Manager.
* Firewall Policies (DNAT, Application, Network).
* Route Tables.

# Resource group creation

First, we need to create two spoke virtual networks and subnets.

* Go to portal.azure.com.
* Search for virtual Networks.
* Click on Create.

![Resource Group](./resource_group.png)

* Select an appropriate subscription.
* Click on the Create new resource group link.
* Enter a name for the new resource group.
* Click on OK.
* Enter a name for the virtual network.
* Select an appropriate region.
* Click on the IP Addresses tab.

![Resource Group](./resource_group.png)

* Click on the default text link under Subnets.
* Enter a name for the subnet.
* Modify the starting IP address.
* Click on Save.

![Resource Group](./resource_group.png)

* Click on Review + create.
* Click on Create.

Now we need to create another virtual network.

As above, select an appropriate subscription, select the same resource group, enter an appropriate name for this other virtual network instance, and select the same region as above.

![Resource Group](./resource_group.png)

In the IP Addresses tab, update the IP address range.

![Resource Group](./resource_group.png)

* As above, click on the default text link under Subnets.
* Enter a name for the subnet.
* Modify the starting IP address.
* Click on Save.

![Resource Group](./resource_group.png)

* Click on Review + create.
* Click on Create.

# Creating a Secured Virtual Hub

Next, we need to create a secured virtual hub.
* Go to portal.azure.com.
* Search for Azure Firewalls.
* Under Secure your resources, click on Virtual Hubs.
* Click on Create new secured virtual hub.

![Resource Group](./resource_group.png)

* Select your subscription.
* Select the resource group created earlier.
* Select the same region as used above.
* Enter a name for the virtual hub.
* Enter an appropriate IP address range.
* Select Standard for the type.
* Leave the Include VPN gateway to enable Security Partner Providers unchecked.

![Resource Group](./resource_group.png)

* Click on the Azure Firewall tab.
* Leave the default Azure Firewall setting on Enabled.
* Select the Standard Azure Firewall tier.
* In this case I’ve removed the Availability Zones that were selected.
* Check the box next to the Default Deny Policy.

![Resource Group](./resource_group.png)

* Click on the Review + create tab.
* Click on Create.

Note: It can take up to 30 minutes to create a secured virtual hub.

* Navigate back to Firewall Manager.
* Click on the Virtual Hubs menu item.
* Select the hub created earlier.


# Resources

* [Microsoft Azure Security Engineer Associate (AZ-500) Professional Certificate](https://www.coursera.org/professional-certificates/microsoft-azure-security-engineer-associate)

