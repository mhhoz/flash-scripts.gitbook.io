---
description: >-
  The Flash Pawnshop resource provides four main exports that allow other
  resources to interact with the pawnshop UI
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# API

## Client Exports

***

## OpenUI

Opens the main pawnshop interface for a specific shop

```lua
exports['flash-pawnshop']:OpenUI(shopId)
```

## CloseUI

Closes the main pawnshop interface

{% code fullWidth="false" %}
```lua
exports['flash-pawnshop']:CloseUI()
```
{% endcode %}

## OpenPricesUI

```lua
exports['flash-pawnshop']:OpenPricesUI()
```

## ClosePricesUI

```lua
exports['flash-pawnshop']:ClosePricesUI()
```





