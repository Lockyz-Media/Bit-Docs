---
description: 'The file required for Bit: Cores plugin update system to work'
icon: folder-gear
---

# update.json

{% hint style="danger" %}
This version of Bit has reached End of Life, this means it'll no longer receive ANY updates.

By continuing to use this version, you take full responsibility for any security issues that may be present.
{% endhint %}

The bot will check the update json for the latest version of the plugin, where to download it from and what version of Bit: Core it's for.

<table><thead><tr><th>Option</th><th>Description</th><th>Accepted Values</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>downloadLink</td><td>A link to the plugins latest version, is sent to the bots console when outdated</td><td>string/url</td><td>true</td></tr><tr><td>5.2</td><td>The latest version for Bit 5.2</td><td>string</td><td>true</td></tr><tr><td>5.1</td><td>The latest version for Bit 5.1</td><td>string</td><td>false</td></tr><tr><td>5.0</td><td>The latest version for Bit 5.0</td><td>string</td><td>false</td></tr></tbody></table>

Update JSON Example

```json
{
    "latest": "5.2.0",
    "developer": "Lockyz Dev",
    "downloadLink": "https://cdn.lockyzmedia.com/bit/plugins/xp/latest.zip",
    "5.2": "5.2.0",
    "5.1": "5.1.0",
    "5.0": "5.0.0"
}
```
