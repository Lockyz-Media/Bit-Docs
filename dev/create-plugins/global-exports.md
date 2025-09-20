---
icon: flask-round-potion
---

# Global Exports

{% include "../../.gitbook/includes/experimental-feature.md" %}

Added in Bit 2025.2, plugins can now define global exports that can be run within other plugins.

All you need is an index.js file within your main plugin directory, and different functions within your module.exports.

Example

```javascript
module.exports = {
    test_function: function test_function() {
        console.log("Test Works!!!!")
    }
}
```

This can then be imported and used according to the example below

```javascript
const test_plugin = require("bit/plugin/test-plugin");

test_plugin.test_function();

// Outputs "Test Works!!!!"
```

This feature should be VERY useful for plugin developers who want to interact with other plugins.
