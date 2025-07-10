# Inventory System Configuration

## Overview
The Pawnshop resource supports multiple inventory systems to provide flexibility for different server setups.

## Configuration Options

### Inventory Selection
```lua
Config.Inventory = "auto"
```

#### Supported Inventory Systems
- `"auto"`: Automatically detect the inventory system
- `"custom"`: Use a custom inventory implementation
- `"ox_inventory"`: Ox Inventory
- `"qs-inventory"`: QS Inventory

### Image URL Configuration
```lua
Config.ImgURL = "nui://ox_inventory/web/images/"
```

#### Inventory-Specific Image URLs
- Ox Inventory: `"nui://ox_inventory/web/images/"`
- QS Inventory: `"nui://qs-inventory/html/images/"`
- QB Inventory: `"nui://qb-inventory/html/images/"`

## Choosing the Right Inventory System

### Auto Detection
- Recommended for most setups
- Automatically identifies the inventory system in use
- Provides the most flexible configuration

### Manual Inventory Selection
- Use when auto-detection fails
- Specify the exact inventory system you're using
- Ensures precise compatibility

## Example Configurations

```lua
-- Auto-detect inventory system
Config.Inventory = "auto"

-- Manually set to Ox Inventory
Config.Inventory = "ox_inventory"
Config.ImgURL = "nui://ox_inventory/web/images/"

-- Use custom inventory
Config.Inventory = "custom"
```

## Troubleshooting
- If experiencing inventory-related issues, try:
  1. Manually specifying the inventory system
  2. Checking inventory version compatibility
  3. Verifying image URL configuration

## Custom Inventory Implementation
- Create custom inventory files in the `inventories/custom/` directory
- Implement required inventory-specific functions
- Refer to existing inventory implementations as a guide

### Custom Inventory Requirements
1. Implement server-side inventory functions
2. Create corresponding client-side inventory functions
3. Match the expected interface for item management

## Best Practices
- Keep inventory configurations up-to-date
- Test thoroughly with your specific inventory version
- Ensure image URLs are correctly configured
- Report any compatibility issues to the resource developer

### Image URL Troubleshooting
- Verify the correct path for your inventory system
- Check that image files exist in the specified directory
- Ensure the URL follows the `nui://` protocol format 
