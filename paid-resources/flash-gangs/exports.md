---
layout:
  width: default
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
  metadata:
    visible: false
---

# Exports

## AddGangStrike

Adds a strike to a gang.

{% code fullWidth="true" %}
```lua
AddGangStrike(gangName, reason, adminName)
```
{% endcode %}

* `gangName` (string): The name of the gang
* `reason` (string): Reason for adding the strike
* `adminName` (string): Name of the admin adding the strike

**Example**

{% code overflow="wrap" fullWidth="true" %}
```lua
exports['flash-gangs']:AddGangStrike('ballas', 'Violation of server rules', 'AdminName')
```
{% endcode %}

## RemoveGangStrike

Removes a strike from a gang (decreases by 1, minimum 0).

* `gangName` (string): The name of the gang
* `reason` (string): Reason for removing the strike
* `adminName` (string): Name of the admin removing the strike

{% code fullWidth="true" %}
```lua
RemoveGangStrike(gangName, reason, adminName)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```lua
exports['flash-gangs']:RemoveGangStrike('ballas', 'Strike appeal accepted', 'AdminName')
```
{% endcode %}
