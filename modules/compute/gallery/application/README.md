# Compute Galleries Applications `[Microsoft.Compute/galleries/applications]`

This module deploys an Azure Compute Gallery Application.

## Navigation

- [Resource Types](#Resource-Types)
- [Parameters](#Parameters)
- [Outputs](#Outputs)
- [Cross-referenced modules](#Cross-referenced-modules)
- [Notes](#Notes)

## Resource Types

| Resource Type | API Version |
| :-- | :-- |
| `Microsoft.Authorization/roleAssignments` | [2022-04-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Authorization/2022-04-01/roleAssignments) |
| `Microsoft.Compute/galleries/applications` | [2022-03-03](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Compute/2022-03-03/galleries/applications) |

## Parameters

**Required parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`name`](#parameter-name) | string | Name of the application definition. |

**Conditional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`galleryName`](#parameter-galleryname) | string | The name of the parent Azure Compute Gallery. Required if the template is used in a standalone deployment. |

**Optional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`customActions`](#parameter-customactions) | array | A list of custom actions that can be performed with all of the Gallery Application Versions within this Gallery Application. |
| [`description`](#parameter-description) | string | The description of this gallery Application Definition resource. This property is updatable. |
| [`enableDefaultTelemetry`](#parameter-enabledefaulttelemetry) | bool | Enable telemetry via a Globally Unique Identifier (GUID). |
| [`endOfLifeDate`](#parameter-endoflifedate) | string | The end of life date of the gallery Image Definition. This property can be used for decommissioning purposes. This property is updatable. Allowed format: 2020-01-10T23:00:00.000Z. |
| [`eula`](#parameter-eula) | string | The Eula agreement for the gallery Application Definition. Has to be a valid URL. |
| [`location`](#parameter-location) | string | Location for all resources. |
| [`privacyStatementUri`](#parameter-privacystatementuri) | string | The privacy statement uri. Has to be a valid URL. |
| [`releaseNoteUri`](#parameter-releasenoteuri) | string | The release note uri. Has to be a valid URL. |
| [`roleAssignments`](#parameter-roleassignments) | array | Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'. |
| [`supportedOSType`](#parameter-supportedostype) | string | This property allows you to specify the supported type of the OS that application is built for. |
| [`tags`](#parameter-tags) | object | Tags for all resources. |

### Parameter: `customActions`

A list of custom actions that can be performed with all of the Gallery Application Versions within this Gallery Application.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `description`

The description of this gallery Application Definition resource. This property is updatable.
- Required: No
- Type: string
- Default: `''`

### Parameter: `enableDefaultTelemetry`

Enable telemetry via a Globally Unique Identifier (GUID).
- Required: No
- Type: bool
- Default: `True`

### Parameter: `endOfLifeDate`

The end of life date of the gallery Image Definition. This property can be used for decommissioning purposes. This property is updatable. Allowed format: 2020-01-10T23:00:00.000Z.
- Required: No
- Type: string
- Default: `''`

### Parameter: `eula`

The Eula agreement for the gallery Application Definition. Has to be a valid URL.
- Required: No
- Type: string
- Default: `''`

### Parameter: `galleryName`

The name of the parent Azure Compute Gallery. Required if the template is used in a standalone deployment.
- Required: Yes
- Type: string

### Parameter: `location`

Location for all resources.
- Required: No
- Type: string
- Default: `[resourceGroup().location]`

### Parameter: `name`

Name of the application definition.
- Required: Yes
- Type: string

### Parameter: `privacyStatementUri`

The privacy statement uri. Has to be a valid URL.
- Required: No
- Type: string
- Default: `''`

### Parameter: `releaseNoteUri`

The release note uri. Has to be a valid URL.
- Required: No
- Type: string
- Default: `''`

### Parameter: `roleAssignments`

Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `supportedOSType`

This property allows you to specify the supported type of the OS that application is built for.
- Required: No
- Type: string
- Default: `'Windows'`
- Allowed: `[Linux, Windows]`

### Parameter: `tags`

Tags for all resources.
- Required: No
- Type: object
- Default: `{object}`


## Outputs

| Output | Type | Description |
| :-- | :-- | :-- |
| `location` | string | The location the resource was deployed into. |
| `name` | string | The name of the image. |
| `resourceGroupName` | string | The resource group the image was deployed into. |
| `resourceId` | string | The resource ID of the image. |

## Cross-referenced modules

_None_

## Notes

### Parameter Usage: `customActions`

Create a list of custom actions that can be performed with all of the Gallery Application Versions within this Gallery Application.

<details>

<summary>Parameter JSON format</summary>

```json
"customActions": {
    "value": [
        {
            "description": "This is a sample custom action",
            "name": "Name of the custom action 1 (Required). Must be unique within the Compute Gallery",
            "parameters": [
                {
                    "defaultValue": "Default Value of Parameter1. Only applies to string types.",
                    "description": "a description value to help others understands what it means.",
                    "name": "The parameter name. (Required)",
                    "required": True,
                    "type": "ConfigurationDataBlob, LogOutputBlob, or String"
                },
                {
                    "defaultValue": "Default Value of Parameter2. Only applies to string types.",
                    "description": "a description value to help others understands what it means.",
                    "name": "The parameter name. (Required)",
                    "required": False,
                    "type": "ConfigurationDataBlob, LogOutputBlob, or String"
                }
            ],
            "script": "The script to run when executing this custom action. (Required)"
        },
        {
            "description": "This is another sample custom action",
            "name": "Name of the custom action 2 (Required). Must be unique within the Compute Gallery",
            "parameters": [
                {
                    "defaultValue": "Default Value of Parameter1. Only applies to string types.",
                    "description": "a description value to help others understands what it means.",
                    "name": "The parameter name. (Required)",
                    "required": True,
                    "type": "ConfigurationDataBlob, LogOutputBlob, or String"
                }
            ],
            "script": "The script to run when executing this custom action. (Required)"
        }
    ]
}
```

</details>

<details>

<summary>Bicep format</summary>

```bicep
customActions: [
    {
        description: "This is a sample custom action"
        name: "Name of the custom action 1 (Required). Must be unique within the Compute Gallery"
        parameters: [
            {
                defaultValue: "Default Value of Parameter 1. Only applies to string types."
                description: "a description value to help others understands what it means."
                name: "The parameter name. (Required)"
                required: True,
                type: "ConfigurationDataBlob, LogOutputBlob, or String"
            }
            {
                defaultValue: "Default Value of Parameter 2. Only applies to string types."
                description: "a description value to help others understands what it means."
                name: "The parameter name. (Required)"
                required: True,
                type: "ConfigurationDataBlob, LogOutputBlob, or String"
            }
        ]
        script: "The script to run when executing this custom action. (Required)"
    }
    {
        description: "This is another sample custom action"
        name: "Name of the custom action 2 (Required). Must be unique within the Compute Gallery"
        parameters: [
            {
                defaultValue: "Default Value of Parameter. Only applies to string types."
                description: "a description value to help others understands what it means."
                name: "The paramter name. (Required)"
                required: True,
                type: "ConfigurationDataBlob, LogOutputBlob, or String"
            }
        ]
        script: "The script to run when executing this custom action. (Required)"
    }
]
```

</details>
<p>
