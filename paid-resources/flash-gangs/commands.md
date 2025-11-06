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

## Player Comands

### Gangs Menu

**Command:** `Config.Command` (default: `gangs`)

**Description:** Opens the gangs menu interface

**Usage:**

```
/gang
```

**Permissions:** Available to all players

***

## Admin Commands

All admin commands require the `group.admin` permission level.

### Add Player to Gang

**Command:** `Config.AdminCommands.AddToGang.command` (default: `setplayergang`)

**Description:** `Config.AdminCommands.AddToGang.description` (default: "Add a player to a gang - Custom gangs only")

**Usage:**

```
/setplayergang [playerId] [gangName] [optional:rank]
```

**Parameters:**

* `playerId` (number): Target player's server ID
* `gangName` (string): Gang name to add the player to
* `rank` (number, optional): Rank level in the gang (default: 0)

**Example:**

```
/setplayergang 1 ballas 3
```

**Note:** This command only works when `Config.UseFrameworkGangs` is set to `false`.

***

### Add Gang Strike

**Command:** `Config.AdminCommands.AddGangStrike.command` (default: `addgangstrike`)

**Description:** `Config.AdminCommands.AddGangStrike.description` (default: "Add a strike to a gang")

**Usage:**

```
/addgangstrike [gangName] [reason]
```

**Parameters:**

* `gangName` (string): Gang name to give a strike to
* `reason` (string, optional): Reason for the strike

**Example:**

```
/addgangstrike ballas Violation of server rules
```

***

### Remove Gang Strike

**Command:** `Config.AdminCommands.RemoveGangStrike.command` (default: `removegangstrike`)

**Description:** `Config.AdminCommands.RemoveGangStrike.description` (default: "Remove a strike from a gang")

**Usage:**

```
/removegangstrike [gangName] [reason]
```

**Parameters:**

* `gangName` (string): Gang name to remove strike from
* `reason` (string, optional): Reason for removing the strike

**Example:**

```
/removegangstrike ballas Strike appeal accepted
```

***

### Reset Gang Strikes

**Command:** `Config.AdminCommands.ResetGangStrikes.command` (default: `resetgangstrikes`)

**Description:** `Config.AdminCommands.ResetGangStrikes.description` (default: "Reset all strikes for a gang")

**Usage:**

```
/resetgangstrikes [gangName] [reason]
```

**Parameters:**

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
Config.Command = 'gang'

-- Admin commands configuration
Config.AdminCommands = {
    AddToGang = {
        command = 'setplayergang',
        description = 'Add a player to a gang',
        restricted = 'group.admin'
    },
    AddGangStrike = {
        command = 'addgangstrike',
        description = 'Add a strike to a gang',
        restricted = 'group.admin'
    },
    RemoveGangStrike = {
        command = 'removegangstrike',
        description = 'Remove a strike from a gang',
        restricted = 'group.admin'
    },
    ResetGangStrikes = {
        command = 'resetgangstrikes',
        description = 'Reset all strikes for a gang',
        restricted = 'group.admin'
    }
}
```
