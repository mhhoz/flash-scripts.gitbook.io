# Configuration

This comprehensive guide walks you through the configuration options in the Pawnshop resource, helping you tailor the resource to your server.

***

## Debug Mode

Enable detailed console logging for troubleshooting and development. Set to false in production to reduce performance overhead.

```lua
Config.Debug = false
```

**Options**: `true`, `false` **Default**: `false`

***

## Locale Configuration

Choose the default language for the market. Ensure corresponding locale JSON file exists in the locales/ directory.

```lua
Config.Locale = "en"
```

**Options**: `"en"`, `"ar"`, `"de"`, `"es"`, `"fr"`, `"it"`, `"pt"`, `"ch"`, `"sv"`, `"tk"` **Default**: `"en"`

***

## Framework Configuration

Automatic framework detection or manual selection.

```lua
Config.Framework = "auto"
```

**Options**: 
* `"auto"` - Automatically detect the framework
* `"esx"` - Explicitly use ESX framework
* `"qb"` - Explicitly use QBCore framework
* `"qbx"` - Explicitly use QBX framework

**Default**: `"auto"`

### ESX-Specific Configuration

For compatibility with older ESX versions.

```lua
Config.esx = {
    useOldExport = false
}
```

**Options**: `true`, `false` **Default**: `false`

***

## Inventory Configuration

Select inventory system or use automatic detection.

```lua
Config.Inventory = "auto"
```

**Options**:
* `"auto"` - Automatically detect inventory system
* `"ox"` - Ox Inventory
* `"qs"` - QS Inventory

**Default**: `"auto"`

### Image URL Configuration

Base URL for item images.

```lua
Config.ImgURL = "nui://ox_inventory/web/images/"
```

**Examples**:

* Ox Inventory: `"nui://ox_inventory/web/images/"`
* QS Inventory: `"nui://qs-inventory/html/images/"`
* QB Inventory: `"nui://qb-inventory/html/images/"`

***

## Notification Configuration

Choose one of the supported notification systems.

```lua
Config.Notification = 'ox'
```

**Supported Systems**:
* `'ox'` - OX Lib Notify
* `'mythic'` - Mythic Notify
* `'codem'` - Codem Notification
* `'okok'` - okokNotify
* `'17mov'` - 17mov_Hud
* `'qb'` - QBCore Notify
* `'esx'` - ESX Notification

**Default**: `'ox'`

***

## Target Interaction System

Choose the interaction method for market NPCs.

```lua
Config.Target = "TextUI"
```

**Options**:
* `"ox"` - Ox Target
* `"qb"` - QB Target
* `"TextUI"` - Default text-based interaction

**Default**: `"TextUI"`

### Target Settings Configuration

Customize target UI settings for different systems.

```lua
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

***

## Buying/Selling Configuration

### Enable Buying

Enable or disable item purchasing from pawnshops.

```lua
Config.EnableBuying = false
```

**Options**: `true`, `false` **Default**: `false`

### Buy Price Mode

Price calculation method for buying.

```lua
Config.BuyPriceMode = "same"
```

**Options**: 
* `"same"` - No markup, same as sell price
* `"markup"` - Use multiplier for markup

**Default**: `"same"`

### Buy Price Multiplier

Applied when `BuyPriceMode` is set to `"markup"`.

```lua
Config.BuyPriceMultiplier = 1.5
```

### Buying Affects Prices

Influences market prices when buying items.

```lua
Config.BuyingAffectsPrices = false
```

**Options**: `true`, `false` **Default**: `false`

***

## Pawnshop Ownership Configuration

### Enable Ownership

Allows pawnshop ownership by players.

```lua
Config.EnablePawnshopOwnership = false
```

**Options**: `true`, `false` **Default**: `false`

### Ownership Duration

Time (in days) before ownership expires.

```lua
Config.PawnshopOwnershipDuration = 8
```

### Maximum Pawnshops Per Player

Maximum number of pawnshops a player can own.

```lua
Config.MaxPawnshopsPerPlayer = 1
```

**Note**: Set to `0` or `nil` for unlimited.

### Prevent Owner Selling

Enable selling restrictions for both owners and employees.

```lua
Config.PreventOwnerSelling = true
```

**Options**: `true`, `false` **Default**: `true`

***

## Price Configuration

### Basic Price Fluctuation

Percent increase on high demand.

```lua
Config.FluctuationIncrease = 15
```

Percent decrease on high supply.

```lua
Config.FluctuationDecrease = 12
```

### Price Update Time

Time between price updates (in minutes).

```lua
Config.PriceUpdateTime = 1
```

### Advanced Price Fluctuation Settings

Fine-tune the price fluctuation system.

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

**See how the price system works**: [Pricing System Documentation](https://flash-scripts.gitbook.io/documentation/paid-resources/flash-pawnshop/how-to-setup/pricing-system)

### Separate Shop Prices

If each shop has separate pricing.

```lua
Config.SeparateShopPrices = true
```

**Options**: `true`, `false` **Default**: `true`

### Allow Sell Anywhere

Allows selling items at any pawnshop.

```lua
Config.AllowSellAnywhere = false
```

**Options**: `true`, `false` **Default**: `false`

### Quality Multiplier

Adjust prices based on item quality.

```lua
Config.QualityMultiplier = false
```

**Options**: `true`, `false` **Default**: `false`

**Note**: Set to `false` if you don't want quality to affect price.

***

## Command Configuration

### Prices Command

Enable or disable the prices command.

```lua
Config.PricesCommand = {
    enabled = false, -- Enable or disable the prices command
    name = "prices", -- Command name
    help = "View current pawnshop prices" -- Command help text
}
```

***

## Money and Item Configuration

### Blacklisted Items

Disallowed items for selling.

```lua
Config.BlacklistedItems = {
    'money',
    'cash',
    'black_money',
}
```

### Money Types

Display labels and icons for money types.

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

***

## Product Lists

Shared item lists between pawnshops. These lists define which items can be bought/sold and their base prices.

```lua
Config.ProductLists = {
    ["jewelry"] = { -- List name/identifier - name it anything you want
        [1] = {
            productName = "diamond_ring", -- Item name
            productLabel = "Diamond Ring", -- Item label
            productPrice = 500, -- Item base price
            moneyType = "money", -- Money type
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
            productType = "sell" -- Only sellable
        },
        [4] = {
            productName = "radio",
            productLabel = "Radio",
            productPrice = 2000,
            moneyType = "black_money",
            productType = "buy" -- Only buyable
        }
    },
    ["food"] = {
        [1] = {
            productName = "burger",
            productLabel = "Burger",
            productPrice = 500,
            moneyType = "money",
            productType = "both"
        },
        [2] = {
            productName = "water",
            productLabel = "Water",
            productPrice = 1000,
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

***

## Pawnshop Locations

Detailed location and settings for each shop.

```lua
Config.Pawnshops = {
    [1] = {
        PawnshopName = "Downtown Pawnshop", -- Pawnshop Name
        ShopLocation = "Innocence Blvd", -- Shop Location
        Blip = {
            enable = true, -- Enable blip
            blipSprite = 267, -- Blip sprite
            blipDisplay = 4, -- Blip display
            blipScale = 0.7, -- Blip scale
            blipColour = 0, -- Blip colour
            blipDisplayName = "Downtown Pawnshop" -- Blip display name
        },
        Ped = {
            model = 's_m_o_busker_01', -- Ped model
            location = vector4(182.584625, -1319.7626, 29.313599, 240.94488), -- Ped location (x, y, z, heading)
            interactionRange = 2.0, -- Interaction range
        },
        ProductList = {"jewelry", "food"}, -- Can use multiple product lists or a single product list
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
            stash = {
                enabled = true, -- Enable stash for this pawnshop
                slots = 100, -- Number of slots in the stash
                maxWeight = 200, -- Max weight the stash can hold
                location = vector3(181.2731628418,-1323.1893310547,29.315742492676), -- Location of the stash
                label = "Downtown Pawnshop Storage" -- Label for the stash
            },
            management = {
                enabled = true, -- Enable management for this pawnshop
                location = vector3(181.84,-1321.45,29.32), -- Location of the management access
                label = "Downtown Pawnshop Management" -- Label for the management
            }
        },
    },
    [2] = {
        PawnshopName = "Vinewood Pawnshop",
        ShopLocation = "Vinewood Blvd",
        Blip = {
            enable = true,
            blipSprite = 267,
            blipDisplay = 4,
            blipScale = 0.7,
            blipColour = 0,
            blipDisplayName = "Vinewood Pawnshop"
        },
        Ped = {
            model = 's_m_o_busker_01',
            location = vector4(412.66, 313.819, 103.016, 209.763),
            interactionRange = 2.0,
        },
        ProductList = {"jewelry", "food"},
        Ownership = {
            ownable = false,
            price = 125000,
            renewalPrice = 62500,
            jobRestriction = nil,
            owner = nil,
            requireShopFunds = false,
            ownerCanEditPrices = false,
            storeItemsInStash = false,
            enableStaticBuying = false,
            stash = {
                enabled = false,
                slots = 100,
                maxWeight = 200,
                location = vector3(414.66, 314.819, 103.016),
                label = "Vinewood Pawnshop Storage"
            },
            management = {
                enabled = false,
                location = vector3(415.26, 315.50, 103.02),
                label = "Vinewood Pawnshop Management"
            }
        }
    }
}
```

**Key Settings Explained**:

* **ProductList**: Can be a single string `"jewelry"` or an array `{"jewelry", "food"}` to use multiple product lists
* **ownable**: Must be `true` for ownership features to work (also requires `Config.EnablePawnshopOwnership = true`)
* **storeItemsInStash**: When `true`, sold items go to the stash and buying is limited to stash contents
* **enableStaticBuying**: When `true`, shows products from ProductList with unlimited stock (ignores stash)
* **requireShopFunds**: When `true`, shop must have funds to purchase items from players
* **ownerCanEditPrices**: When `true`, shop owners can edit prices from the Management interface

***

## Compatibility

Ensure all frameworks, inventories, and dependencies are **up to date and supported** by the resource.
