# Service Bus Namespace Queue `[Microsoft.ServiceBus/namespaces/queues]`

This module deploys a Service Bus Namespace Queue.

## Navigation

- [Resource Types](#Resource-Types)
- [Parameters](#Parameters)
- [Outputs](#Outputs)
- [Cross-referenced modules](#Cross-referenced-modules)

## Resource Types

| Resource Type | API Version |
| :-- | :-- |
| `Microsoft.Authorization/locks` | [2020-05-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Authorization/2020-05-01/locks) |
| `Microsoft.Authorization/roleAssignments` | [2022-04-01](https://learn.microsoft.com/en-us/azure/templates/Microsoft.Authorization/2022-04-01/roleAssignments) |
| `Microsoft.ServiceBus/namespaces/queues` | [2022-10-01-preview](https://learn.microsoft.com/en-us/azure/templates/Microsoft.ServiceBus/2022-10-01-preview/namespaces/queues) |
| `Microsoft.ServiceBus/namespaces/queues/authorizationRules` | [2022-10-01-preview](https://learn.microsoft.com/en-us/azure/templates/Microsoft.ServiceBus/2022-10-01-preview/namespaces/queues/authorizationRules) |

## Parameters

**Required parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`name`](#parameter-name) | string | Name of the Service Bus Queue. |

**Conditional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`namespaceName`](#parameter-namespacename) | string | The name of the parent Service Bus Namespace for the Service Bus Queue. Required if the template is used in a standalone deployment. |

**Optional parameters**

| Parameter | Type | Description |
| :-- | :-- | :-- |
| [`authorizationRules`](#parameter-authorizationrules) | array | Authorization Rules for the Service Bus Queue. |
| [`autoDeleteOnIdle`](#parameter-autodeleteonidle) | string | ISO 8061 timeSpan idle interval after which the queue is automatically deleted. The minimum duration is 5 minutes (PT5M). |
| [`deadLetteringOnMessageExpiration`](#parameter-deadletteringonmessageexpiration) | bool | A value that indicates whether this queue has dead letter support when a message expires. |
| [`defaultMessageTimeToLive`](#parameter-defaultmessagetimetolive) | string | ISO 8601 default message timespan to live value. This is the duration after which the message expires, starting from when the message is sent to Service Bus. This is the default value used when TimeToLive is not set on a message itself. |
| [`duplicateDetectionHistoryTimeWindow`](#parameter-duplicatedetectionhistorytimewindow) | string | ISO 8601 timeSpan structure that defines the duration of the duplicate detection history. The default value is 10 minutes. |
| [`enableBatchedOperations`](#parameter-enablebatchedoperations) | bool | Value that indicates whether server-side batched operations are enabled. |
| [`enableDefaultTelemetry`](#parameter-enabledefaulttelemetry) | bool | Enable telemetry via a Globally Unique Identifier (GUID). |
| [`enableExpress`](#parameter-enableexpress) | bool | A value that indicates whether Express Entities are enabled. An express queue holds a message in memory temporarily before writing it to persistent storage. |
| [`enablePartitioning`](#parameter-enablepartitioning) | bool | A value that indicates whether the queue is to be partitioned across multiple message brokers. |
| [`forwardDeadLetteredMessagesTo`](#parameter-forwarddeadletteredmessagesto) | string | Queue/Topic name to forward the Dead Letter message. |
| [`forwardTo`](#parameter-forwardto) | string | Queue/Topic name to forward the messages. |
| [`lock`](#parameter-lock) | string | Specify the type of lock. |
| [`lockDuration`](#parameter-lockduration) | string | ISO 8601 timespan duration of a peek-lock; that is, the amount of time that the message is locked for other receivers. The maximum value for LockDuration is 5 minutes; the default value is 1 minute. |
| [`maxDeliveryCount`](#parameter-maxdeliverycount) | int | The maximum delivery count. A message is automatically deadlettered after this number of deliveries. default value is 10. |
| [`maxMessageSizeInKilobytes`](#parameter-maxmessagesizeinkilobytes) | int | Maximum size (in KB) of the message payload that can be accepted by the queue. This property is only used in Premium today and default is 1024. |
| [`maxSizeInMegabytes`](#parameter-maxsizeinmegabytes) | int | The maximum size of the queue in megabytes, which is the size of memory allocated for the queue. Default is 1024. |
| [`requiresDuplicateDetection`](#parameter-requiresduplicatedetection) | bool | A value indicating if this queue requires duplicate detection. |
| [`requiresSession`](#parameter-requiressession) | bool | A value that indicates whether the queue supports the concept of sessions. |
| [`roleAssignments`](#parameter-roleassignments) | array | Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'. |
| [`status`](#parameter-status) | string | Enumerates the possible values for the status of a messaging entity. - Active, Disabled, Restoring, SendDisabled, ReceiveDisabled, Creating, Deleting, Renaming, Unknown. |

### Parameter: `authorizationRules`

Authorization Rules for the Service Bus Queue.
- Required: No
- Type: array
- Default: `[System.Management.Automation.OrderedHashtable]`

### Parameter: `autoDeleteOnIdle`

ISO 8061 timeSpan idle interval after which the queue is automatically deleted. The minimum duration is 5 minutes (PT5M).
- Required: No
- Type: string
- Default: `''`

### Parameter: `deadLetteringOnMessageExpiration`

A value that indicates whether this queue has dead letter support when a message expires.
- Required: No
- Type: bool
- Default: `True`

### Parameter: `defaultMessageTimeToLive`

ISO 8601 default message timespan to live value. This is the duration after which the message expires, starting from when the message is sent to Service Bus. This is the default value used when TimeToLive is not set on a message itself.
- Required: No
- Type: string
- Default: `'P14D'`

### Parameter: `duplicateDetectionHistoryTimeWindow`

ISO 8601 timeSpan structure that defines the duration of the duplicate detection history. The default value is 10 minutes.
- Required: No
- Type: string
- Default: `'PT10M'`

### Parameter: `enableBatchedOperations`

Value that indicates whether server-side batched operations are enabled.
- Required: No
- Type: bool
- Default: `True`

### Parameter: `enableDefaultTelemetry`

Enable telemetry via a Globally Unique Identifier (GUID).
- Required: No
- Type: bool
- Default: `True`

### Parameter: `enableExpress`

A value that indicates whether Express Entities are enabled. An express queue holds a message in memory temporarily before writing it to persistent storage.
- Required: No
- Type: bool
- Default: `False`

### Parameter: `enablePartitioning`

A value that indicates whether the queue is to be partitioned across multiple message brokers.
- Required: No
- Type: bool
- Default: `False`

### Parameter: `forwardDeadLetteredMessagesTo`

Queue/Topic name to forward the Dead Letter message.
- Required: No
- Type: string
- Default: `''`

### Parameter: `forwardTo`

Queue/Topic name to forward the messages.
- Required: No
- Type: string
- Default: `''`

### Parameter: `lock`

Specify the type of lock.
- Required: No
- Type: string
- Default: `''`
- Allowed: `['', CanNotDelete, ReadOnly]`

### Parameter: `lockDuration`

ISO 8601 timespan duration of a peek-lock; that is, the amount of time that the message is locked for other receivers. The maximum value for LockDuration is 5 minutes; the default value is 1 minute.
- Required: No
- Type: string
- Default: `'PT1M'`

### Parameter: `maxDeliveryCount`

The maximum delivery count. A message is automatically deadlettered after this number of deliveries. default value is 10.
- Required: No
- Type: int
- Default: `10`

### Parameter: `maxMessageSizeInKilobytes`

Maximum size (in KB) of the message payload that can be accepted by the queue. This property is only used in Premium today and default is 1024.
- Required: No
- Type: int
- Default: `1024`

### Parameter: `maxSizeInMegabytes`

The maximum size of the queue in megabytes, which is the size of memory allocated for the queue. Default is 1024.
- Required: No
- Type: int
- Default: `1024`

### Parameter: `name`

Name of the Service Bus Queue.
- Required: Yes
- Type: string

### Parameter: `namespaceName`

The name of the parent Service Bus Namespace for the Service Bus Queue. Required if the template is used in a standalone deployment.
- Required: Yes
- Type: string

### Parameter: `requiresDuplicateDetection`

A value indicating if this queue requires duplicate detection.
- Required: No
- Type: bool
- Default: `False`

### Parameter: `requiresSession`

A value that indicates whether the queue supports the concept of sessions.
- Required: No
- Type: bool
- Default: `False`

### Parameter: `roleAssignments`

Array of role assignment objects that contain the 'roleDefinitionIdOrName' and 'principalId' to define RBAC role assignments on this resource. In the roleDefinitionIdOrName attribute, you can provide either the display name of the role definition, or its fully qualified ID in the following format: '/providers/Microsoft.Authorization/roleDefinitions/c2f4ef07-c644-48eb-af81-4b1b4947fb11'.
- Required: No
- Type: array
- Default: `[]`

### Parameter: `status`

Enumerates the possible values for the status of a messaging entity. - Active, Disabled, Restoring, SendDisabled, ReceiveDisabled, Creating, Deleting, Renaming, Unknown.
- Required: No
- Type: string
- Default: `'Active'`
- Allowed: `[Active, Creating, Deleting, Disabled, ReceiveDisabled, Renaming, Restoring, SendDisabled, Unknown]`


## Outputs

| Output | Type | Description |
| :-- | :-- | :-- |
| `name` | string | The name of the deployed queue. |
| `resourceGroupName` | string | The resource group of the deployed queue. |
| `resourceId` | string | The resource ID of the deployed queue. |

## Cross-referenced modules

_None_
