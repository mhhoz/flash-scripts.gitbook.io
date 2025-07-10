# Pawnshop Configuration Guide

This comprehensive guide will walk you through the configuration options available in the Pawnshop resource, helping you customize the resource to fit your server's needs.

# Locale Configuration

### Config.Locale
-- Sets the language for the resource
-- Options: "en", "ar", "de", "es", "fr", "it", "pt", "ch"
-- Default: "en"
Config.Locale = "en"

# Debug Mode

### Config.Debug
-- Enables detailed console logging for troubleshooting
-- Options: true or false
-- Default: false
Config.Debug = false

# Framework Configuration

### Config.Framework
-- Specifies the framework used on your server
-- Options: "auto", "custom", "esx", "qb", "qbx"
-- Default: "auto"
Config.Framework = "auto"

### Config.esx.useOldExport
-- Compatibility setting for older ESX versions
-- Options: true or false
-- Default: false
Config.esx.useOldExport = false

# Inventory Configuration

### Config.Inventory
-- Specifies the inventory system used on your server
-- Options: "auto", "custom", "ox_inventory", "qs-inventory"
-- Default: "auto"
Config.Inventory = "auto"

### Config.ImgURL
-- Base URL for item images
-- Default Examples:
--   Ox Inventory: "nui://ox_inventory/web/images/"
--   QS Inventory: "nui://qs-inventory/html/images/"
--   QB Inventory: "nui://qb-inventory/html/images/"
Config.ImgURL = "nui://ox_inventory/web/images/"

# Buying Configuration

### Config.EnableBuying
-- Enables or disables item purchasing from pawnshops
-- Options: true or false
-- Default: false
Config.EnableBuying = false

### Config.BuyPriceMode
-- Determines how buying prices are calculated
-- Options: "same", "markup"
-- Default: "same"
Config.BuyPriceMode = "same"

### Config.BuyPriceMultiplier
-- Multiplier applied when buying items
-- Default: 1.5
Config.BuyPriceMultiplier = 1.5

### Config.BuyingAffectsPrices
-- Determines if buying items impacts market prices
-- Options: true or false
-- Default: false
Config.BuyingAffectsPrices = false

### Config.StoreItemsInStash
-- Controls whether sold items are stored in the pawnshop stash
-- Options: true or false
-- Default: false
-- Additional Effect: When true, buying is restricted to items in the stash
Config.StoreItemsInStash = false

# Pawnshop Ownership

### Config.EnablePawnshopOwnership
-- Allows pawnshops to be purchased and owned
-- Options: true or false
-- Default: false
Config.EnablePawnshopOwnership = false

### Config.PawnshopOwnershipDuration
-- Number of days before ownership expires
-- Default: 8
Config.PawnshopOwnershipDuration = 8

# Price Configuration

### Config.FluctuationIncrease
-- Percentage increase when demand is high
-- Default: 10
Config.FluctuationIncrease = 10

### Config.FluctuationDecrease
-- Percentage decrease when supply is high
-- Default: 10
Config.FluctuationDecrease = 10

### Config.PriceUpdateTime
-- Interval between automatic price updates
-- Unit: Minutes
-- Default: 25
Config.PriceUpdateTime = 25

### Config.SeparateShopPrices
-- Determines if item prices are independent for each shop
-- Options: true or false
-- Default: true
Config.SeparateShopPrices = true

### Config.AllowSellAnywhere
-- Controls where items can be sold
-- Options: true, false
-- Default: false
Config.AllowSellAnywhere = false

### Config.QualityMultiplier
-- Enables price adjustment based on item quality/durability
-- Options: true or false
-- Default: false
Config.QualityMultiplier = false

# Interaction Configuration

### Config.Target
-- Specifies the targeting system
-- Options: "ox", "qb", "TextUI"
-- Default: "TextUI"
Config.Target = "TextUI"

### Config.TargetSettings
-- Customizes interaction settings for different targeting systems
-- Includes label, icon, distance
-- Example:
Config.TargetSettings = {
    label = "Open Pawnshop",
    icon = "fa-solid fa-shop",
    distance = 2.5
}

# Item Restrictions

### Config.BlacklistedItems
-- List of items that cannot be sold
Config.BlacklistedItems = {
    "money",
    "cash",
    "black_money"
}

# Money Types

### Config.MoneyTypes
-- Defines different money types with labels and icons
Config.MoneyTypes = {
    money = {label = "Cash", icon = "💵"},
    black_money = {label = "Dirty Money", icon = "🧪"}
}

# Product Lists

### Config.ProductLists
-- Predefined lists of items that can be shared between shops
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

# Pawnshop Locations

### Config.Pawnshops
-- Defines individual pawnshop locations with detailed configurations
-- Includes shop name, location, blip, ped, products, ownership, stash
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

# Notes

-- Always test configurations in a development environment
-- Some settings may require additional framework or inventory system support
-- Restart your server after making configuration changes

# Customization Tips

-- Set Config.Debug = true when setting up to get detailed logs
-- Choose framework/inventory carefully to match your server setup
-- Adjust price fluctuations to match your in-game economy
-- Use shared product lists for consistent pricing

# Compatibility

-- Ensure framework, inventory, and dependencies are up to date and compatible with this resource
