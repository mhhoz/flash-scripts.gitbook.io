# Pawnshop Configuration Guide

This comprehensive guide will walk you through the configuration options available in the Pawnshop resource, helping you customize the resource to fit your server's needs.

## 🌐 Locale Configuration

### `Config.Locale`
- **Description**: Sets the language for the resource
- **Options**: "en", "ar", "de", "es", "fr", "it", "pt", "ch"
- **Default**: "en"
- **Usage**: Determines the language used for translations and notifications

## 🐞 Debug Mode

### `Config.Debug`
- **Description**: Enables detailed console logging for troubleshooting
- **Options**: `true` or `false`
- **Default**: `false`
- **Usage**: When set to `true`, prints additional information to help diagnose issues

## 🔧 Framework Configuration

### `Config.Framework`
- **Description**: Specifies the framework used on your server
- **Options**: 
  - `"auto"`: Automatically detect the framework
  - `"custom"`: Use a custom framework implementation
  - `"esx"`: ESX Framework
  - `"qb"`: QB Framework
  - `"qbx"`: QBX Framework
- **Default**: `"auto"`

### `Config.esx.useOldExport`
- **Description**: Compatibility setting for older ESX versions
- **Options**: `true` or `false`
- **Default**: `false`
- **Usage**: Set to `true` if using an older version of ESX that requires different export methods

## 📦 Inventory Configuration

### `Config.Inventory`
- **Description**: Specifies the inventory system used on your server
- **Options**:
  - `"auto"`: Automatically detect the inventory system
  - `"custom"`: Use a custom inventory implementation
  - `"ox_inventory"`: Ox Inventory
  - `"qs-inventory"`: QS Inventory
- **Default**: `"auto"`

### `Config.ImgURL`
- **Description**: Base URL for item images
- **Default Examples**:
  - Ox Inventory: `"nui://ox_inventory/web/images/"`
  - QS Inventory: `"nui://qs-inventory/html/images/"`
  - QB Inventory: `"nui://qb-inventory/html/images/"`
- **Usage**: Provides the base path for item images in the inventory

## 💰 Buying Configuration

### `Config.EnableBuying`
- **Description**: Enables or disables item purchasing from pawnshops
- **Options**: `true` or `false`
- **Default**: `false`

### `Config.BuyPriceMode`
- **Description**: Determines how buying prices are calculated
- **Options**:
  - `"same"`: No price markup
  - `"markup"`: Apply a price multiplier
- **Default**: `"same"`

### `Config.BuyPriceMultiplier`
- **Description**: Multiplier applied when buying items
- **Default**: `1.5`
- **Usage**: Increases the price when buying items from the pawnshop

### `Config.BuyingAffectsPrices`
- **Description**: Determines if buying items impacts market prices
- **Options**: `true` or `false`
- **Default**: `false`

### `Config.StoreItemsInStash`
- **Description**: Controls whether sold items are stored in the pawnshop stash
- **Options**: `true` or `false`
- **Default**: `false`
- **Additional Effect**: When `true`, buying is restricted to items in the stash

## 🏪 Pawnshop Ownership

### `Config.EnablePawnshopOwnership`
- **Description**: Allows pawnshops to be purchased and owned
- **Options**: `true` or `false`
- **Default**: `false`

### `Config.PawnshopOwnershipDuration`
- **Description**: Number of days before ownership expires
- **Default**: `8`
- **Usage**: Determines how long a pawnshop remains owned before requiring renewal

## 💹 Price Configuration

### `Config.FluctuationIncrease`
- **Description**: Percentage increase when demand is high
- **Default**: `10`
- **Usage**: Controls price increases based on market demand

### `Config.FluctuationDecrease`
- **Description**: Percentage decrease when supply is high
- **Default**: `10`
- **Usage**: Controls price decreases based on market supply

### `Config.PriceUpdateTime`
- **Description**: Interval between automatic price updates
- **Default**: `25`
- **Unit**: Minutes
- **Recommendation**: Between 25 and higher values

### `Config.SeparateShopPrices`
- **Description**: Determines if item prices are independent for each shop
- **Options**: `true` or `false`
- **Default**: `true`

### `Config.AllowSellAnywhere`
- **Description**: Controls where items can be sold
- **Options**:
  - `true`: Items can be sold at any pawnshop
  - `false`: Items can only be sold at shops that list them
- **Default**: `false`

### `Config.QualityMultiplier`
- **Description**: Enables price adjustment based on item quality/durability
- **Options**: `true` or `false`
- **Default**: `false`

## 🎮 Interaction Configuration

### `Config.Target`
- **Description**: Specifies the targeting system
- **Options**: `"ox"`, `"qb"`, `"TextUI"`
- **Default**: `"TextUI"`

### `Config.TargetSettings`
- **Description**: Customizes interaction settings for different targeting systems
- **Includes**:
  - Label text
  - Interaction icon
  - Interaction distance

## 🚫 Item Restrictions

### `Config.BlacklistedItems`
- **Description**: List of items that cannot be sold
- **Default**:
  ```lua
  {
      'money',
      'cash',
      'black_money'
  }
  ```

## 💵 Money Types

### `Config.MoneyTypes`
- **Description**: Defines different money types with labels and icons
- **Default Includes**:
  - `money`: Cash
  - `black_money`: Dirty Money

## 📋 Product Lists

### `Config.ProductLists`
- **Description**: Predefined lists of items that can be shared between shops
- **Example Categories**:
  - `"jewelry"`: Rings, necklaces, etc.
  - `"food"`: Consumable items

## 🏬 Pawnshop Locations

### `Config.Pawnshops`
- **Description**: Defines individual pawnshop locations with detailed configurations
- **Configuration Includes**:
  - Shop name and location
  - Blip settings
  - Ped configuration
  - Product lists
  - Ownership options
  - Stash and management settings

## 📝 Notes

- Always test configurations in a development environment first
- Some settings may require additional framework or inventory system support
- Restart your server after making configuration changes

## 🛠 Customization Tips

1. Use `Config.Debug = true` when setting up to get more detailed logs
2. Carefully choose compatible framework and inventory system settings
3. Customize product lists to match your server's economy
4. Adjust price fluctuations to balance in-game economy

## ⚠️ Compatibility

Ensure your chosen framework, inventory system, and other dependencies are up to date and compatible with this resource.
