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

```lua
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

```

***
