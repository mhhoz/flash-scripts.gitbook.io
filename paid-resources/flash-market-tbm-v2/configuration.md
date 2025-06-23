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
Config.Markets = {
    [1] = {
        MarketName = "General Marketplace", -- Displayed name of the market in the UI
        MarketSettings = { -- Comprehensive market-specific configuration
            IsSeperated = false, -- If true, this market is isolated from other markets
            SpecificJob = false, -- Enable job-restricted access to this market
            JobName = nil, -- Specific job(s) required to access this market
            -- Job Configuration Examples:
            -- Single job: JobName = "police"
            -- Multiple jobs: JobName = {"police", "ambulance"}
            -- Job with minimum grade: JobName = {
            --     {name = "police", grade = 2},  -- Police with grade 2 or higher
            --     {name = "ambulance", grade = {1, 3}}  -- Ambulance with grade between 1 and 3
            -- }
            EnableVehicleMarket = true, -- Allow vehicle listings in this market
            EnableItemsMarket = true, -- Allow item listings in this market
            BlacklistedItems = { -- Items that cannot be listed in this market
                "money",
                "cash", 
                "black_money",
                "weapon_smg"
            },
            BlacklistedVehicles = { -- Vehicles that cannot be listed in this market
                "ADDER",
                -- Add more vehicle models to restrict
            },
            ItemCurrencies = { -- Custom currency mappings for specific items
                ["WEAPON_PISTOL"] = "money", -- Pistols can only be sold for money
                ["WEAPON_SMG"] = "money"     -- SMGs can only be sold for money
            }
        },
        CommandSettings = {        -- Market-specific command configuration
            Enabled = true,        -- Enable/disable market command
            Command = 'market',    -- Command to open this specific market
            Description = 'Open the Market menu' -- Command description
        },
        PedLocations = { -- NPC interaction points for the market
            {
                Enabled = true,                    -- Enable/disable this NPC location
                Model = "a_m_m_business_01",       -- NPC model
                PedCorrds = vector4(354.567047, -944.386841, 29.431519, 181.4173), -- NPC spawn coordinates (x, y, z, heading)
                Scenario = "WORLD_HUMAN_AA_SMOKE", -- NPC scenario/animation
                TargetOption = {
                    label = "Open General Marketplace", -- Interaction label
                    icon = "fa-solid fa-store",    -- Font Awesome icon
                    coords = vector3(354.567047, -944.386841, 29.431519), -- Interaction coordinates
                    size = vector3(2.0, 2.0, 2.0), -- Interaction zone size
                    rotation = 45.0,              -- Interaction zone rotation
                    debug = false                 -- Enable debug visualization
                }
            },
            {
                Enabled = false,
                Model = "a_m_m_business_01",
                PedCorrds = vector4(356.663727, -944.518677, 29.431519, 178.5826),
                Scenario = "WORLD_HUMAN_AA_SMOKE",
                TargetOption = {
                    label = "Open General Marketplace",
                    icon = "fa-solid fa-store",
                    coords = vector3(356.663727, -944.518677, 29.431519),
                    size = vector3(2.0, 2.0, 2.0),
                    rotation = 45.0,
                    debug = false,
                }
            },
            -- Add more ped locations as needed
        },
        BlipSettings = {       -- Map Blip Settings
            Enabled = true,    -- Enable/disable blip
            sprite = 605,      -- Blip icon
            color = 2,         -- Blip color
            scale = 0.7,       -- Blip size 
            display = 4,       -- Display mode
            shortRange = true,
            name = "General Marketplace"
        }
    },
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

