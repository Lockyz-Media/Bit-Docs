---
icon: shield-exclamation
---

# Plugin Requirements

If your plugin uses functions from another plugin, you can make sure to warn the user by making use of Bits plugin requirements system!

## Setup

Within your plugins plugin.json file you can find a field for defining your plugins requirements, these requirements will be listed when the plugin loads into bit, and when you run the plugins command.

```json
{
    "requirements": {
        "bit": {
            "version": "2025.1.0",
            "level": 0
        },
        "jupiter": {
            "version": "2025.1.0",
            "level": 2
    }
}
```

An example of a plugin requiring Bit and Jupiter

## Requirement Levels

There are 4 different levels of Bit requirements, these can be used to stop the plugin from loading if the plugin and specific version is not present, and can be used to stop the plugin from loading if the plugin IS present.



Level 0, requires the external plugin at that specific version be loaded for your plugin to work.

Level 1, requires the external plugin to be loaded regardless of said external plugins version

Level 2, is basically a soft requirement, the external plugin is not "required" but part of your plugin will not work without it. (You should include a check for this in your code, however a feature will be added to Bit Core to aid in this in the future.)

Level 3, the plugin will NOT start if a plugin of this level is also loaded. This can be used for plugins that are incompatible with yours.
