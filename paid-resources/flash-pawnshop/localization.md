# Localization
# Localization Configuration

## Overview
Localization allows you to customize the language and translation settings for the Pawnshop resource.

## Configuration Options

### Locale Setting
```lua
Config.Locale = "en"
```

#### Supported Languages
- `"en"`: English
- `"ar"`: Arabic
- `"de"`: German
- `"es"`: Spanish
- `"fr"`: French
- `"it"`: Italian
- `"pt"`: Portuguese
- `"ch"`: Chinese

### How to Change Language
1. Set the `Config.Locale` to your desired language code
2. Ensure corresponding translation files exist in the `locales/` directory

### Troubleshooting
- If notifications remain in English, add `setr ox:locale [language_code]` to your `server.cfg`
- Verify that translation files are complete and up-to-date

## Adding New Translations
1. Create a new JSON file in the `locales/` directory
2. Translate all existing keys
3. Contribute back to the community!

## Example
```lua
-- Set language to German
Config.Locale = "de"
```

### Best Practices
- Always test translations thoroughly
- Coordinate with your community for accurate translations
- Keep translations consistent across all resource components 
