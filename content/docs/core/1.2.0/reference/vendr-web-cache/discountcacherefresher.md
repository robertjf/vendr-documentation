---
title: DiscountCacheRefresher
description: API reference for DiscountCacheRefresher in Vendr, the eCommerce solution for Umbraco v8+
---
## DiscountCacheRefresher

```csharp
public class DiscountCacheRefresher : 
    VendrEntityStateCacheRefresherBase<DiscountCacheRefresher, IDiscountService, DiscountReadOnly>
```

**Inheritance**

* class [VendrEntityStateCacheRefresherBase&lt;TInstanceType,TService,TEntity&gt;](../vendrentitystatecacherefresherbase-3/)

**Namespace**
* [Vendr.Web.Cache](../)

### Constructors

#### DiscountCacheRefresher

```csharp
public DiscountCacheRefresher(AppCaches appCaches, IEntityStateCache stateCache, 
    IDiscountService entityService)
```


### Properties

#### CacheKey

```csharp
public override string CacheKey { get; }
```


---

#### Name

```csharp
public override string Name { get; }
```


---

#### RefresherUniqueId

```csharp
public override Guid RefresherUniqueId { get; }
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Web.dll -->
