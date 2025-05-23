---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: false
---

# Configuration

<details>

<summary>Config File</summary>

```
Config = {}

-- Enable debug mode for troubleshooting
Config.Debug = false
-- Enable version checking
Config.VersionCheck = true -- Keep track of the latest version

Config.Locale = "en" -- Options: "en", "fr", "es", etc.

-- Framework configuration
Config.Framework = "auto" -- Options: "auto", "esx", "qb", "qbx"
Config.esx = {
    useOldExport = false -- Set to true if using an older version of ESX
}

-- Inventory configuration
Config.Inventory = "auto" -- Options: "auto", "ox_inventory", "qs-inventory"

-- Image URL configuration
-- for ox inventory use: nui://ox_inventory/web/images/
-- for qs inventory use: nui://qs-inventory/html/images/
Config.ImgURL = "nui://ox_inventory/web/images/" -- Imgs folder link for item images

-- Price fluctuation settings
Config.FluctuationIncrease = 10  -- % increase if demand is high
Config.FluctuationDecrease = 10  -- % decrease if supply is high

-- Price update time
-- Recommended time to be from 15 to whatever you want
Config.PriceUpdateTime = 15      -- Minutes between price updates

-- Optional: Price multiplier based on item quality/durability
Config.QualityMultiplier = false -- Set to false if you don't want quality to affect price

Config.AllowSellAnywhere = false -- If true, items can be sold at any pawnshop. If false, items can only be sold at pawnshops that list them.

-- Command Configuration
Config.PricesCommand = {
    enabled = false, -- Enable or disable the prices command
    name = "prices", -- Command name
    help = "View current pawnshop prices" -- Command help text
}

-- Target configuration
Config.Target = "TextUI" -- Options: "ox", "qb", "TextUI"

-- Target configuration
Config.TargetSettings = {
    -- TextUI target settings
    TextUI = {
        label = "[E] Open Pawnshop",
    },
    -- ox target settings
    ox = {
        icon = "fas fa-store",
        label = "Open Pawnshop",
        distance = 2.0
    },
    -- qb target settings
    qb = {
        icon = "fas fa-store",
        label = "Open Pawnshop",
        distance = 2.0
    }
}

-- Blacklisted items that cannot be sold
Config.BlacklistedItems = {
    'money',
    'cash',
    'black_money',
}

-- Pawnshop Locations
Config.Category = {
    [1] = {
        CategoryLabel = "Downtown Pawnshop", -- Category label
        Blip = {
            enable = true, -- Enable blip
            blipSprite = 605, -- Blip sprite
            blipDisplay = 4, -- Blip display
            blipScale = 0.7, -- Blip scale
            blipColour = 2, -- Blip colour
            blipDisplayName = "Pawn Shop" -- Blip display name
        },
        Ped = {
            model = 's_m_o_busker_01',                                    -- Ped model
            location = vector3(182.584625, -1319.7626, 29.313599),       -- Ped location
            heading = 240.94488,                                         -- Ped heading
            interactionRange = 2.0,                                      -- Interaction range
        },
        Products = {
            [1] = {
                productName = "diamond_ring", -- Product name
                productLabel = "Diamond Ring", -- Product label
                productPrice = "500", -- Product price
                moneyType = "money" -- Money type
            },
            [2] = {
                productName = "diamond_earring",
                productLabel = "Diamond Earring",
                productPrice = "300",
                moneyType = "money"
            },
            [3] = {
                productName = "phone",
                productLabel = "Phone",
                productPrice = "1500",
                moneyType = "money"
            },
            [4] = {
                productName = "radio",
                productLabel = "Radio",
                productPrice = "2000",
                moneyType = "money"
            },
            [5] = {
                productName = "diamond",
                productLabel = "Diamond",
                productPrice = "750",
                moneyType = "money"
            },
            [6] = {
                productName = "gold_ring",
                productLabel = "Gold Ring",
                productPrice = "750",
                moneyType = "money"
            },
            [7] = {
                productName = "gold_earrings",
                productLabel = "Gold Earrings",
                productPrice = "750",
                moneyType = "money"
            },
            [8] = {
                productName = "rolex",
                productLabel = "Gold Bar",
                productPrice = "4500",
                moneyType = "money"
            },
            [9] = {
                productName = "goldchain",
                productLabel = "Gold Chain",
                productPrice = "1500",
                moneyType = "money"
            },
            -- Add more items as needed
        }
    }
    -- Add more pawnshop locations as needed
}
```

</details>
