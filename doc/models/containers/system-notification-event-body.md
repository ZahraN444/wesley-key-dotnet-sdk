
# System Notification Event Body

## Class Name

`SystemNotificationEventBody`

## Cases

| Type | Factory Method |
|  --- | --- |
| [`SystemAlertNotificationEvent`](../../../doc/models/system-alert-notification-event.md) | SystemNotificationEventBody.FromSystemAlertNotificationEvent(SystemAlertNotificationEvent systemAlertNotificationEvent) |
| [`SystemMaintenanceNotificationEvent`](../../../doc/models/system-maintenance-notification-event.md) | SystemNotificationEventBody.FromSystemMaintenanceNotificationEvent(SystemMaintenanceNotificationEvent systemMaintenanceNotificationEvent) |
| [`SystemPerformanceNotificationEvent`](../../../doc/models/system-performance-notification-event.md) | SystemNotificationEventBody.FromSystemPerformanceNotificationEvent(SystemPerformanceNotificationEvent systemPerformanceNotificationEvent) |

## SystemAlertNotificationEvent

### Initialization Code

#### Example

```csharp
SystemNotificationEventBody value = SystemNotificationEventBody.FromSystemAlertNotificationEvent(
    new SystemAlertNotificationEvent
    {
        SystemAlertNotificationEventType = "system.alert",
    }
);
```

## SystemMaintenanceNotificationEvent

### Initialization Code

#### Example

```csharp
SystemNotificationEventBody value = SystemNotificationEventBody.FromSystemMaintenanceNotificationEvent(
    new SystemMaintenanceNotificationEvent
    {
        SystemMaintenanceNotificationEventType = "system.maintenance",
    }
);
```

## SystemPerformanceNotificationEvent

### Initialization Code

#### Example

```csharp
SystemNotificationEventBody value = SystemNotificationEventBody.FromSystemPerformanceNotificationEvent(
    new SystemPerformanceNotificationEvent
    {
        SystemPerformanceNotificationEventType = "system.performance",
    }
);
```

