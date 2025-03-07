---
icon: sliders-up
---

# plugin.json

{% hint style="danger" %}
This version of Bit has reached End of Life, this means it'll no longer receive ANY updates.

By continuing to use this version, you take full responsibility for any security issues that may be present.
{% endhint %}

All the plugin.json options for a Bit Plugin and what they're used for

<table data-full-width="true"><thead><tr><th>Option</th><th>Description</th><th>Accepted Values</th><th>Default Value</th></tr></thead><tbody><tr><td>name</td><td>The plugins name</td><td>string</td><td>Bit Core</td></tr><tr><td>developer</td><td>The plugins developer</td><td>string</td><td>Lockyz Media</td></tr><tr><td>version</td><td>What version the plugin is</td><td>string</td><td>5.2.3</td></tr><tr><td>support</td><td>A place to go to get support</td><td>string</td><td><a href="https://github.com/Lockyz-Media/bit/issues">https://github.com/Lockyz-Media/bit/issues</a></td></tr><tr><td>updateURL</td><td>A url pointing to a json file used for the update notification system</td><td>string/url</td><td><a href="https://cdn.lockyzmedia.com/discord/bots/bit/plugins/core/update.json">https://cdn.lockyzmedia.com/discord/bots/bit/plugins/core/update.json</a></td></tr><tr><td>events</td><td>Whether the plugin has events or not</td><td>string(true or false)</td><td>false</td></tr><tr><td>commands</td><td>whether the plugin has slash commands or not</td><td>string(true or false)</td><td>true</td></tr><tr><td>bitVersions</td><td>The version of Bit this plugin uses</td><td>string</td><td>5.2.3</td></tr></tbody></table>

Example

```json
{
    "name": "Bit Core",
    "developer": "Robin Painter",
    "version": "5.2.3",
    "bitVersion": "5.2.3",
    "support": "https://github.com/Lockyz-Dev/bit-core/issues",
    "updateURL": "https://cdn.lockyzmedia.com/discord/bit/update/core/update.json",
    "events": "false",
    "commands": "true"
}
```
