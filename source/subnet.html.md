---
title: Subnet ARM Resource

language_tabs: # must be one of https://git.io/vQNgJ
  - json
  - powershell

toc_footers:

search: true
---

# Subnet Resource

Specifies a Subnet to an existing Virtual Network.

# Declare Resource

```json
"resources": [  
      {
          "name": "myVirtualNetwork/frontend_subnet",
          "type": "Microsoft.Network/virtualNetworks/subnets",
          "dependsOn": ["myVirtualNetwork"],
          "apiVersion": "2020-04-01",
          "properties": {
              //PLEASE SEE Properties Section for Required Values
          }

      }
  ]
```


Name | Type | Required | Description
--------- | ------- |  ------- | -----------
name | string | **yes** | Name of the Subnet given in {VNet Resource Name}/{Resource Name}
type | enum | **yes** | Microsoft.Network/virtualNetworks/subnets 
dependsOn | array | **yes** |  Name of the resources this Subnet is dependent on. VNet Resource name is Required
apiVersion | enum | **yes** | The apiVersion that will be invoked for this resource.  Ex: 2020-04-01
[properties](#properties) | object | **yes** | Defining properties for the VNET Resource


# Properties

Name | Type | Required 
---- | ----- | ----  
[addressPrefix](#addressPrefix) | string | **yes** 
[addressPrefixes](#addressPrefixes) | array | no
[networkSecurityGroup](#networkSecurityGroup) | object | no
[routeTable](#routeTable) | object | no
[natGateway](#natGateway) | object | no
[serviceEndpoints](#serviceEndpoints) | array | no
[serviceEndpointPolicies](#serviceEndpointPolicies) | array | no
[ipAllocations](#ipAllocations) | array | no
[delegations](#delegations) | array | no
[privateEndpointNetworkPolicies](#privateEndpointNetworkPolicies) | string | no
[privateLinkServiceNetworkPolicies](#privateLinkServiceNetworkPolicies) | string | no

## addressPrefix

```json
"addressPrefix": "10.0.1.0/24"
```

The subnet address to be created within the Vnet CIDR block

## addressPrefixes
```json
"addressPrefixes": ["10.0.1.0/24","10.0.2.0/24"]
```

A list of subnet address to be created within gthe Vnet CIDR block


# Issues

## addressPrefixes 
{"code":"DeploymentFailed","message":"At least one resource deployment operation failed. Please list deployment operations for details. Please see https://aka.ms/DeployOperations for usage details.","details":[{"code":"BadRequest","message":"{\r\n \"error\": {\r\n \"code\": \"SubscriptionNotRegisteredForFeature\",\r\n \"message\": \"Subscription 66d5997f-8792-477b-9e2a-a69d08275ddd is not registered for feature Microsoft.Network/AllowMultipleAddressPrefixesOnSubnet required to carry out the requested operation.\",\r\n \"details\": []\r\n }\r\n}"}]}