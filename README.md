# Service-Endpoints

# What are Service-Endpoints?
- Service endpoints helps secure communication between virtual machines in a virtual network AND the resources in your subscription.
- They also limit public access to some Azure services to a Vnet or a subnet.

# Important Note: 

- VM's connecting to the Azure Storage Account will be connecting to the Azure Storage Account's Public IP.
- The Azure Storage Account will see the connection from the virtual machine's Private IP address.
- When the Service Endpoint is enabled for the subnet, everything access will be blocked except for the virtual machine is that subnet where the service endpoint was created.
- Connection is going over Microsoft's backbone network and never over the internet. It is still connecting via the Storage account's public IP.

<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/196273560-2c8b7d05-ac91-41fd-a58d-7b0263f7285d.png" height="70%" width="70%" alt="service endpoints"/>

<p/>


# Example
- By default, Azure Storage accounts are accessible to the public to anyone with an internet connection. 
- To secure it, admins can enable service endpoint.

# How to enable service endpoint?
- Virtual Network > Subnet > Enable Service endpoint

# Must enable service endpoint on the service itself via "firewalls and virtal networks" blade

# Implementing Service Endpoints
- Service endpoints have to be enabled from the azure virtual network and from the azure resource such as the key vault
- We could manually enter the public IP address of the virtual machine in the Azure Key Vault's firewall rule and set to allow access BUT A secure way would be enabling service endpoints
- Virtual Network > Service Endpoints > Add > Select a service > Select the subnet
- Now navigate to the virtual network > add existing virtual network > select subnet 
- This extends the service endpoint on to the azure keyvault service from the azure virtual network.
- After done, the azure vm would be able to access the key vault. 

# SERVICE ENDPOINTS ARE A MORE SECURE WAY.
- It blocks public access but allow virtual machines to connect to the service using it's public IP.
- Only virtual machines that are in the same subnet as the storage account or Azure SQL server are allowed to connect.

 
# Implementation of Service Endpoints Demo
- 






# What are the differences between Service Endpoint and Private Endpoints?
- Service endpoint connectivity persepctive, the connection goes over the Microsoft backbone network, never goes over the internet, and connects to a service's public IP.
- With Private Endpoints, it is like the communication is occuring within the same virtual network or same subnet. The connection never leaves the subnet.



# Private Endpoints: 1:1 connection
- A 1:1 connection between a subnet of your virtual network AND one specific resource of a resource.
- Similar to Service Endpoint, but a NIC is assigned and added to the resource that connects to the VNet.
- The NIC has a private IP and acts like any other device.
- It blocks public access with the firewall
- NSG's are not applied to the Private Endpoint


# Important:
- The connection between a virtual machine and the azure resource will appear as if the connection is happening between two NIC and inside the subnet.
- The azure service will get an NIC card and private IP address.
- Connection never leaves the subnet where the private endpoint is created. It appears like the connection is from a resource on the same subnet because the Storage Account has an NIC just like the VM.


<p align="center">
  
<img src="https://user-images.githubusercontent.com/104326475/196273511-8456071f-5d70-4da3-8123-f2503250aa23.png" height="70%" width="70%" alt="private endpoints"/>

<p/>
