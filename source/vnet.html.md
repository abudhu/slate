---
title: VNET ARM Resource

language_tabs: # must be one of https://git.io/vQNgJ
  - json
  - powershell

toc_footers:

search: true
---

# VNET Resource

Specified a VNET Resource with a IPv4 CIDR block.  Fore more information on Azure Virtual Networks see [What is Azure Virtual Network](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)

# Declare Resource

```json
{
    "resources": [  
      {
            "name": "Vnet",
            "type": "Microsoft.Network/virtualNetworks",
            "apiVersion": "2020-04-01",
            "location": "West US 2",
            "properties": { 
                //PLEASE SEE Properties Section for Required Values
            }
        }
    ],
  }
```


Name | Type | Required | Description
--------- | ------- |  ------- | -----------
name | string | **yes** | Name of the VNET Resource
type | enum | **yes** | Microsoft.Network/virtualNetworks
apiVersion | enum | **yes** | The apiVersion that will be invoked for this resource.  Ex: 2020-04-01
location | string | **yes** | The Azure Region to deloy this resource. 
[properties](#Properties) | object | **yes** | Defining properties for the VNET Resource
[resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/child-resource-name-type) | array | no | Attach to an existing resource that this is dependent on.
tags | object | no | Resource Tags

# Properties

Name | Type | Required 
---- | ----- | ----  
[addressSpace](#addressSpace) | object | **yes** 
[dhcpOptions](#dhcpOptions) | object | no 
[subnets] (#subnet) | array | no 
[virtualNetworkPeerings](#virtualNetworkPeerings) | array | no 
[enableDdosProtection](#enableDdosProtection) | boolean | no 
[enableVmProtection](#enableVmProtection) | boolean | no
[ddosProtectionPlan](#ddosProtectionPlan) | object | no
[bgpCommunities](#bgpCommunities) | object | no
[ipAllocations](#ipAllocations) | array | no

## addressSpace

```json
"addressSpace": {
    "addressPrefixes": ["10.0.0.0/16"]
}
```

```powershell
$virtualNetwork = New-AzVirtualNetwork `
  -ResourceGroupName myResourceGroup `
  -Location WestUS2 `
  -Name Vnet `
  -AddressPrefix 10.0.0.0/16
```

The Address Space that contains an array of IP address that can be used by Subnets 

Name | Type | Required | Description
---- | ----- | ---- | ----
addressPrefixes | object | **yes** | A list of address blocks, in *string* format reserved for this virtual network in CIDR notation

## dhcpOptions

```json
"dhcpOptions": {
    "dnsServers": ["1.1.1.1", "2.2.2.2"]
}
```

Contains an array of DNS Servers available to Virtual Machines deployed in the virtual network 

Name | Type | Required | Description
---- | ----- | ---- | ----
dnsServers | array | **yes** | List of DNS Server IP addresses in *string* format

## enableDdosProtection

```json
"enableDdosProtection": "true",
```

Enable DDoS protection for all protected resources in a virtual network.  Requires [DDoS protection Plan](https://docs.microsoft.com/en-us/azure/virtual-network/ddos-protection-overview) associated with the resource. 

## enableVmProtection

```json
"enableVmProtection": "true"
```

Indicates if VM protection is enabled for all the subnets in the virtual network

## ddosProtectionPlan

```json
"ddosProtectionPlan": {
      "id": "00000-0000-0000-000"
    }
```

The DDoS protection plan associated with the virtual network.

Name | Type | Required | Description
---- | ----- | ---- | ----
id | string | **yes** | Resource ID

## bgpCommunities

```json
"bgpCommunities": {
      "virtualNetworkCommunity": "11111-1111-111-111"
    }
```

Bgp Communities sent over ExpressRoute with each route corresponding to a prefix in this VNET

Name | Type | Required | Description
---- | ----- | ---- | ----
virtualNetworkCommunity | string | **yes** | The BGP community associated with the virtual network.

## ipAllocations

```json
"ipAllocations": {
      "id": "00000-0000-0000-000"
    }
```

Array of IpAllocation which reference this VNET.

Name | Type | Required | Description
---- | ----- | ---- | ----
id | string | **yes** | Resource ID
