---
description: The following exports are available on the client-side only.
---

# Client

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
