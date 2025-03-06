---
icon: desktop-arrow-down
---

# Updating to Bit 2025.2

## Plugin Count and Plugin List functions have been moved!

With bit now exporting the pluginLoader.js file and the functions within, we've officially deprecated the old `plugin_count()` and `plugin_list()` functions from Bit: Core.



Replacement Example

```
// Old Code Example
const core = require('bit/core')

const totalPlugins = core.plugin_count()
const pluginsList = core.plugin_list()

// New Code Example
const plugins = require('bit/plugins')

const totalPlugins = plugins.count()
const pluginsList = plugins.list()
```

## New Plugin Functions

This version of Bit adds a few extra functions added to make interacting between plugins easier.

For example, the new `plugins.is_active(id)` function makes it MUCH easier to know if a plugin is installed and active.



You can find more information on these new functions in [plugin-functions.md](functions/plugin-functions.md "mention")
