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

# Flash Gangs - Exports Documentation

This document explains how to use the exported functions from `server/functions.lua`.

---

## Strike Management

### `AddGangStrike`

Adds a strike to a gang.

**Parameters:**
- `gangName` (string): The name of the gang  
- `reason` (string): Reason for adding the strike  
- `adminName` (string): Name of the admin adding the strike  

**Returns:** `nil` (async operation, logs activity automatically)

**Usage Example:**
```lua
exports['flash-gangs']:AddGangStrike('ballas', 'Violation of server rules', 'AdminName')
```

**Return Example:**
```lua
-- No return value, operation is async
-- Activity is logged automatically
```

---

### `RemoveGangStrike`

Removes a strike from a gang (decreases by 1, minimum 0).

**Parameters:**
- `gangName` (string): The name of the gang  
- `reason` (string): Reason for removing the strike  
- `adminName` (string): Name of the admin removing the strike  

**Returns:** `nil` (async operation, logs activity automatically)

**Usage Example:**
```lua
exports['flash-gangs']:RemoveGangStrike('ballas', 'Strike appeal accepted', 'AdminName')
```

**Return Example:**
```lua
-- No return value, operation is async
-- Activity is logged automatically
```

---

### `ResetGangStrikes`

Resets all strikes for a gang to 0.

**Parameters:**
- `gangName` (string): The name of the gang  
- `reason` (string): Reason for resetting strikes  
- `adminName` (string): Name of the admin resetting strikes  

**Returns:** `nil` (async operation, logs activity automatically)

**Usage Example:**
```lua
exports['flash-gangs']:ResetGangStrikes('ballas', 'Fresh start', 'AdminName')
```

**Return Example:**
```lua
-- No return value, operation is async
-- Activity is logged automatically
```

---

### `GetGangStrikes`

Gets the current number of strikes for a gang.

**Parameters:**
- `gangName` (string): The name of the gang  

**Returns:** `number` (strike count, 0 if gang not found or invalid gang name)

**Usage Example:**
```lua
local strikes = exports['flash-gangs']:GetGangStrikes('ballas')
print('Gang has ' .. strikes .. ' strikes')
```

**Return Example:**
```lua
local strikes = exports['flash-gangs']:GetGangStrikes('ballas')
-- Returns: 3 (or 0 if gang not found)
```

---

## Member Management

### `AddOrUpdatePlayerToGang`

Adds a new player to a gang or updates an existing member's rank and grade. Preserves existing XP and join date.

**Parameters:**
- `source` (number): Player server ID  
- `gangName` (string): The name of the gang  
- `rank` (string): Rank name for the player  
- `grade` (number): Grade/level for the player  

**Returns:** `boolean` (`true` if player was successfully added/updated, `false` if failed)

**Usage Example:**
```lua
local success = exports['flash-gangs']:AddOrUpdatePlayerToGang(1, 'ballas', 'Member', 1)
if success then
    print('Player added/updated successfully')
else
    print('Failed to add/update player')
end
```

**Return Example:**
```lua
local success = exports['flash-gangs']:AddOrUpdatePlayerToGang(1, 'ballas', 'Member', 1)
-- Returns: true (if successful) or false (if player not found, gang not found, or invalid parameters)
-- If player is new: adds with xp = 0, join_date = current date
-- If player exists: updates rank/grade, preserves xp and join_date
```

---

### `RemovePlayerFromGang`

Removes a player from a specific gang.

**Parameters:**
- `source` (number): Player server ID  
- `gangName` (string): The name of the gang  

**Returns:** `boolean` (`true` if player was successfully removed, `false` if failed)

**Usage Example:**
```lua
local success = exports['flash-gangs']:RemovePlayerFromGang(1, 'ballas')
if success then
    print('Player removed successfully')
else
    print('Failed to remove player')
end
```

**Return Example:**
```lua
local success = exports['flash-gangs']:RemovePlayerFromGang(1, 'ballas')
-- Returns: true (if player was removed) or false (if player not found, gang not found, or invalid parameters)
```

---

### `RemovePlayerFromAllGangs`

Removes a player from all gangs they are a member of.

**Parameters:**
- `source` (number): Player server ID  

**Returns:** `boolean` (`true` if player was removed from at least one gang, `false` if not found in any gang or invalid source)

**Usage Example:**
```lua
local success = exports['flash-gangs']:RemovePlayerFromAllGangs(1)
if success then
    print('Player removed from all gangs')
else
    print('Player not found in any gang')
end
```

**Return Example:**
```lua
local success = exports['flash-gangs']:RemovePlayerFromAllGangs(1)
-- Returns: true (if player was removed from at least one gang) or false (if player not found in any gang or invalid source)
```

---

## Experience Points (XP)

### `AddGangXP`

Adds XP to a gang's total XP.

**Parameters:**
- `gangName` (string): The name of the gang  
- `xpAmount` (number): Amount of XP to add (must be > 0)

**Returns:** `boolean` (`true` if XP was successfully added, `false` if failed)

**Usage Example:**
```lua
local success = exports['flash-gangs']:AddGangXP('ballas', 100)
if success then
    print('XP added successfully')
else
    print('Failed to add XP')
end
```

**Return Example:**
```lua
local success = exports['flash-gangs']:AddGangXP('ballas', 100)
-- Returns: true (if XP was added) or false (if gang not found, invalid parameters, or update failed)
```

---

### `AddMemberXPByCitizenId`

Adds XP to a specific member by their citizen ID. Searches all gangs to find the member.

**Parameters:**
- `citizenid` (string): Player's citizen ID  
- `xpAmount` (number): Amount of XP to add (must be > 0)

**Returns:** `nil` (async operation)

**Usage Example:**
```lua
exports['flash-gangs']:AddMemberXPByCitizenId('ABC12345', 50)
```

**Return Example:**
```lua
-- No return value, operation is async
-- Updates member.xp in the gang they belong to
```

---

## Permissions

### `GetPlayerRankPermissions`

Gets the rank permissions for a player based on their citizen ID and current gang membership.

**Parameters:**
- `citizenid` (string): Player's citizen ID  

**Returns:** `table` or `nil`

**Usage Example:**
```lua
local permissions = exports['flash-gangs']:GetPlayerRankPermissions('ABC12345')
if permissions then
    print('Player has permissions: ' .. json.encode(permissions))
else
    print('Player not found in any gang or no rank permissions')
end
```

**Return Example:**
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
