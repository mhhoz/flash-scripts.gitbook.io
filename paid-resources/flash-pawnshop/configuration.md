# Pawnshop Configuration Guide

This comprehensive guide walks you through the configuration options in the Pawnshop resource, helping you tailor the resource to your server.

---

## Locale Configuration
Sets the language for the resource.

```lua
Config.Locale = "en"
```

**Options**: `"en"`, `"ar"`, `"de"`, `"es"`, `"fr"`, `"it"`, `"pt"`, `"ch"`
**Default**: `"en"`

---

## Debug Mode
Enables detailed logging for debugging.

```lua
Config.Debug = false
```

**Options**: `true`, `false`
**Default**: `false`

---

## Framework Configuration
Specifies the server framework.

```lua
Config.Framework = "auto"
```

**Options**: `"auto"`, `"custom"`, `"esx"`, `"qb"`, `"qbx"`
**Default**: `"auto"`

For compatibility with older ESX versions.

```lua
Config.esx.useOldExport = false
```

**Options**: `true`, `false`
**Default**: `false`

---

## Inventory Configuration
Specifies the inventory system used.

```lua
Config.Inventory = "auto"
```

**Options**: `"auto"`, `"custom"`, `"ox_inventory"`, `"qs-inventory"`
**Default**: `"auto"`

Base URL for item images.

```lua
Config.ImgURL = "nui://ox_inventory/web/images/"
```

**Examples**:

* Ox Inventory: `"nui://ox_inventory/web/images/"`
* QS Inventory: `"nui://qs-inventory/html/images/"`
* QB Inventory: `"nui://qb-inventory/html/images/"`

---

## Buying Configuration
Enables item purchasing from pawnshops.

```lua
Config.EnableBuying = false
```

Price calculation method for buying.

```lua
Config.BuyPriceMode = "same"
```

**Options**: `"same"`, `"markup"`
**Default**: `"same"`

Applied when `BuyPriceMode` is `markup`.

```lua
Config.BuyPriceMultiplier = 1.5
```

Influences market prices when buying items.

```lua
Config.BuyingAffectsPrices = false
```

Sold items go to stash (affects buying).

```lua
Config.StoreItemsInStash = false
```

**Note**: When `true`, buying is limited to items available in the stash.

---

## Pawnshop Ownership
Allows pawnshop ownership by players.

```lua
Config.EnablePawnshopOwnership = false
```

Time (in days) before ownership expires.

```lua
Config.PawnshopOwnershipDuration = 8
```

---

## Price Configuration
Percent increase on high demand.

```lua
Config.FluctuationIncrease = 10
```

Percent decrease on high supply.

```lua
Config.FluctuationDecrease = 10
```

Time between price updates (in minutes).

```lua
Config.PriceUpdateTime = 25
```

If each shop has separate pricing.

```lua
Config.SeparateShopPrices = true
```

Allows selling items anywhere.

```lua
Config.AllowSellAnywhere = false
```

Adjust prices based on item quality.

```lua
Config.QualityMultiplier = false
```

---

## Interaction Configuration
Targeting system used for interaction.

```lua
Config.Target = "TextUI"
```

**Options**: `"ox"`, `"qb"`, `"TextUI"`

Customize target UI settings.

```lua
Config.TargetSettings = {
  label = "Open Pawnshop",
  icon = "fa-solid fa-shop",
  distance = 2.5
}
```

---

## Item Restrictions
Disallowed items for selling.

```lua
Config.BlacklistedItems = {
  "money",
  "cash",
  "black_money"
}
```

---

## Money Types
Display labels and icons for money.

```lua
Config.MoneyTypes = {
  money = {label = "Cash", icon = "💵"},
  black_money = {label = "Dirty Money", icon = "🧪"}
}
```

---

## Product Lists
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

---

## Pawnshop Locations
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

---

## Notes

> ⚠️ **Always test changes in a development environment**.

* Some options require specific frameworks or inventories.
* Restart your server after making configuration changes.

---

## Customization Tips

* Set `Debug = true` during setup for detailed logs.
* Use `shared product lists` to sync pricing across locations.
* Match price settings with your in-game economy.

---

## Compatibility

Ensure all frameworks, inventories, and dependencies are **up to date and supported** by the resource.
