---
title: CalculateOrderLineUnitPriceDiscountTask
description: API reference for CalculateOrderLineUnitPriceDiscountTask in Vendr, the eCommerce solution for Umbraco v8+
---
## CalculateOrderLineUnitPriceDiscountTask

```csharp
public class CalculateOrderLineUnitPriceDiscountTask : 
    PipelineTaskWithTypedArgsBase<OrderLineCalculationPipelineArgs, OrderLineCalculation>
```

**Inheritance**

* class [PipelineTaskWithTypedArgsBase&lt;TArgs,T&gt;](../pipelinetaskwithtypedargsbase-2/)

**Namespace**
* [Vendr.Core.Pipelines.OrderLine.Tasks](../)

### Constructors

#### CalculateOrderLineUnitPriceDiscountTask

The default constructor.

```csharp
public CalculateOrderLineUnitPriceDiscountTask()
```


### Methods

#### Execute

```csharp
public override PipelineResult<OrderLineCalculation> Execute(OrderLineCalculationPipelineArgs args)
```


<!-- DO NOT EDIT: generated by xmldocmd for Vendr.Core.dll -->
