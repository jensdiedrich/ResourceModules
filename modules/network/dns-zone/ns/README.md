# Public DNS Zone NS record `[Microsoft.Network/dnsZones/NS]`

This module deploys a Public DNS Zone NS record.

## Navigation

- [Resource Types](#Resource-Types)
- [Parameters](#Parameters)
- [Outputs](#Outputs)
- [Cross-referenced modules](#Cross-referenced-modules)

## Resource Types

| Resource Type | API Version |
| :-- | :-- |
| `Microsoft.Authorization/roleAssignments` | [2022-04-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Authorization/2022-04-01/roleAssignments) |
| `Microsoft.Network/dnsZones/NS` | [2018-05-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Network/2018-05-01/dnsZones/NS) |

## Parameters

**Required parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`name`](#parameter-name) | string | The name of the NS record. |

**Conditional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`dnsZoneName`](#parameter-dnszonename) | string | The name of the parent DNS zone. Required if the template is used in a standalone deployment. |

**Optional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`enableDefaultTelemetry`](#parameter-enabledefaulttelemetry) | bool | Enable telemetry via a Globally Unique Identifier (GUID). |
| [`metadata`](#parameter-metadata) | object | The metadata attached to the record set. |
| [`nsRecords`](#parameter-nsrecords) | array | The list of NS records in the record set. |
| [`roleAssignments`](#parameter-roleassignments) | array | Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'. |
| [`ttl`](#parameter-ttl) | int | The TTL (time-to-live) of the records in the record set. |

### Parameter: `dnsZoneName`

The name of the parent DNS zone. Required if the template is used in a standalone deployment.
- Required: Yes
- Type: string

### Parameter: `enableDefaultTelemetry`

Enable telemetry via a Globally Unique Identifier (GUID).
- Required: No
- Type: bool
- Default: `True`

### Parameter: `metadata`

The metadata attached to the record set.
- Required: No
- Type: object
- Default: `{object}`

### Parameter: `name`

The name of the NS record.
- Required: Yes
- Type: string

### Parameter: `nsRecords`

The list of NS records in the record set.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `roleAssignments`

Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `ttl`

The TTL (time-to-live) of the records in the record set.
- Required: No
- Type: int
- Default: `3600`


## Outputs

| Output | Type | Description |
| :-- | :-- | :-- |
| `name` | string | The name of the deployed NS record. |
| `resourceGroupName` | string | The resource group of the deployed NS record. |
| `resourceId` | string | The resource ID of the deployed NS record. |

## Cross-referenced modules

_None_
