# How to Setup

This comprehensive guide walks you through the configuration options in the Pawnshop resource, helping you tailor the resource to your server.

***

## Pawnshop Location Setup

### Basic Pawnshop Configuration

To add a new pawnshop, you'll modify the `Config.Pawnshops` table in the `shared/config.lua` file. Here's a step-by-step breakdown:

```lua
Config.Pawnshops = {
    [1] = {
        -- Unique identifier for the pawnshop
        PawnshopName = "Downtown Pawnshop",

        -- Location description
        ShopLocation = "Innocence Blvd",

        -- Blip (map marker) configuration
        Blip = {
            enable = true,
            blipSprite = 267,
            blipDisplay = 4,
            blipScale = 0.7,
            blipColour = 0,
            blipDisplayName = "Downtown Pawnshop"
        },

        -- NPC (Ped) configuration
        Ped = {
            model = 's_m_o_busker_01',
            location = vector4(182.584625, -1319.7626, 29.313599, 240.94488), -- x, y, z, heading
            interactionRange = 2.0
        },

        -- Product lists to be sold at this pawnshop (can use multiple lists)
        ProductList = {"jewelry", "food"},

        -- Ownership and management options
        Ownership = {
            ownable = false, -- Can this pawnshop be purchased/owned - Enable this first (Config.EnablePawnshopOwnership)
            price = 75000, -- Price to purchase this pawnshop
            renewalPrice = 37500, -- Price to renew ownership
            jobRestriction = nil, -- Job required to purchase (set to nil or empty string for no job restriction)
            owner = nil, -- Will be filled with owner identifier from database
            requireShopFunds = false, -- Require shop to have funds to buy items
            -- Set to false to allow selling without checking shop funds
            ownerCanEditPrices = false, -- Allow shop owners to edit prices from Management
            storeItemsInStash = true, -- If true, sold items will be added to the pawnshop stash and buying is restricted to only items in the stash
            enableStaticBuying = false, -- If true, show products from ProductList for buying with unlimited stock (ignores stash)

            -- Stash (storage) configuration
            stash = {
                enabled = true,
                slots = 100,
                maxWeight = 200,
                location = vector3(181.2731628418, -1323.1893310547, 29.315742492676),
                label = "Downtown Pawnshop Storage"
            },

            -- Management location
            management = {
                enabled = true,
                location = vector3(181.84, -1321.45, 29.32),
                label = "Downtown Pawnshop Management"
            }
        }
    }
    -- You can add more pawnshops here
}
```

**Key Ownership Settings Explained**:

* **ownable**: Must be `true` for ownership features to work (also requires `Config.EnablePawnshopOwnership = true`)
* **storeItemsInStash**: When `true`, sold items go to the stash and buying is limited to stash contents
* **enableStaticBuying**: When `true`, shows products from ProductList with unlimited stock (ignores stash)
* **requireShopFunds**: When `true`, shop must have funds to purchase items from players
* **ownerCanEditPrices**: When `true`, shop owners can edit prices from the Management interface

***

## Managing Product Lists

### Creating Product Lists

Product lists are defined in `Config.ProductLists`. Here's how to create and use them:

```lua
Config.ProductLists = {
    ["jewelry"] = {
        [1] = {
            productName = "diamond_ring", -- Item name (must match your inventory item)
            productLabel = "Diamond Ring", -- Display label
            productPrice = 500, -- Base price (number, not string)
            moneyType = "money", -- Money type (must be defined in Config.MoneyTypes)
            productType = "both" -- Options: "both", "buy", "sell"
        },
        [2] = {
            productName = "diamond_necklace",
            productLabel = "Diamond Necklace",
            productPrice = 1000,
            moneyType = "money",
            productType = "both"
        },
        [3] = {
            productName = "phone",
            productLabel = "Phone",
            productPrice = 1500,
            moneyType = "money",
            productType = "sell" -- Only sellable, cannot be bought
        },
        [4] = {
            productName = "radio",
            productLabel = "Radio",
            productPrice = 2000,
            moneyType = "black_money", -- Uses different currency
            productType = "buy" -- Only buyable, cannot be sold
        }
    },

    ["electronics"] = {
        [1] = {
            productName = "phone",
            productLabel = "Phone",
            productPrice = 1500,
            moneyType = "money",
            productType = "both"
        },
        [2] = {
            productName = "laptop",
            productLabel = "Laptop",
            productPrice = 2500,
            moneyType = "money",
            productType = "both"
        }
    }
}
```

**Product Type Options**:
* `"both"` - Item can be both bought and sold
* `"buy"` - Item can only be purchased from the pawnshop
* `"sell"` - Item can only be sold to the pawnshop

### Assigning Product Lists to Pawnshops

In the pawnshop configuration, use the product list names. You can assign multiple lists:

```lua
ProductList = {"jewelry", "electronics"} -- Multiple lists
```

Or a single list:

```lua
ProductList = {"jewelry"} -- Single list
```

***

## Item Blacklisting

Prevent certain items from being sold:

```lua
Config.BlacklistedItems = {
    'money',
    'cash',
    'black_money',
    'weapon_pistol',
    'police_badge'
}
```

***

## Pricing and Economy

### Price Fluctuation

Configure how prices change dynamically:

```lua
-- Basic fluctuation settings
Config.FluctuationIncrease = 15  -- % increase if demand is high
Config.FluctuationDecrease = 12  -- % decrease if supply is high
Config.PriceUpdateTime = 1      -- Minutes between price updates
Config.SeparateShopPrices = true -- If true, item prices will be independent for each shop
Config.AllowSellAnywhere = false -- If true, items can be sold at any pawnshop
Config.QualityMultiplier = false -- Set to false if you don't want quality to affect price
```

### Advanced Price Fluctuation Settings

Fine-tune the price fluctuation system:

```lua
Config.PriceFluctuation = {
    baseFactor = 0.05,              -- Base fluctuation factor (5%)
    noActivityDivisor = 200,        -- Divisor for no activity price change
    salesRatioThresholdHigh = 1.2,  -- Threshold for high sales ratio
    salesRatioThresholdLow = 0.8,   -- Threshold for low sales ratio
    singleActivityMultiplier = 0.6, -- Multiplier for single-sided activity
    minMultiplier = 0.2,            -- Minimum price as % of base price (20%)
    maxMultiplier = 4.0             -- Maximum price as % of base price (400%)
}
```

**Price Range**: Items can fluctuate between 20% and 400% of their base price.

***

## Interaction Settings

Configure how players interact with pawnshops:

```lua
Config.Target = "TextUI" -- Options: "ox", "qb", "TextUI"

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
```

### Notification System

Configure the notification system:

```lua
Config.Notification = "ox" -- Options: "qb", "esx", "qbx", "ox", "okok", "17mov", "mythic", "codem"
```

***

## Advanced Configuration

### Ownership and Management

Enable pawnshop ownership:

```lua
Config.EnablePawnshopOwnership = false -- If true, pawnshops can be purchased/owned
Config.PawnshopOwnershipDuration = 8 -- Days before ownership expires
Config.MaxPawnshopsPerPlayer = 1 -- Maximum number of pawnshops a player can own (set to 0 or nil for unlimited)
Config.PreventOwnerSelling = true -- Enable selling restrictions for both owners and employees
```

### Buying Configuration

Configure buying functionality:

```lua
Config.EnableBuying = false -- Set to false to disable buying items from pawnshop
Config.BuyPriceMode = "same" -- Options: "same" (no markup), "markup" (use multiplier)
Config.BuyPriceMultiplier = 1.5 -- Used when BuyPriceMode is set to "markup"
Config.BuyingAffectsPrices = false -- If true, buying items will affect market prices
```

### Money Types

Configure different money types:

```lua
Config.MoneyTypes = {
    ["money"] = {
        label = "Cash", -- Money type label
        icon = "fa-dollar-sign" -- FontAwesome icon
    },
    ["black_money"] = {
        label = "Dirty Money",
        icon = "fa-sack-dollar"
    }
    -- Add any other money types you want
}
```

### Prices Command

Enable a command to view current prices:

```lua
Config.PricesCommand = {
    enabled = false, -- Enable or disable the prices command
    name = "prices", -- Command name
    help = "View current pawnshop prices" -- Command help text
}
```

***

## Example Full Setup

Here's a complete example of setting up a pawnshop with ownership enabled:

```lua
-- First, enable ownership globally
Config.EnablePawnshopOwnership = true
Config.PawnshopOwnershipDuration = 8
Config.MaxPawnshopsPerPlayer = 1

-- Define product lists
Config.ProductLists = {
    ["electronics"] = {
        [1] = {
            productName = "phone",
            productLabel = "Phone",
            productPrice = 1500,
            moneyType = "money",
            productType = "both"
        },
        [2] = {
            productName = "laptop",
            productLabel = "Laptop",
            productPrice = 2500,
            moneyType = "money",
            productType = "both"
        }
    }
}

-- Configure the pawnshop
Config.Pawnshops = {
    [1] = {
        PawnshopName = "Vinewood Electronics Shop",
        ShopLocation = "Vinewood Blvd",
        Blip = {
            enable = true,
            blipSprite = 267,
            blipDisplay = 4,
            blipScale = 0.7,
            blipColour = 0,
            blipDisplayName = "Electronics Pawnshop"
        },
        Ped = {
            model = 's_m_y_shop_mask',
            location = vector4(412.66, 313.819, 103.016, 209.763),
            interactionRange = 2.0
        },
        ProductList = {"electronics"},
        Ownership = {
            ownable = true, -- Can be purchased
            price = 100000, -- Purchase price
            renewalPrice = 50000, -- Renewal price
            jobRestriction = nil, -- No job restriction
            owner = nil, -- Will be set when purchased
            requireShopFunds = true, -- Shop needs funds to buy items
            ownerCanEditPrices = true, -- Owner can edit prices
            storeItemsInStash = true, -- Items go to stash
            enableStaticBuying = false, -- Use stash for buying
            stash = {
                enabled = true,
                slots = 100,
                maxWeight = 500,
                location = vector3(414.66, 314.819, 103.016),
                label = "Vinewood Electronics Storage"
            },
            management = {
                enabled = true,
                location = vector3(415.26, 315.50, 103.02),
                label = "Vinewood Electronics Management"
            }
        }
    }
}
```
