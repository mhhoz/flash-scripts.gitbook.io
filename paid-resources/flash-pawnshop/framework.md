# Framework Integration

## Overview
The Pawnshop resource supports multiple frameworks to ensure compatibility with different server setups.

## Configuration Options

### Framework Selection
```lua
Config.Framework = "auto"
```

#### Supported Frameworks
- `"auto"`: Automatically detect the framework
- `"custom"`: Use a custom framework implementation
- `"esx"`: ESX Framework
- `"qb"`: QB-Core Framework
- `"qbx"`: QBX Framework

### ESX-Specific Configuration
```lua
Config.esx = {
    useOldExport = false
}
```

#### ESX Export Options
- `useOldExport = false`: Use modern ESX export methods
- `useOldExport = true`: Use legacy ESX export methods for older versions

## Choosing the Right Framework

### Auto Detection
- Recommended for most setups
- Automatically identifies the framework in use
- Provides the most flexible configuration

### Manual Framework Selection
- Use when auto-detection fails
- Specify the exact framework you're using
- Ensures precise compatibility

## Example Configurations

```lua
-- Auto-detect framework
Config.Framework = "auto"

-- Manually set to ESX with legacy exports
Config.Framework = "esx"
Config.esx.useOldExport = true

-- Use custom framework
Config.Framework = "custom"
```

## Troubleshooting
- If experiencing framework-related issues, try:
  1. Manually specifying the framework
  2. Checking framework version compatibility
  3. Verifying resource load order

## Custom Framework Implementation
- Create custom framework files in the `frameworks/custom/` directory
- Implement required framework-specific functions
- Refer to existing framework implementations as a guide

### Best Practices
- Keep framework configurations up-to-date
- Test thoroughly with your specific framework version
- Report any compatibility issues to the resource developer 
