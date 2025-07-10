# Pawnshop Configuration Guide

> This comprehensive guide walks you through the configuration options in the Pawnshop resource, helping you tailor the resource to your server.

## Locale Configuration

- `Config.Locale`

Sets the language for the resource.

```lua
Config.Locale = "en"
```

**Options**: `"en"`, `"ar"`, `"de"`, `"es"`, `"fr"`, `"it"`, `"pt"`, `"ch"`
**Default**: `"en"`

## Debug Mode

- `Config.Debug`

Enables detailed logging for debugging.

```lua
Config.Debug = false
```

**Options**: `true`, `false`
**Default**: `false`

## Framework Configuration

- `Config.Framework`

Specifies the server framework.

```lua
Config.Framework = "auto"
```

**Options**: `"auto"`, `"custom"`, `"esx"`, `"qb"`, `"qbx"`
**Default**: `"auto"`

- `Config.esx.useOldExport`

For compatibility with older ESX versions.

```lua
Config.esx.useOldExport = false
```

**Options**: `true`, `false`
**Default**: `false`

## Inventory Configuration

- `Config.Inventory`

Specifies the inventory system used.

```lua
Config.Inventory = "auto"
```

**Options**: `"auto"`, `"custom"`, `"ox_inventory"`, `"qs-inventory"`
**Default**: `"auto"`

- `Config.ImgURL`

Base URL for item images.

```lua
Config.ImgURL = "nui://ox_inventory/web/images/"
```

**Examples**:

* Ox Inventory: `"nui://ox_inventory/web/images/"`
* QS Inventory: `"nui://qs-inventory/html/images/"`
* QB Inventory: `"nui://qb-inventory/html/images/"`

## Buying Configuration

- `Config.EnableBuying`

Enables item purchasing from pawnshops.

```lua
Config.EnableBuying = false
```

- `Config.BuyPriceMode`

Price calculation method for buying.

```lua
Config.BuyPriceMode = "same"
```

**Options**: `"same"`, `"markup"`
**Default**: `"same"`

- `Config.BuyPriceMultiplier`

Applied when `BuyPriceMode` is `markup`.

```lua
Config.BuyPriceMultiplier = 1.5
```

- `Config.BuyingAffectsPrices`

Influences market prices when buying items.

```lua
Config.BuyingAffectsPrices = false
```

- `Config.StoreItemsInStash`

Sold items go to stash (affects buying).

```lua
Config.StoreItemsInStash = false
```

## Pawnshop Ownership

- `Config.EnablePawnshopOwnership`

Allows pawnshop ownership by players.

```lua
Config.EnablePawnshopOwnership = false
```

- `Config.PawnshopOwnershipDuration`

Time (in days) before ownership expires.

```lua
Config.PawnshopOwnershipDuration = 8
```

## Price Configuration

- `Config.FluctuationIncrease`

Percent increase on high demand.

```lua
Config.FluctuationIncrease = 10
```

- `Config.FluctuationDecrease`

Percent decrease on high supply.

```lua
Config.FluctuationDecrease = 10
```

- `Config.PriceUpdateTime`

Time between price updates (in minutes).

```lua
Config.PriceUpdateTime = 25
```

- `Config.SeparateShopPrices`

If each shop has separate pricing.

```lua
Config.SeparateShopPrices = true
```

- `Config.AllowSellAnywhere`

Allows selling items anywhere.

```lua
Config.AllowSellAnywhere = false
```

- `Config.QualityMultiplier`

Adjust prices based on item quality.

```lua
Config.QualityMultiplier = false
```

## Interaction Configuration

- `Config.Target`

Targeting system used for interaction.

```lua
Config.Target = "TextUI"
```

**Options**: `"ox"`, `"qb"`, `"TextUI"`
**Default**: `"TextUI"`

- `Config.TargetSettings`

Customize target UI settings.

```lua
Config.TargetSettings = {
  label = "Open Pawnshop",
  icon = "fa-solid fa-shop",
  distance = 2.5
}
```

## Item Restrictions

- `Config.BlacklistedItems`

Disallowed items for selling.

```lua
Config.BlacklistedItems = {
  "money",
  "cash",
  "black_money"
}
```

## Money Types

- `Config.MoneyTypes`

Display labels and icons for money.

```lua
Config.MoneyTypes = {
  money = {label = "Cash", icon = "💵"},
  black_money = {label = "Dirty Money", icon = "🧪"}
}
```

## Product Lists

- `Config.ProductLists`

Shared item lists between pawnshops.

```lua
Config.ProductLists = {
  jewelry = {
    { name = "diamond_ring", price = 250 },
    { name = "gold_chain", price = 200 }
  },
  food = {
    { name = "burger", price = 15 },
    { name = "water", price = 10 }
  }
}
```

## Pawnshop Locations

- `Config.Pawnshops`

Detailed location and settings for each shop.

```lua
Config.Pawnshops = {
  ["downtown"] = {
    name = "Downtown Pawn",
    coords = vec3(-123.45, -456.78, 31.12),
    ped = { model = "s_m_y_dealer_01", heading = 180.0 },
    blip = { sprite = 617, color = 5, scale = 0.8, label = "Pawnshop" },
    productList = "jewelry",
    enableOwnership = true,
    useStash = true,
    allowManagement = true
  }
}
```

## Notes

> ⚠️ Always test in a development environment first.

* Some options require specific frameworks/inventory.
* Restart the server after making changes.

## Customization Tips

* Set `Debug = true` during setup.
* Use `shared product lists` to sync pricing.
* Match price settings with your economy.

## Compatibility

Ensure all frameworks and inventory dependencies are up to date and supported.
