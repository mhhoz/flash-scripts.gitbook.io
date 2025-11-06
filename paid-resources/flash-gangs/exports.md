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

This document explains how to use the exported functions from `server/functions.lua`.

***

## Strike Management

### AddGangStrike

Adds a strike to a gang.

* `gangName` (string): The name of the gang  
* `reason` (string): Reason for adding the strike  
* `adminName` (string): Name of the admin adding the strike  

Returns: `nil`

```lua
exports['flash-gangs']:AddGangStrike('ballas', 'Violation of server rules', 'AdminName')
```

```lua
-- No return value
-- Activity is logged automatically
```

***

### RemoveGangStrike

Removes a strike from a gang (decreases by 1, minimum 0).

* `gangName` (string): The name of the gang  
* `reason` (string): Reason for removing the strike  
* `adminName` (string): Name of the admin removing the strike  

Returns: `nil`

```lua
exports['flash-gangs']:RemoveGangStrike('ballas', 'Strike appeal accepted', 'AdminName')
```

```lua
-- No return value
-- Activity is logged automatically
```

***

### ResetGangStrikes

Resets all strikes for a gang to 0.

* `gangName` (string): The name of the gang  
* `reason` (string): Reason for resetting strikes  
* `adminName` (string): Name of the admin resetting strikes  

Returns: `nil`

```lua
exports['flash-gangs']:ResetGangStrikes('ballas', 'Fresh start', 'AdminName')
```

```lua
-- No return value
-- Activity is logged automatically
```

***

### GetGangStrikes

Gets the current number of strikes for a gang.

* `gangName` (string): The name of the gang  

Returns: `number`

```lua
local strikes = exports['flash-gangs']:GetGangStrikes('ballas')
print('Gang has ' .. strikes .. ' strikes')
```

```lua
local strikes = exports['flash-gangs']:GetGangStrikes('ballas')
-- Returns: 3 (or 0 if gang not found)
```

***

## Member Management

### AddOrUpdatePlayerToGang

Adds a new player to a gang or updates an existing member's rank and grade. Preserves existing XP and join date.

* `source` (number): Player server ID  
* `gangName` (string): The name of the gang  
* `rank` (string): Rank name for the player  
* `grade` (number): Grade/level for the player  

Returns: `boolean`

```lua
local success = exports['flash-gangs']:AddOrUpdatePlayerToGang(1, 'ballas', 'Member', 1)
if success then
    print('Player added/updated successfully')
else
    print('Failed to add/update player')
end
```

```lua
-- Returns: true or false
-- If player is new: adds with xp = 0, join_date = current date
-- If player exists: updates rank/grade, preserves xp and join_date
```

***

### RemovePlayerFromGang

Removes a player from a specific gang.

* `source` (number): Player server ID  
* `gangName` (string): The name of the gang  

Returns: `boolean`

```lua
local success = exports['flash-gangs']:RemovePlayerFromGang(1, 'ballas')
if success then
    print('Player removed successfully')
else
    print('Failed to remove player')
end
```

```lua
-- Returns: true or false
```

***

### RemovePlayerFromAllGangs

Removes a player from all gangs they are a member of.

* `source` (number): Player server ID  

Returns: `boolean`

```lua
local success = exports['flash-gangs']:RemovePlayerFromAllGangs(1)
if success then
    print('Player removed from all gangs')
else
    print('Player not found in any gang')
end
```

```lua
-- Returns: true or false
```

***

## Experience Points (XP)

### AddGangXP

Adds XP to a gang's total XP.

* `gangName` (string): The name of the gang  
* `xpAmount` (number): Amount of XP to add (must be > 0)  

Returns: `boolean`

```lua
local success = exports['flash-gangs']:AddGangXP('ballas', 100)
```

```lua
-- Returns: true or false
```

***

### AddMemberXPByCitizenId

Adds XP to a specific member by their citizen ID. Searches all gangs to find the member.

* `citizenid` (string): Player's citizen ID  
* `xpAmount` (number): Amount of XP to add (must be > 0)  

Returns: `nil`

```lua
exports['flash-gangs']:AddMemberXPByCitizenId('ABC12345', 50)
```

```lua
-- No return value
```

***

## Permissions

### GetPlayerRankPermissions

Gets the rank permissions for a player based on their citizen ID and current gang membership.

* `citizenid` (string): Player's citizen ID  

Returns: `table` or `nil`

```lua
local permissions = exports['flash-gangs']:GetPlayerRankPermissions('ABC12345')
if permissions then
    print('Player has permissions: ' .. json.encode(permissions))
else
    print('Player not found in any gang or no rank permissions')
end
```

```lua
-- Returns permissions table or nil
```
