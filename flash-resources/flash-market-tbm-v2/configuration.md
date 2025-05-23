---
layout:
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
---

# Configuration

## Basic Configuration

<details>

<summary>Basic Configuration</summary>

```lua
Config = Config or {}

-- Debug and Version Settings
Config.Debug = false
Config.VersionCheck = true

-- Framework Settings
Config.Framework = "auto" -- Options: "auto", "esx", "qb", "qbx"
Config.esx = {
    useOldExport = false -- Set to true if using an older version of ESX
}

-- Inventory Settings
Config.Inventory = "auto" -- Options: "auto", "ox", "qs"
Config.InventoryImagePath = "nui://ox_inventory/web/images/"

-- Market Features
Config.EnableVehicleMarket = true
Config.EnableMyVehicles = true
Config.UseJGDealership = false

-- Command Settings
Config.CommandEnabled = true
Config.Command = 'market'
Config.CommandDescription = 'Open the Market menu'

-- Language Settings
Config.Locale = "en" -- Options: "en", "ar", "de", "es", "fr", "it", "pt"
```

</details>

## Location Configuration

<details>

<summary>Location Configuration</summary>

```lua
-- Location Settings
Config.EnableLocations = false
Config.Target = "TextUI" -- Options: "ox", "qb", "TextUI"

-- Blip Settings
Config.EnableBlips = false
Config.BlipSettings = {
    sprite = 605,
    color = 2,
    scale = 0.7,
    display = 4,
    shortRange = true,
    name = "Marketplace"
}

-- Market Locations
Config.Locations = {
    {
        label = "Open Marketplace",
        icon = "fa-solid fa-store",
        rotation = 45.0,
        debug = false,
        coords = vector3(371.49, -941.89, 29.44),
        size = vector3(2.0, 2.0, 2.0),
        ped = {
            enabled = true,
            model = "a_m_m_business_01",
            coords = vector4(371.49, -941.89, 28.44, 181.24),
            scenario = "WORLD_HUMAN_AA_SMOKE"
        }
    }
}
```

</details>

## Currency Configuration

<details>

<summary>Currency Configuration</summary>

```lua
-- Available Currencies
Config.Currencies = {
    {
        name = "Cash",
        id = "money",
        item = "money",
        icon = "fa-solid fa-dollar-sign",
        hideSeller = false
    },
    {
        name = "Black Money",
        id = "black_money",
        item = "black_money",
        icon = "fa-solid fa-money-bill",
        hideSeller = false
    }
    -- Add any other currencies here
}

-- Item-Specific Currency Restrictions
Config.ItemCurrencies = {
    ["WEAPON_PISTOL"] = "black_money",
    ["WEAPON_SMG"] = "money"
}
```

</details>

## Vehicle Configuration

<details>

<summary>Vehicle Configuration</summary>

```lua
-- Vehicle Classes
Config.VehicleClasses = {
    [0] = "Compacts",
    [1] = "Sedans",
    [2] = "SUVs",
    [3] = "Coupes",
    [4] = "Muscle",
    [5] = "Sports Classics",
    [6] = "Sports",
    [7] = "Super",
    [8] = "Motorcycles",
    [9] = "Off-road",
    [10] = "Industrial",
    [11] = "Utility",
    [12] = "Vans",
    [13] = "Cycles",
    [14] = "Boats",
    [15] = "Helicopters",
    [16] = "Planes",
    [17] = "Service",
    [18] = "Emergency",
    [19] = "Military",
    [20] = "Commercial",
    [21] = "Trains"
}

-- Blacklisted Vehicles
Config.BlacklistedVehicles = {
    "POLICE",
    "POLICE2",
    "POLICE3",
    "AMBULANCE"
}
```

</details>

## Item Configuration

<details>

<summary>Item Configuration</summary>

```lua
-- Blacklisted Items
Config.BlacklistedItems = {
    "money",
    "cash",
    "black_money"
}
```

</details>

## Image Configuration

<details>

<summary>Image Configuration</summary>

```lua
-- Vehicle Image Settings
Config.Images = {
    BaseURL = "https://r2.fivemanage.com",
    Token = "BmrEYpTbKc06q3WsdNPd3"
}
```

</details>

## Webhook Configuration

<details>

<summary>Webhook Configuration</summary>

```lua
-- Webhook Settings
Config.EnableWebhooks = false

Config.Webhooks = {
    ['ItemListed'] = {
        Enabled = false,
        Username = "Flash Market",
        Icon = '',
        URL = '',
        Color = 0x3498DB,
    },
    ['ItemPurchased'] = {
        Enabled = false,
        Username = "Flash Market",
        Icon = '',
        URL = '',
        Color = 0x2ECC71,
    },
    ['ItemRemoved'] = {
        Enabled = false,
        Username = "Flash Market",
        Icon = '',
        URL = '',
        Color = 0xE74C3C,
    },
    ['MoneyClaimed'] = {
        Enabled = false,
        Username = "Flash Market",
        Icon = '',
        URL = '',
        Color = 0x2ECC71,
    },
    ['ItemPriceUpdated'] = {
        Enabled = false,
        Username = "Flash Market",
        Icon = '',
        URL = '',
        Color = 0xF39C12,
    },
    ['VehicleListed'] = {
        Enabled = false,
        Username = "Flash Market",
        Icon = '',
        URL = '',
        Color = 0x1ABC9C,
    },
    ['VehiclePurchased'] = {
        Enabled = false,
        Username = "Flash Market",
        Icon = '',
        URL = '',
        Color = 0x2ECC71,
    }
}
```

</details>
