---
icon: sliders-up
---

# plugin.json

All the plugin.json options for a Bit Plugin and what they're used for

<table data-full-width="true"><thead><tr><th>Option</th><th>Description</th><th>Accepted Values</th><th>Default Value</th></tr></thead><tbody><tr><td>name</td><td>The plugins name</td><td>string</td><td>Bit Core</td></tr><tr><td>id</td><td>The plugins ID</td><td>string (requirements below)</td><td>bit-core</td></tr><tr><td>developer</td><td>The plugins developer</td><td>string</td><td>Lockyz Media</td></tr><tr><td>version</td><td>What version the plugin is</td><td>string</td><td>2024.1.0</td></tr><tr><td>support</td><td>A place to go to get support</td><td>string</td><td><a href="https://github.com/Lockyz-Media/bit/issues">https://github.com/Lockyz-Media/bit/issues</a></td></tr><tr><td>update_url</td><td>A url pointing to a json file used for the update notification system</td><td>string/url</td><td><a href="https://cdn.lockyzmedia.com/discord/bots/bit/plugins/core/update.json">https://cdn.lockyzmedia.com/discord/bots/bit/plugins/core/update.json</a></td></tr><tr><td>events</td><td>Whether the plugin has events or not</td><td>boolean (true/false)</td><td>true</td></tr><tr><td>commands</td><td>whether the plugin has slash commands or not</td><td>boolean (true/false)</td><td>true</td></tr><tr><td>hasIndex</td><td>Whether the plugin can start on bot startup or not</td><td>boolean (true/false)</td><td>true</td></tr><tr><td>mainFile</td><td>The file the bot should use to find the startup function</td><td>string</td><td>index.js</td></tr><tr><td>list_in_plugins_command</td><td>Whether to display the plugin in the plugins command</td><td>boolean (true/false)</td><td>true</td></tr><tr><td>requirements</td><td>The various requirements for the plugin</td><td>array</td><td>See Below</td></tr></tbody></table>

Example

```json
{
    "name": "Bit Core",
    "id": "bit-core",
    "developer": "Lockyz Media",
    "version": "2024.1.0",
    "support": "https://github.com/Lockyz-Media/bit/issues",
    "update_url": "https://cdn.lockyzmedia.com/discord/bots/bit/plugins/core/update.json",
    "events": true,
    "commands": true,
    "hasIndex": true,
    "mainFile": "index.js",
    "list_in_plugins_command": true,
    "requirements": {
        "bit": {
            "version": "2024.1.0",
            "level": "1"
        }
    }
}
```

## Plugin IDs

Plugins use an ID system to make it easier for developers wanting to use your code, to do their code. Plugin IDs will be used for plugin requirements, querying plugins (ex. loading the plugin list), and other bot functions. All plugins must use unique ID's when loaded into the bot, otherwise the bot will disable the plugin loaded second (We will only enforce plugin ID's in our certified plugins program. Plugins with the ID of bit-core will cause the bot to crash).

Plugin ID requirements are:

MUST be in Kebab Case (ex. kebab-case)!

CANNOT include numbers!

CANNOT include symbols bar the dash (-) that replaces the space!

CANNOT include a space - this WILL break the bot, use a dash (-) instead!

CANNOT use the name `bit-core`

CANNOT use offensive language.
