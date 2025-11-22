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

### StartDrugSelling

Starts the drug selling process for the local player. This function will:

* Check if the player is in a vehicle or water (returns error if so)
* Check if drug selling is already active (returns error if so)
* Verify the player has sellable items configured in `Config.Drugs.Items`
* Start the selling loop if all checks pass

```lua
StartDrugSelling()
```

Returns: `success (boolean), message (string)`

**Return Values:**

* `success`: `true` if the check was initiated successfully, `false` if validation failed
* `message`: Status message describing the result

**Possible Return Messages:**

* `"Checking for sellable items..."` - Successfully initiated item check
* `"Cannot start drug selling while in a vehicle"` - Player is in a vehicle
* `"Cannot start drug selling while in water"` - Player is swimming or in water
* `"Drug selling is already active"` - Drug selling is already running

**Note:** The function will trigger a server-side check for sellable items. If items are found, the selling loop will start automatically. If no items are found, the player will receive a notification and selling will not start.

**Example:**

```lua
local success, message = exports['flash-gangs']:StartDrugSelling()
if success then
    print('Drug selling check initiated: ' .. message)
else
    print('Failed to start drug selling: ' .. message)
end
```

**Example with error handling:**

```lua
local success, message = exports['flash-gangs']:StartDrugSelling()
if not success then
    -- Handle error cases
    if message == "Cannot start drug selling while in a vehicle" then
        -- Player needs to exit vehicle
    elseif message == "Cannot start drug selling while in water" then
        -- Player needs to get out of water
    elseif message == "Drug selling is already active" then
        -- Already selling, no action needed
    end
end
```

***

### StopDrugSelling

Stops the drug selling process for the local player. This function will:

* Check if drug selling is currently active
* Stop the selling loop
* Clear player tasks
* Show a notification to the player

```lua
StopDrugSelling()
```

Returns: `success (boolean), message (string)`

**Return Values:**

* `success`: `true` if drug selling was stopped, `false` if it wasn't active
* `message`: Status message describing the result

**Possible Return Messages:**

* `"Drug selling disabled"` - Successfully stopped drug selling
* `"Drug selling is not active"` - Drug selling was not active, nothing to stop

**Example:**

```lua
local success, message = exports['flash-gangs']:StopDrugSelling()
if success then
    print('Drug selling stopped: ' .. message)
else
    print('Could not stop drug selling: ' .. message)
end
```

**Example with state check:**

```lua
-- Check state first, then stop if active
local isSelling = exports['flash-gangs']:GetDrugSellingState()
if isSelling then
    local success, message = exports['flash-gangs']:StopDrugSelling()
    if success then
        print('Successfully stopped drug selling')
    end
end
```

***

### Complete Usage Example

Here's a complete example showing how to use all three exports together:

```lua
-- Check current state
local currentState = exports['flash-gangs']:GetDrugSellingState()
print('Current selling state: ' .. tostring(currentState))

-- Start selling if not already active
if not currentState then
    local success, message = exports['flash-gangs']:StartDrugSelling()
    if success then
        print('Started drug selling: ' .. message)
    else
        print('Failed to start: ' .. message)
    end
end

-- Later, stop selling
local success, message = exports['flash-gangs']:StopDrugSelling()
if success then
    print('Stopped drug selling: ' .. message)
end
```

***

