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

# Commands

This document lists all available commands in the Flash Gangs resource.

***

## Player Commands

### Gangs Menu

**Command:** `Config.Command` (default: `gangs`)

**Description:** Opens the gangs menu interface

**Usage:**
```
/gangs
```

**Permissions:** Available to all players

***

## Admin Commands

All admin commands require the `Config.RestrictedGroup` (default: `group.admin`) permission level.

### Admin Dashboard

**Command:** `Config.AdminDashboardCommand` (default: `adminui`)

**Description:** Opens the admin dashboard interface

**Usage:**
```
/[command]
```

**Example:**
```
/adminui
```

**Permissions:** Requires `Config.RestrictedGroup` (default: `group.admin`) permission level

**Note:** Replace `[command]` with the value of `Config.AdminDashboardCommand` (default: `adminui`). Opens the admin dashboard interface for managing gangs, territories, and other administrative functions.

***

### Add Player to Gang

**Command:** `Config.AddPlayerToGangCommand` (default: `setplayergang`)

**Description:** Set a player's gang (Custom gangs only)

**Usage:**
```
/[command] [playerId] [gangName] [optional:rank]
```

**Parameters:**
* `playerId` (number): Target player's server ID
* `gangName` (string): Gang name to add the player to
* `rank` (number, optional): Rank level in the gang (default: 0)

**Example:**
```
/setplayergang 1 ballas 3
```

**Note:** Replace `[command]` with the value of `Config.AddPlayerToGangCommand` (default: `setplayergang`)

**Note:** This command only works when `Config.UseFrameworkGangs` is set to `false`.

***

### Add Gang Strike

**Command:** `Config.AddGangStrikeCommand` (default: `addgangstrike`)

**Description:** Add a strike to a gang

**Usage:**
```
/[command] [gangName] [reason]
```

**Parameters:**
* `gangName` (string): Gang name to give a strike to
* `reason` (string, optional): Reason for the strike

**Example:**
```
/addgangstrike ballas Violation of server rules
```

**Note:** Replace `[command]` with the value of `Config.AddGangStrikeCommand` (default: `addgangstrike`)

***

### Remove Gang Strike

**Command:** `Config.RemoveGangStrikeCommand` (default: `removegangstrike`)

**Description:** Remove a strike from a gang

**Usage:**
```
/[command] [gangName] [reason]
```

**Parameters:**
* `gangName` (string): Gang name to remove strike from
* `reason` (string, optional): Reason for removing the strike

**Example:**
```
/removegangstrike ballas Strike appeal accepted
```

**Note:** Replace `[command]` with the value of `Config.RemoveGangStrikeCommand` (default: `removegangstrike`)

***

### Reset Gang Strikes

**Command:** `Config.ResetGangStrikesCommand` (default: `resetgangstrikes`)

**Description:** Reset all strikes for a gang

**Usage:**
```
/[command] [gangName] [reason]
```

**Parameters:**
* `gangName` (string): Gang name to reset strikes for
* `reason` (string, optional): Reason for resetting the strikes

**Example:**
```
/resetgangstrikes ballas Fresh start
```

**Note:** Replace `[command]` with the value of `Config.ResetGangStrikesCommand` (default: `resetgangstrikes`)

***

## Configuration

All commands can be customized in `shared/config.lua`:

```lua
-- Main gangs menu command
Config.Command = 'gangs'

-- Admin commands configuration
Config.AdminDashboardCommand = 'adminui'
Config.AddPlayerToGangCommand = 'setplayergang'
Config.AddGangStrikeCommand = 'addgangstrike'
Config.RemoveGangStrikeCommand = 'removegangstrike'
Config.ResetGangStrikesCommand = 'resetgangstrikes'
Config.RestrictedGroup = 'group.admin'
```

