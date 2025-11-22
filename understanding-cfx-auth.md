# FiveM asset escrow errors

The **FiveM asset escrow system** secures assets by encrypting critical files, ensuring that exclusive Quasar Store assets are protected against unauthorized use or modification. Below is a detailed guide to common errors and solutions, with titled sections for clarity.

## Failed to Verify Protected Resource <a href="#failed-to-verify-protected-resource" id="failed-to-verify-protected-resource"></a>

This error usually means the files were corrupted during transfer.



{% stepper %}
{% step %}
## Error <a href="#error" id="error"></a>

Failed to verify protected resource (flash-resourceName).
{% endstep %}

{% step %}
## Cause

Files were corrupted during transfer
{% endstep %}

{% step %}
## Solution

* Ensure all files, including `.fxap`, are uploaded correctly.
* Use [**WinSCP** ](https://winscp.net/eng/downloads.php)instead of FileZilla for transferring files, as FileZilla might skip encrypted components.
{% endstep %}
{% endstepper %}

***

### Missing Required Entitlement <a href="#missing-required-entitlement" id="missing-required-entitlement"></a>

This error occurs when your server license key is not linked to the account that purchased the asset.

{% stepper %}
{% step %}
## Error

You lack the required entitlement to use flash-resourceName.
{% endstep %}

{% step %}
## Cause

Server license key does not match the account that purchased the asset.
{% endstep %}

{% step %}
## Solution

* Verify that your **server license key in Keymaster** matches the one used during purchase.
* Restart your server after installation to apply any changes.
{% endstep %}
{% endstepper %}

***

## **S**yntax Errors <a href="#syntax-errors" id="syntax-errors"></a>

This error can be caused by several factors:

{% stepper %}
{% step %}
## Error

Syntax error \</1> or similar issues.
{% endstep %}

{% step %}
## Cause

Outdated artifacts or attempts to edit encrypted code.
{% endstep %}

{% step %}
## Solution

* Update to **artifact version 4960 or newer**.
* Avoid editing encrypted files, as this will damage the asset.
* Restart your server to resolve initialization issues.
{% endstep %}
{% endstepper %}

***

## **R**ecommendations

{% stepper %}
{% step %}
## Use the Latest Artifacts

Always run **artifact version 4960 or higher** to avoid compatibility problems.
{% endstep %}

{% step %}
## Use Reliable File Transfer Tools <a href="#use-reliable-file-transfer-tools" id="use-reliable-file-transfer-tools"></a>

Switch to [**WinSCP** ](https://winscp.net/eng/downloads.php)for file uploads to ensure `.fxap` files and other encrypted components aren't skipped.
{% endstep %}

{% step %}
## Avoid Editing Encrypted Code <a href="#avoid-editing-encrypted-code" id="avoid-editing-encrypted-code"></a>

Never attempt to modify encrypted files. If customizations are needed, refer to documentation or contact support.
{% endstep %}

{% step %}
## Restart Your Server Regularly <a href="#restart-your-server-regularly" id="restart-your-server-regularly"></a>

After installing or updating assets, restart your server to ensure all changes are applied and potential errors are resolved.


{% endstep %}
{% endstepper %}

