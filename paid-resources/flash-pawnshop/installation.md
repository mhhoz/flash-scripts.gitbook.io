# Installation

### Installation Guide

{% stepper %}
{% step %}
Go to CFX Keymaster, navigate to "Granted Assets", and find "Flash Pawnshop" in your purchased assets
{% endstep %}

{% step %}
Click the "Download" button, extract the ZIP file, then move the extracted `flash-pawnshop` folder into your server's `resources` folder
{% endstep %}

{% step %}
Import the appropriate SQL file `install.sql`
{% endstep %}

{% step %}
Ensure you have the following resources installed:

```lua
ensure oxmysql
ensure ox_lib
```
{% endstep %}

{% step %}
Go to `flash-pawnshop/shared/config.lua` and configure the settings, pawnshop locations, currencies, and products list as needed for your server.
{% endstep %}
{% endstepper %}

## If you encounter any issues:

* Check the server console for error messages
* Verify all dependencies are running
* Ensure the database tables were created correctly
* Check the config file for any misconfigurations
* Contact flash support if issues persist
