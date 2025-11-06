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

**Description:** Opens the admin dashboard interface

**Command:** `Config.AdminDashboardCommand`

```
/adminui
```

**Permissions:** Requires `Config.RestrictedGroup` (default: `group.admin`) permission level

***

### Add Player to Gang

**Description:** Set a player's gang (Custom gangs only)

**Command:** `Config.AddPlayerToGangCommand`

```
/setplayergang [playerId] [gangName] [optional:rank]
```

* `playerId` (number): Target player's server ID
* `gangName` (string): Gang name to add the player to
* `rank` (number, optional): Rank level in the gang (default: 0)

**Example:**

```
/setplayergang 1 ballas 3
```

**Note:** Replace `[command]` with the value of `Config.AddPlayerToGangCommand` (default: `setplayergang`)

**Note:** This command works when `Config.UseFrameworkGangs` is set to `false`.

***

### Add Gang Strike

**Description:** Add a strike to a gang

**Command:** `Config.AddGangStrikeCommand` (default: `addgangstrike`)

**Usage:**

```
/addgangstrike [gangName] [reason]
```

* `gangName` (string): Gang name to give a strike to
* `reason` (string, optional): Reason for the strike

**Example:**

```
/addgangstrike ballas Violation of server rules
```

***

### Remove Gang Strike

**Description:** Remove a strike from a gang

**Command:** `Config.RemoveGangStrikeCommand` (default: `removegangstrike`)

**Usage:**

```
/removegangstrike [gangName] [reason]
```

* `gangName` (string): Gang name to remove strike from
* `reason` (string, optional): Reason for removing the strike

**Example:**

```
/removegangstrike ballas Strike appeal accepted
```

***

### Reset Gang Strikes

**Description:** Reset all strikes for a gang

**Command:** `Config.ResetGangStrikesCommand` (default: `resetgangstrikes`)

**Usage:**

```
/resetgangstrikes [gangName] [reason]
```

* `gangName` (string): Gang name to reset strikes for
* `reason` (string, optional): Reason for resetting the strikes

**Example:**

```
/resetgangstrikes ballas Fresh start
```

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
