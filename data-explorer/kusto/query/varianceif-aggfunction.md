---
title: varianceif() (aggregation function) - Azure Data Explorer
description: Learn how to use the varianceif() aggregation function to calculate the variance in an expression if the a condition is TRUE in Azure Data Explorer.
ms.reviewer: alexans
ms.topic: reference
ms.date: 09/21/2022
---
# varianceif() (aggregation function)

Calculates the [variance](variance-aggfunction.md) of *Expr* across the group for which *Predicate* evaluates to `true`.

[!INCLUDE [data-explorer-agg-function-summarize-note](../../includes/data-explorer-agg-function-summarize-note.md)]

## Syntax

`varianceif` `(`*Expr*`,` *Predicate*`)`

## Arguments

| Name | Type | Required | Description |
|--|--|--|--|
|*Expr* | string | &check; | Expression that will be used for aggregation calculation.|
|*Predicate*| string | &check; | Predicate that if true, the *Expr* calculated value will be added to the variance.

## Returns

Returns the variance value of *Expr* across the group where *Predicate* evaluates to `true`.

## Example

**\[**[**Click to run query**](https://dataexplorer.azure.com/clusters/help/databases/Samples?query=H4sIAAAAAAAAAytKzEtPVahQSCvKz1UwVCjJVzA0MFAoLkktUDDkqlEoLs3NTSzKrEpVKANSiXnJqZlpGhU6ChWqRgq2tgoGmgA5lfgVQAAAAA==)**\]**

```kusto
range x from 1 to 100 step 1
| summarize varianceif(x, x%2 == 0)
```

**Results**

|varianceif_x|
|---|
|850|
