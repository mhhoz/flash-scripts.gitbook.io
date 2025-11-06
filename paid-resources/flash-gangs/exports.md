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

---

## ResetGangStrikes

Resets all strikes for a gang to 0.

* `gangName` (string): The name of the gang
* `reason` (string): Reason for resetting strikes
* `adminName` (string): Name of the admin resetting strikes

{% code fullWidth="true" %}
```lua
ResetGangStrikes(gangName, reason, adminName)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```lua
exports['flash-gangs']:ResetGangStrikes('ballas', 'Fresh start', 'AdminName')
```
{% endcode %}

---

## GetGangStrikes

Gets the current number of strikes for a gang.

* `gangName` (string): The name of the gang  

**Returns:** `number` (strike count, 0 if gang not found or invalid gang name)

{% code fullWidth="true" %}
```lua
GetGangStrikes(gangName)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```lua
local strikes = exports['flash-gangs']:GetGangStrikes('ballas')
print('Gang has ' .. strikes .. ' strikes')
```
{% endcode %}

**Return Example**

{% code overflow="wrap" fullWidth="true" %}
```lua
local strikes = exports['flash-gangs']:GetGangStrikes('ballas')
-- Returns: 3 (or 0 if gang not found)
```
{% endcode %}

---

# Member Management

## AddOrUpdatePlayerToGang

Adds a new player to a gang or updates an existing member's rank and grade. Preserves existing XP and join date.

* `source` (number): Player server ID
* `gangName` (string): The name of the gang
* `rank` (string): Rank name for the player
* `grade` (number): Grade/level for the player

{% code fullWidth="true" %}
```lua
AddOrUpdatePlayerToGang(source, gangName, rank, grade)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```lua
exports['flash-gangs']:AddOrUpdatePlayerToGang(1, 'ballas', 'Member', 1)
```
{% endcode %}

---

## RemovePlayerFromGang

Removes a player from a specific gang.

* `source` (number): Player server ID
* `gangName` (string): The name of the gang

{% code fullWidth="true" %}
```lua
RemovePlayerFromGang(source, gangName)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```lua
exports['flash-gangs']:RemovePlayerFromGang(1, 'ballas')
```
{% endcode %}

---

## RemovePlayerFromAllGangs

Removes a player from all gangs they are a member of.

* `source` (number): Player server ID

{% code fullWidth="true" %}
```lua
RemovePlayerFromAllGangs(source)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```lua
exports['flash-gangs']:RemovePlayerFromAllGangs(1)
```
{% endcode %}
