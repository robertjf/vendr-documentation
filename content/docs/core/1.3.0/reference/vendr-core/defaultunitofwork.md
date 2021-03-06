---
title: DefaultUnitOfWork
description: API reference for DefaultUnitOfWork in Vendr, the eCommerce solution for Umbraco v8+
---
## DefaultUnitOfWork

A [`IDatabaseUnitOfWork`](../idatabaseunitofwork/) implementation using Umbraco Scopes

```csharp
public class DefaultUnitOfWork : IDatabaseUnitOfWork
```

**Inheritance**

* interface [IDatabaseUnitOfWork](../idatabaseunitofwork/)

**Namespace**
* [Vendr.Core](../)

### Properties

#### Database

A IDatabase reference for use in the Unit of Work

```csharp
public IDatabase Database { get; }
```


---

#### EntityStateCache

```csharp
public IEntityStateCache EntityStateCache { get; }
```


### Methods

#### Complete

Marks the completion of a successful Unit of Work

```csharp
public void Complete()
```


---

#### Dispose

Disposes of the Unit of Work

```csharp
public void Dispose()
```


---

#### ScheduleNotification

Schedules a Notification Event to be raised once the Unit of Work is complete

```csharp
public void ScheduleNotification(INotificationEvent notificationEvent)
```

**Parameters**

| Parameter | Description |
| --- | --- |
| notificationEvent | The Notification Event to raise |


---

#### ScheduleNotifications (1 of 2)

Schedules a series of Notification Events to be raised once the Unit of Work is complete

```csharp
public void ScheduleNotifications(params INotificationEvent[] notificationEvents)
```

**Parameters**

| Parameter | Description |
| --- | --- |
| notificationEvents | The list of Notification Events to raise |

---

#### ScheduleNotifications (2 of 2)

Schedules a series of Notification Events to be raised once the Unit of Work is complete

```csharp
public void ScheduleNotifications(IEnumerable<INotificationEvent> notificationEvents)
```

**Parameters**

| Parameter | Description |
| --- | --- |
| notificationEvents | The list of Notification Events to raise |


### Events

#### NotificationEventHandler

A utility Notification Event dispatch handler for registering Notification Events on the Umbraco Scope

```csharp
public static event EventHandler<NotificationEventArgs> NotificationEventHandler;
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->
