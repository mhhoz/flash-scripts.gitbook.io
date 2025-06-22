### Configuration File: `shared/config.lua`

#### 1. Locale Configuration
```lua
Config.Locale = "en"
```
- Sets the default language for the market.
- Ensure the corresponding locale JSON file exists in the `locales/` directory.
- Default is English (`en`).

---

#### 2. Debug Mode
```lua
Config.Debug = false
```
- Enables detailed console logging for troubleshooting.
- Set to `false` in production to reduce performance overhead.

---

#### 3. Framework Configuration
```lua
Config.Framework = "auto"
```
**Options:**
- `"auto"` - Automatically detect the framework.
- `"esx"` - Explicitly use ESX framework.
- `"qb"` - Explicitly use QBCore framework.
- `"qbx"` - Explicitly use QBX framework.

**ESX-specific Configuration:**
```lua
Config.esx = {
    useOldExport = false -- Set to true if using an older version of ESX
}
```

---

#### 4. Inventory Configuration
```lua
Config.Inventory = "auto"
```
**Options:**
- `"auto"` - Automatically detect inventory system.
- `"ox"` - Ox Inventory.
- `"qs"` - QS Inventory.

**Inventory Image Path:**
```lua
Config.InventoryImagePath = "nui://ox_inventory/web/images/"
```
- Ensure this matches your inventory system’s image path.

---

#### 5. Dealership Integration
```lua
Config.UseJGDealership = false
```
- Enable integration with JG Dealership for financed vehicles.

---

#### 6. Vehicle Images
```lua
Config.Images = {
    BaseURL = "https://r2.fivemanage.com",
    Token = "BmrEYpTbKc06q3WsdNPd3"
}
```
- Configure base URL and token for vehicle images.
- Image names should be lowercase (e.g., `youga.png`).

---

#### 7. Target Interaction System
```lua
Config.Target = "TextUI"
```
**Options:**
- `"ox"` - Ox Target.
- `"qb"` - QB Target.
- `"TextUI"` - Default text-based interaction.

---

#### 8. Markets Configuration
```lua
Config.Markets[1] = {
    MarketName = "General Marketplace",
    MarketSettings = {
        IsSeperated = false,
        SpecificJob = false,
        JobName = nil,
        EnableVehicleMarket = true,
        EnableItemsMarket = true,
        BlacklistedItems = { "money", "cash", "black_money" },
        BlacklistedVehicles = { "ADDER" }
    }
}
```
- Multiple markets can be configured.
- Allows job-specific market access.
- Blacklist specific items and vehicles.

---

#### 9. Vehicle Classes
```lua
Config.VehicleClasses = {
    [0] = "Compacts",
    [1] = "Sedans",
    -- ... more classes
}
```
- Predefined vehicle class names for categorization.

---

#### 10. Currencies
```lua
Config.Currencies = {
    {
        name = "Cash",
        id = "money",
        item = "money",
        icon = "fa-solid fa-dollar-sign"
    }
    -- Add more currencies
}
```
- Define available currencies for transactions.

---

#### 11. Webhooks Configuration
```lua
Config.EnableWebhooks = false
Config.Webhooks = {
    ['ItemListed'] = {
        Enabled = false,
        URL = '',
        Color = 0x3498DB
    }
    -- More webhook configurations
}
```
- Enable and configure webhook events for logging or automation.

