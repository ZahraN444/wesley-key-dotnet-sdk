
# User Notification Event Body

## Class Name

`UserNotificationEventBody`

## Cases

| Type | Factory Method |
|  --- | --- |
| [`UserActionNotificationEvent`](../../../doc/models/user-action-notification-event.md) | UserNotificationEventBody.FromUserActionNotificationEvent(UserActionNotificationEvent userActionNotificationEvent) |
| [`UserStatusNotificationEvent`](../../../doc/models/user-status-notification-event.md) | UserNotificationEventBody.FromUserStatusNotificationEvent(UserStatusNotificationEvent userStatusNotificationEvent) |
| [`UserPreferenceNotificationEvent`](../../../doc/models/user-preference-notification-event.md) | UserNotificationEventBody.FromUserPreferenceNotificationEvent(UserPreferenceNotificationEvent userPreferenceNotificationEvent) |

## UserActionNotificationEvent

### Initialization Code

#### Example

```csharp
UserNotificationEventBody value = UserNotificationEventBody.FromUserActionNotificationEvent(
    new UserActionNotificationEvent
    {
        UserActionNotificationEventType = "user.action",
    }
);
```

## UserStatusNotificationEvent

### Initialization Code

#### Example

```csharp
UserNotificationEventBody value = UserNotificationEventBody.FromUserStatusNotificationEvent(
    new UserStatusNotificationEvent
    {
        UserStatusNotificationEventType = "user.status",
    }
);
```

## UserPreferenceNotificationEvent

### Initialization Code

#### Example

```csharp
UserNotificationEventBody value = UserNotificationEventBody.FromUserPreferenceNotificationEvent(
    new UserPreferenceNotificationEvent
    {
        UserPreferenceNotificationEventType = "user.preference",
    }
);
```

