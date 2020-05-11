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

<aside class="notice">
Cannot be used when <em><a href="http://51.143.17.183:4567/subnet.html#addressprefixes">addressPrefixes</a></em> is used
</aside>

## addressPrefixes

```json
"addressPrefixes": ["10.0.1.0/24","10.0.2.0/24"]
```

A list of subnet address to be created within gthe Vnet CIDR block

<aside class="notice">
Cannot be used when <a href="http://51.143.17.183:4567/subnet.html#addressprefix"><em>addressPrefix</em></a> is used
</aside>

### Issues

Issue | Description
--- | ----
SubscriptionNotRegisteredForFeature | Your subscription may not be registered for the following feature: Microsoft.Network/AllowMultipleAddressPrefixesOnSubnet 