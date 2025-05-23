# Installation

### Installation Guide

{% stepper %}
{% step %}
Go to CFX Keymaster, navigate to "Granted Assets", and find "Flash TBM" in your purchased assets
{% endstep %}

{% step %}
Click the "Download" button, extract the ZIP file, then move the extracted `flash-market` folder into your server's `resources` folder
{% endstep %}

{% step %}
Import the appropriate SQL file based on your framework

* For ESX: `installation/ESX.sql`
* For QB-Core: `installation/QB.sql`
* For QBX: `installation/QBX.sql`
{% endstep %}

{% step %}
Ensure you have the following resources installed:

```lua
ensure oxmysql
ensure ox_lib
```
{% endstep %}

{% step %}
Go to `flash-market/shared/config.lua` and configure the settings, market locations, currencies, and webhooks as needed for your server.
{% endstep %}
{% endstepper %}

## If you encounter any issues:

* Check the server console for error messages
* Verify all dependencies are running
* Ensure the database tables were created correctly
* Check the config file for any misconfigurations
* Contact flash support if issues persist
