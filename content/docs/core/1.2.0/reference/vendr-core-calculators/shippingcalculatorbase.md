---
title: ShippingCalculatorBase
description: API reference for ShippingCalculatorBase in Vendr, the eCommerce solution for Umbraco v8+
---
## ShippingCalculatorBase

```csharp
public abstract class ShippingCalculatorBase : IShippingCalculator
```

**Inheritance**

* interface [IShippingCalculator](../ishippingcalculator/)

**Namespace**
* [Vendr.Core.Calculators](../)

### Methods

#### CalculateShippingMethodPrice

```csharp
public abstract Price CalculateShippingMethodPrice(ShippingMethodReadOnly shippingMethod, 
    Guid currencyId, Guid countryId, Guid? regionId, TaxRate taxRate)
```


---

#### CalculateShippingMethodTaxRate

```csharp
public abstract TaxRate CalculateShippingMethodTaxRate(ShippingMethodReadOnly shippingMethod, 
    TaxSource taxSource, TaxRate fallbackTaxRate)
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->