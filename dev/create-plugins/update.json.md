---
description: 'The file required for Bit: Cores plugin update system to work'
icon: folder-gear
---

# update.json

The bot will check the update json for the latest version of the plugin, where to download it from and what version of Bit: Core it's for.

<table><thead><tr><th>Option</th><th>Description</th><th>Accepted Values</th><th data-type="checkbox">Required</th></tr></thead><tbody><tr><td>download_link</td><td>A link to the plugins latest version, is sent to the bots console when outdated</td><td>string/url</td><td>true</td></tr><tr><td>bit_version</td><td>Each bit version can have it's own "latest" version. If a specified version is not found the bot will tell the user to update their Bit version.</td><td>array</td><td>true</td></tr></tbody></table>

Update JSON Example

```json
{
    "download_link": "https://cdn.lockyzmedia.com/bit/plugins/xp/latest.zip",
    "bit_versions": {
        "2024.2": "2.0.0"
    }
}
```
