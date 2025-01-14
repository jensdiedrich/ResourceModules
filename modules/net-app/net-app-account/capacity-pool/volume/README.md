# Azure NetApp Files Capacity Pool Volumes `[Microsoft.NetApp/netAppAccounts/capacityPools/volumes]`

This module deploys an Azure NetApp Files Capacity Pool Volume.

## Navigation

- [Resource Types](#Resource-Types)
- [Parameters](#Parameters)
- [Outputs](#Outputs)
- [Cross-referenced modules](#Cross-referenced-modules)

## Resource Types

| Resource Type | API Version |
| :-- | :-- |
| `Microsoft.Authorization/roleAssignments` | [2022-04-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Authorization/2022-04-01/roleAssignments) |
| `Microsoft.NetApp/netAppAccounts/capacityPools/volumes` | [2022-11-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.NetApp/netAppAccounts/capacityPools/volumes) |

## Parameters

**Required parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`name`](#parameter-name) | string | The name of the pool volume. |
| [`subnetResourceId`](#parameter-subnetresourceid) | string | The Azure Resource URI for a delegated subnet. Must have the delegation Microsoft.NetApp/volumes. |
| [`usageThreshold`](#parameter-usagethreshold) | int | Maximum storage quota allowed for a file system in bytes. |

**Conditional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`capacityPoolName`](#parameter-capacitypoolname) | string | The name of the parent capacity pool. Required if the template is used in a standalone deployment. |
| [`netAppAccountName`](#parameter-netappaccountname) | string | The name of the parent NetApp account. Required if the template is used in a standalone deployment. |

**Optional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`creationToken`](#parameter-creationtoken) | string | A unique file path for the volume. This is the name of the volume export. A volume is mounted using the export path. File path must start with an alphabetical character and be unique within the subscription. |
| [`enableDefaultTelemetry`](#parameter-enabledefaulttelemetry) | bool | Enable telemetry via a Globally Unique Identifier (GUID). |
| [`exportPolicyRules`](#parameter-exportpolicyrules) | array | Export policy rules. |
| [`location`](#parameter-location) | string | Location of the pool volume. |
| [`protocolTypes`](#parameter-protocoltypes) | array | Set of protocol types. |
| [`roleAssignments`](#parameter-roleassignments) | array | Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'. |
| [`serviceLevel`](#parameter-servicelevel) | string | The pool service level. Must match the one of the parent capacity pool. |

### Parameter: `capacityPoolName`

The name of the parent capacity pool. Required if the template is used in a standalone deployment.
- Required: Yes
- Type: string

### Parameter: `creationToken`

A unique file path for the volume. This is the name of the volume export. A volume is mounted using the export path. File path must start with an alphabetical character and be unique within the subscription.
- Required: No
- Type: string
- Default: `[parameters('name')]`

### Parameter: `enableDefaultTelemetry`

Enable telemetry via a Globally Unique Identifier (GUID).
- Required: No
- Type: bool
- Default: `True`

### Parameter: `exportPolicyRules`

Export policy rules.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `location`

Location of the pool volume.
- Required: No
- Type: string
- Default: `[resourceGroup().location]`

### Parameter: `name`

The name of the pool volume.
- Required: Yes
- Type: string

### Parameter: `netAppAccountName`

The name of the parent NetApp account. Required if the template is used in a standalone deployment.
- Required: Yes
- Type: string

### Parameter: `protocolTypes`

Set of protocol types.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `roleAssignments`

Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `serviceLevel`

The pool service level. Must match the one of the parent capacity pool.
- Required: No
- Type: string
- Default: `'Standard'`
- Allowed: `[Premium, Standard, StandardZRS, Ultra]`

### Parameter: `subnetResourceId`

The Azure Resource URI for a delegated subnet. Must have the delegation Microsoft.NetApp/volumes.
- Required: Yes
- Type: string

### Parameter: `usageThreshold`

Maximum storage quota allowed for a file system in bytes.
- Required: Yes
- Type: int


## Outputs

| Output | Type | Description |
| :-- | :-- | :-- |
| `location` | string | The location the resource was deployed into. |
| `name` | string | The name of the Volume. |
| `resourceGroupName` | string | The name of the Resource Group the Volume was created in. |
| `resourceId` | string | The Resource ID of the Volume. |

## Cross-referenced modules

_None_
