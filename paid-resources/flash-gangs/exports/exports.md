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

# Server

## Gang Information

### GetGangData

Gets the data for a specific gang, including color, label, image, motto, and other details. Returns default values if the gang is not found or if the gang name is invalid.

```lua
GetGangColor(gangName)
```

* `gangName`(string): The name of the gang to retrieve data for.

Returns: `table`

**Example:**

```lua
local gangData = exports['flash-gangs']:GetGangData('ballas')
if gangData then
    local decodedData = json.decode(gangData)
    print(json.encode(decodedData, { indent = true }))
end
```

```
-- Returns a table with the following structure:
{
    color = "#2d5590",                      -- Gang's primary color (hex string)
    label = "Ballas Gang",                  -- Display name of the gang
    image = "https://example.com/logo.png", -- Gang logo/image URL (or nil)
    motto = "Street Life",                  -- Gang motto (or nil)
    secondColor = "#0c0e11",                -- Gang's secondary color (or nil)
    name = "ballas"                         -- Internal gang name
}
```

### GetGangColor

Gets the color for a gang. Returns the gang's custom color, or default white if not found.

```lua
GetGangColor(gangName)
```

* `gangName` (string): The name of the gang

Returns: `string` (color)

**Example:**

```lua
local color, label = exports['flash-gangs']:GetGangColor('ballas')
print('Gang color: ' .. color)

-- Returns: "#ff0000" (or "#ffffff" if gang not found or is default gang)
```

## Strike Management

### AddGangStrike

Adds a strike to a gang.

```lua
AddGangStrike(gangName, reason, adminName)
```

* `gangName` (string): The name of the gang
* `reason` (string): Reason for adding the strike
* `adminName` (string): Name of the admin adding the strike

Returns: `boolean`

**Example:**

```lua
local success = exports['flash-gangs']:AddGangStrike('ballas', 'Violation of server rules', 'AdminName')
if success then
    print('Strike added successfully')
else
    print('Failed to add strike')
end
```

***

### RemoveGangStrike

Removes a strike from a gang (decreases by 1, minimum 0).

```lua
RemoveGangStrike(gangName, reason, adminName)
```

* `gangName` (string): The name of the gang
* `reason` (string): Reason for removing the strike
* `adminName` (string): Name of the admin removing the strike

Returns: `boolean`

**Example:**

{% code fullWidth="false" %}
```lua
local success = exports['flash-gangs']:RemoveGangStrike('ballas', 'Strike appeal accepted', 'AdminName')
if success then
    print('Strike removed successfully')
else
    print('Failed to remove strike')
end
```
{% endcode %}

***

### ResetGangStrikes

Resets all strikes for a gang to 0.

```lua
ResetGangStrikes(gangName, reason, adminName)
```

* `gangName` (string): The name of the gang
* `reason` (string): Reason for resetting strikes
* `adminName` (string): Name of the admin resetting strikes

Returns: `boolean`

**Example:**

```lua
local success = exports['flash-gangs']:ResetGangStrikes('ballas', 'Fresh start', 'AdminName')
if success then
    print('Strikes reset successfully')
else
    print('Failed to reset strikes')
end
```

***

### GetGangStrikes

Gets the current number of strikes for a gang.

```lua
GetGangStrikes(gangName)
```

* `gangName` (string): The name of the gang

Returns: `number`

**Examples:**

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

### AddPlayerToGang

Adds a new player to a gang or updates an existing member's rank and grade. Preserves existing XP and join date.

```lua
AddPlayerToGang(source, gangName, rank, grade)
```

* `source` (number): Player server ID
* `gangName` (string): The name of the gang
* `rank` (string): Rank name for the player
* `grade` (number): Grade/level for the player

Returns: `boolean`

**Example:**

```lua
local success = exports['flash-gangs']:AddPlayerToGang(1, 'ballas', 'Member', 1)
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

```lua
RemovePlayerFromGang(source, gangName)
```

* `source` (number): Player server ID
* `gangName` (string): The name of the gang

Returns: `boolean`

**Example:**

```lua
local success = exports['flash-gangs']:RemovePlayerFromGang(1, 'ballas')
if success then
    print('Player removed successfully')
else
    print('Failed to remove player')
end
```

***

### RemovePlayerFromAllGangs

Removes a player from all gangs they are a member of.

```lua
RemovePlayerFromAllGangs(source)
```

* `source` (number): Player server ID

Returns: `boolean`

**Example:**

```lua
local success = exports['flash-gangs']:RemovePlayerFromAllGangs(1)
if success then
    print('Player removed from all gangs')
else
    print('Player not found in any gang')
end
```

***

## Experience Points (XP)

### AddGangXP

Adds XP to a gang's total XP.

```lua
AddGangXP(gangName, xp)
```

* `gangName` (string): The name of the gang
* `xp` (number): Amount of XP to add (must be > 0)

Returns: `boolean`

**Example:**

```lua
local success = exports['flash-gangs']:AddGangXP('ballas', 100)
if success then
    print('XP added successfully')
else
    print('Failed to add XP - gang not found or invalid parameters')
end
```

***

### AddMemberXPByIdentifier

Adds XP to a specific member by their citizen ID. Searches all gangs to find the member.

```lua
AddMemberXPByIdentifier(identifier, xp)
```

* `identifier` (string): Player's citizen ID
* `xp` (number): Amount of XP to add (must be > 0)

Returns: `boolean`

**Example:**

```lua
local success = exports['flash-gangs']:AddMemberXPByIdentifier('ABC12345', 50)
if success then
    print('XP added successfully')
else
    print('Failed to add XP - member not found or invalid parameters')
end
```

***

## Permissions

### GetPlayerRankPermissions

Gets the rank permissions for a player based on their citizen ID and current gang membership.

```lua
GetPlayerRankPermissions(identifier)
```

* `identifier` (string): Player's citizen ID

Returns: `table` or `nil`

**Example:**

```lua
local permissions = exports['flash-gangs']:GetPlayerRankPermissions('ABC12345')
if permissions then
    print('Player has permissions: ' .. json.encode(permissions))
else
    print('Player not found in any gang or no rank permissions')
end
```

***
