# Metric Alerts `[Microsoft.Insights/metricAlerts]`

This module deploys a Metric Alert.

## Navigation

- [Resource Types](#Resource-Types)
- [Usage examples](#Usage-examples)
- [Parameters](#Parameters)
- [Outputs](#Outputs)
- [Cross-referenced modules](#Cross-referenced-modules)

## Resource Types

| Resource Type | API Version |
| :-- | :-- |
| `Microsoft.Authorization/roleAssignments` | [2022-04-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Authorization/2022-04-01/roleAssignments) |
| `Microsoft.Insights/metricAlerts` | [2018-03-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Insights/2018-03-01/metricAlerts) |

## Usage examples

The following section provides usage examples for the module, which were used to validate and deploy the module successfully. For a full reference, please review the module's test folder in its repository.

>**Note**: Each example lists all the required parameters first, followed by the rest - each in alphabetical order.

>**Note**: To reference the module, please use the following syntax `br:bicep/modules/insights.metric-alert:1.0.0`.

- [Using large parameter set](#example-1-using-large-parameter-set)

### Example 1: _Using large parameter set_

This instance deploys the module with most of its features enabled.


<details>

<summary>via Bicep module</summary>

```bicep
module metricAlert 'br:bicep/modules/insights.metric-alert:1.0.0' = {
  name: '${uniqueString(deployment().name, location)}-test-imacom'
  params: {
    // Required parameters
    criterias: [
      {
        criterionType: 'StaticThresholdCriterion'
        metricName: 'Percentage CPU'
        metricNamespace: 'microsoft.compute/virtualmachines'
        name: 'HighCPU'
        operator: 'GreaterThan'
        threshold: '90'
        timeAggregation: 'Average'
      }
    ]
    name: 'imacom001'
    // Non-required parameters
    actions: [
      '<actionGroupResourceId>'
    ]
    alertCriteriaType: 'Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria'
    enableDefaultTelemetry: '<enableDefaultTelemetry>'
    roleAssignments: [
      {
        principalIds: [
          '<managedIdentityPrincipalId>'
        ]
        principalType: 'ServicePrincipal'
        roleDefinitionIdOrName: 'Reader'
      }
    ]
    tags: {
      Environment: 'Non-Prod'
      'hidden-title': 'This is visible in the resource name'
      Role: 'DeploymentValidation'
    }
    targetResourceRegion: 'westeurope'
    targetResourceType: 'microsoft.compute/virtualmachines'
    windowSize: 'PT15M'
  }
}
```

</details>
<p>

<details>

<summary>via JSON Parameter file</summary>

```json
{
  "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentParameters.json#",
  "contentVersion": "1.0.0.0",
  "parameters": {
    // Required parameters
    "criterias": {
      "value": [
        {
          "criterionType": "StaticThresholdCriterion",
          "metricName": "Percentage CPU",
          "metricNamespace": "microsoft.compute/virtualmachines",
          "name": "HighCPU",
          "operator": "GreaterThan",
          "threshold": "90",
          "timeAggregation": "Average"
        }
      ]
    },
    "name": {
      "value": "imacom001"
    },
    // Non-required parameters
    "actions": {
      "value": [
        "<actionGroupResourceId>"
      ]
    },
    "alertCriteriaType": {
      "value": "Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria"
    },
    "enableDefaultTelemetry": {
      "value": "<enableDefaultTelemetry>"
    },
    "roleAssignments": {
      "value": [
        {
          "principalIds": [
            "<managedIdentityPrincipalId>"
          ],
          "principalType": "ServicePrincipal",
          "roleDefinitionIdOrName": "Reader"
        }
      ]
    },
    "tags": {
      "value": {
        "Environment": "Non-Prod",
        "hidden-title": "This is visible in the resource name",
        "Role": "DeploymentValidation"
      }
    },
    "targetResourceRegion": {
      "value": "westeurope"
    },
    "targetResourceType": {
      "value": "microsoft.compute/virtualmachines"
    },
    "windowSize": {
      "value": "PT15M"
    }
  }
}
```

</details>
<p>


## Parameters

**Required parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`criterias`](#parameter-criterias) | array | Criterias to trigger the alert. Array of 'Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria' or 'Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria' objects. When using MultipleResourceMultipleMetricCriteria criteria type, some parameters becomes mandatory. It is not possible to convert from SingleResourceMultipleMetricCriteria to MultipleResourceMultipleMetricCriteria. The alert must be deleted and recreated. |
| [`name`](#parameter-name) | string | The name of the alert. |

**Conditional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`targetResourceRegion`](#parameter-targetresourceregion) | string | The region of the target resource(s) on which the alert is created/updated. Required if alertCriteriaType is MultipleResourceMultipleMetricCriteria. |
| [`targetResourceType`](#parameter-targetresourcetype) | string | The resource type of the target resource(s) on which the alert is created/updated. Required if alertCriteriaType is MultipleResourceMultipleMetricCriteria. |

**Optional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`actions`](#parameter-actions) | array | The list of actions to take when alert triggers. |
| [`alertCriteriaType`](#parameter-alertcriteriatype) | string | Maps to the 'odata.type' field. Specifies the type of the alert criteria. |
| [`alertDescription`](#parameter-alertdescription) | string | Description of the alert. |
| [`autoMitigate`](#parameter-automitigate) | bool | The flag that indicates whether the alert should be auto resolved or not. |
| [`enabled`](#parameter-enabled) | bool | Indicates whether this alert is enabled. |
| [`enableDefaultTelemetry`](#parameter-enabledefaulttelemetry) | bool | Enable telemetry via a Globally Unique Identifier (GUID). |
| [`evaluationFrequency`](#parameter-evaluationfrequency) | string | how often the metric alert is evaluated represented in ISO 8601 duration format. |
| [`location`](#parameter-location) | string | Location for all resources. |
| [`roleAssignments`](#parameter-roleassignments) | array | Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'. |
| [`scopes`](#parameter-scopes) | array | the list of resource IDs that this metric alert is scoped to. |
| [`severity`](#parameter-severity) | int | The severity of the alert. |
| [`tags`](#parameter-tags) | object | Tags of the resource. |
| [`windowSize`](#parameter-windowsize) | string | the period of time (in ISO 8601 duration format) that is used to monitor alert activity based on the threshold. |

### Parameter: `actions`

The list of actions to take when alert triggers.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `alertCriteriaType`

Maps to the 'odata.type' field. Specifies the type of the alert criteria.
- Required: No
- Type: string
- Default: `'Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria'`
- Allowed: `[Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria, Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria, Microsoft.Azure.Monitor.WebtestLocationAvailabilityCriteria]`

### Parameter: `alertDescription`

Description of the alert.
- Required: No
- Type: string
- Default: `''`

### Parameter: `autoMitigate`

The flag that indicates whether the alert should be auto resolved or not.
- Required: No
- Type: bool
- Default: `True`

### Parameter: `criterias`

Criterias to trigger the alert. Array of 'Microsoft.Azure.Monitor.SingleResourceMultipleMetricCriteria' or 'Microsoft.Azure.Monitor.MultipleResourceMultipleMetricCriteria' objects. When using MultipleResourceMultipleMetricCriteria criteria type, some parameters becomes mandatory. It is not possible to convert from SingleResourceMultipleMetricCriteria to MultipleResourceMultipleMetricCriteria. The alert must be deleted and recreated.
- Required: Yes
- Type: array

### Parameter: `enabled`

Indicates whether this alert is enabled.
- Required: No
- Type: bool
- Default: `True`

### Parameter: `enableDefaultTelemetry`

Enable telemetry via a Globally Unique Identifier (GUID).
- Required: No
- Type: bool
- Default: `True`

### Parameter: `evaluationFrequency`

how often the metric alert is evaluated represented in ISO 8601 duration format.
- Required: No
- Type: string
- Default: `'PT5M'`
- Allowed: `[PT15M, PT1H, PT1M, PT30M, PT5M]`

### Parameter: `location`

Location for all resources.
- Required: No
- Type: string
- Default: `'global'`

### Parameter: `name`

The name of the alert.
- Required: Yes
- Type: string

### Parameter: `roleAssignments`

Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `scopes`

the list of resource IDs that this metric alert is scoped to.
- Required: No
- Type: array
- Default: `[[subscription().id]]`

### Parameter: `severity`

The severity of the alert.
- Required: No
- Type: int
- Default: `3`
- Allowed: `[0, 1, 2, 3, 4]`

### Parameter: `tags`

Tags of the resource.
- Required: No
- Type: object
- Default: `{object}`

### Parameter: `targetResourceRegion`

The region of the target resource(s) on which the alert is created/updated. Required if alertCriteriaType is MultipleResourceMultipleMetricCriteria.
- Required: No
- Type: string
- Default: `''`

### Parameter: `targetResourceType`

The resource type of the target resource(s) on which the alert is created/updated. Required if alertCriteriaType is MultipleResourceMultipleMetricCriteria.
- Required: No
- Type: string
- Default: `''`

### Parameter: `windowSize`

the period of time (in ISO 8601 duration format) that is used to monitor alert activity based on the threshold.
- Required: No
- Type: string
- Default: `'PT15M'`
- Allowed: `[P1D, PT12H, PT15M, PT1H, PT1M, PT30M, PT5M, PT6H]`


## Outputs

| Output | Type | Description |
| :-- | :-- | :-- |
| `location` | string | The location the resource was deployed into. |
| `name` | string | The name of the metric alert. |
| `resourceGroupName` | string | The resource group the metric alert was deployed into. |
| `resourceId` | string | The resource ID of the metric alert. |

## Cross-referenced modules

_None_
