---
description: The following exports are available on the client-side only.
---

# Client

## Territory

### GetPlayerCurrentTerritory

Gets the name of the territory the player is currently standing in. Returns `nil` if the player is not inside any territory.

```lua
GetPlayerCurrentTerritory()
```

Returns: `string` or `nil`

**Example:**

```lua
local territory = exports['flash-gangs']:GetPlayerCurrentTerritory()
if territory then
    print('Player is in territory: ' .. territory)
else
    print('Player is not in any territory')
end
```

***

## Member

### GetPlayerGang

Gets the player's gang data including name, label, rank, level, and boss status

```lua
GetPlayerGang()
```

Returns: `table` or `nil`

**Example:**

````lua
local playerGang = exports['flash-gangs']:GetPlayerGang()
if playerGang then
    print('Gang name: ' .. playerGang.name)
    print('Gang label: ' .. playerGang.label)
    print('Grade: ' .. playerGang.grade)
    print('Level: ' .. playerGang.level)
    print('Is Boss: ' .. tostring(playerGang.isboss))
else
    print('Player is not in a gang')
end

-- {
--    name = "ballas",        -- Gang internal name
--    label = "Ballas",       -- Gang display name
--    grade = "Member",       -- Player's rank name
--    level = 1,              -- Player's rank level/grade
--    isboss = false          -- Whether player is a boss
-- }

# Drug Selling Exports

This document explains how to use the exported functions for the drug selling feature. All exports are available on the **client-side** only.

***

## GetDrugSellingState

Gets the current state of drug selling for the local player.

```lua
GetDrugSellingState()
````

Returns: `boolean` - `true` if drug selling is currently active, `false` otherwise.

**Example:**

```lua
local isSelling = exports['flash-gangs']:GetDrugSellingState()
if isSelling then
    print('Player is currently selling drugs')
else
    print('Player is not selling drugs')
end
```

***

## Drug Selling

### StartSelling

Starts the drug selling process for the player.

```lua
StartSelling()
```

Returns: `boolean`

* Returns `true` if the selling process was initiated successfully
* Returns `false` if:
  * The player is already selling drugs
  * The player is in a vehicle
  * The player is swimming or in water

**Example:**

```lua
local success = exports['flash-gangs']:StartSelling()
if success then
    print('Drug selling started')
else
    print('Failed to start selling - check if already selling or invalid conditions')
end
```

***

### StopSelling

Stops the drug selling process for the player. Clears any active selling tasks and animations.

```lua
StopSelling()
```

Returns: `boolean`

* Returns `true` if the selling process was stopped successfully
* Returns `false` if the player is not currently selling drugs

**Example:**

```lua
local success = exports['flash-gangs']:StopSelling()
if success then
    print('Drug selling stopped')
else
    print('Player is not currently selling drugs')
end
```

***

### IsSelling

Checks if the player is currently in the drug selling state.

```lua
IsSelling()
```

Returns: `boolean`

* Returns `true` if the player is currently selling drugs
* Returns `false` if the player is not selling drugs

**Example:**

```lua
local isSelling = exports['flash-gangs']:IsSelling()
if isSelling then
    print('Player is currently selling drugs')
else
    print('Player is not selling drugs')
end
```

***

