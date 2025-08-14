# How to Setup

This comprehensive guide walks you through the configuration options in the Pawnshop resource, helping you tailor the resource to your server.

---

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
            location = vector4(182.584625, -1319.7626, 29.313599, 240.94488),
            interactionRange = 2.0
        },

        -- Product lists to be sold at this pawnshop
        ProductList = {"jewelry", "food"},

        -- Ownership and management options
        Ownership = {
            ownable = false,
            price = 75000,
            jobRestriction = nil,
            owner = nil,

            -- Stash (storage) configuration
            stash = {
                enabled = false,
                slots = 50,
                maxWeight = 200,
                location = vector3(181.2731628418, -1323.1893310547, 29.315742492676),
                label = "Downtown Pawnshop Storage"
            },

            -- Management location
            management = {
                enabled = false,
                location = vector3(181.84, -1321.45, 29.32),
                label = "Downtown Pawnshop Management"
            }
        }
    }
    -- You can add more pawnshops here
}
```

---

## Managing Product Lists

### Creating Product Lists

Product lists are defined in `Config.ProductLists`. Here's how to create and use them:

```lua
Config.ProductLists = {
    ["jewelry"] = {
        [1] = {
            productName = "diamond_ring",
            productLabel = "Diamond Ring",
            productPrice = "500",
            moneyType = "money"
        },
        [2] = {
            productName = "diamond_necklace",
            productLabel = "Diamond Necklace",
            productPrice = "1000",
            moneyType = "money"
        }
    },

    ["electronics"] = {
        [1] = {
            productName = "phone",
            productLabel = "Phone",
            productPrice = "1500",
            moneyType = "money"
        },
        [2] = {
            productName = "laptop",
            productLabel = "Laptop",
            productPrice = "2500",
            moneyType = "money"
        }
    }
}
```

### Assigning Product Lists to Pawnshops

In the pawnshop configuration, use the product list names:

```lua
ProductList = {"jewelry", "electronics"}
```

---

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

---

## Pricing and Economy

### Price Fluctuation

Configure how prices change:

```lua
Config.FluctuationIncrease = 10
Config.FluctuationDecrease = 10
Config.PriceUpdateTime = 25
Config.SeparateShopPrices = true
```

---

## Interaction Settings

Configure how players interact with pawnshops:

```lua
Config.Target = "TextUI"

Config.TargetSettings = {
    TextUI = {
        label = "[E] Open Pawnshop"
    },
    ox = {
        icon = "fas fa-store",
        label = "Open Pawnshop",
        distance = 2.0
    }
}
```

---

## Advanced Configuration

### Ownership and Management

Enable pawnshop ownership:

```lua
Config.EnablePawnshopOwnership = true
Config.PawnshopOwnershipDuration = 8
```

---

## Best Practices

1. Start with a small number of pawnshops
2. Balance prices carefully
3. Test thoroughly in a development environment
4. Use `Config.Debug = true` when setting up

---

## Troubleshooting

* Ensure all item names match your inventory system
* Check that frameworks and inventory systems are compatible
* Verify coordinates are correct
* Restart the resource after configuration changes

---

## Example Full Setup

Here's a complete example of setting up a pawnshop:

```lua
Config.Pawnshops = {
    [1] = {
        PawnshopName = "Vinewood Electronics Shop",
        ShopLocation = "Vinewood Blvd",
        Blip = {
            enable = true,
            blipSprite = 267,
            blipDisplayName = "Electronics Pawnshop"
        },
        Ped = {
            model = 's_m_y_shop_mask',
            location = vector4(412.66, 313.819, 103.016, 209.763),
            interactionRange = 2.0
        },
        ProductList = {"electronics"},
        Ownership = {
            ownable = true,
            price = 100000,
            stash = {
                enabled = true,
                slots = 100,
                maxWeight = 500
            }
        }
    }
}
```
