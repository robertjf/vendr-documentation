---
title: ValidateAllowedCountryBelongsToCurrencyStore
description: API reference for ValidateAllowedCountryBelongsToCurrencyStore in Vendr, the eCommerce solution for Umbraco v8+
---
## ValidateAllowedCountryBelongsToCurrencyStore

```csharp
public class ValidateAllowedCountryBelongsToCurrencyStore : 
    ValidationEventHandlerBase<ValidateCurrencyAllowInCountry>
```

**Inheritance**

* class [ValidationEventHandlerBase&lt;TValidationEvent&gt;](../validationeventhandlerbase-1/)

**Namespace**
* [Vendr.Core.Events.Validation.Handlers.Currency](../)

### Constructors

#### ValidateAllowedCountryBelongsToCurrencyStore

```csharp
public ValidateAllowedCountryBelongsToCurrencyStore(ICountryService countryService)
```


### Fields

#### _countryService

```csharp
public ICountryService _countryService;
```


### Methods

#### Validate

```csharp
public override void Validate(ValidateCurrencyAllowInCountry evt)
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->
