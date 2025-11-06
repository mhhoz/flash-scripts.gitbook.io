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

## Experience Points (XP)

## AddGangXP

Adds XP to a gang's total XP.

* `gangName` (string): The name of the gang  
* `xpAmount` (number): Amount of XP to add (must be > 0)

**Returns:** `boolean` (returns false if invalid parameters, but async so return may not be accessible)

{% code fullWidth="true" %}
```lua
AddGangXP(gangName, xpAmount)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```lua
exports['flash-gangs']:AddGangXP('ballas', 100)
```
{% endcode %}

**Return Example**

{% code overflow="wrap" fullWidth="true" %}
```lua
-- Returns false if gangName is nil, 'none', or xpAmount <= 0
-- Note: Actual database update is async, return value may not reflect success
-- Returns: false (on invalid input)
```
{% endcode %}

---

## AddMemberXPByCitizenId

Adds XP to a specific member by their citizen ID. Searches all gangs to find the member.

* `citizenid` (string): Player's citizen ID  
* `xpAmount` (number): Amount of XP to add (must be > 0)

**Returns:** `nil` (async operation)

{% code fullWidth="true" %}
```lua
AddMemberXPByCitizenId(citizenid, xpAmount)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```lua
exports['flash-gangs']:AddMemberXPByCitizenId('ABC12345', 50)
```
{% endcode %}

**Return Example**

{% code overflow="wrap" fullWidth="true" %}
```lua
-- No return value, operation is async
-- Updates member.xp in the gang they belong to
```
{% endcode %}

---

# Permissions

## GetPlayerRankPermissions

Gets the rank permissions for a player based on their citizen ID and current gang membership.

* `citizenid` (string): Player's citizen ID  

**Returns:** `table` or `nil`

{% code fullWidth="true" %}
```lua
GetPlayerRankPermissions(citizenid)
```
{% endcode %}

{% code overflow="wrap" fullWidth="true" %}
```lua
local permissions = exports['flash-gangs']:GetPlayerRankPermissions('ABC12345')
if permissions then
    print('Player has permissions: ' .. json.encode(permissions))
else
    print('Player not found in any gang or no rank permissions')
end
```
{% endcode %}

**Return Example**

{% code overflow="wrap" fullWidth="true" %}
```lua
-- Returns permissions table if player found and has rank
-- Example: {
--     ["invite_members"] = true,
--     ["kick_members"] = true,
--     ["manage_ranks"] = false,
--     ...
-- }

-- Returns nil if:
-- - Player not found in any gang
-- - No matching rank found for player's grade
-- - No gangs exist in database
```
{% endcode %}

