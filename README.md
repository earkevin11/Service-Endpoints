# Service-Endpoints

# What are Service-Endpoints?
- Service endpoints helps secure communication between virtual machines in a virtual network and resources in your subscription.
- 


# Implementing Service Endpoints
- Service endpoints have to be enabled from the azure virtual network and from the azure resource such as the key vault
- We could manual enter the public IP address of the virtual machine in the Azure Key Vault's firewall rule and set to allow access BUT
- A secure way would be enabling service endpoints
- Virtual Network > Service Endpoints > Add > Select a service > Select the subnet
- Now navigate to the virtual network > add existing virtual network > select subnet 
- This extends the service endpoint on to the azure keyvault service from the azure virtual network.
- After done, the azure vm would be able to access the key vault. 

# SERVICE ENDPOINTS ARE A MORE SECURE WAY.


# Implementation of Service Endpoints Demo
- 
