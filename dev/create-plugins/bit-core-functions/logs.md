---
icon: terminal
---

# Logs

Bit employs a custom logging system. To use bits new logging system you simply have to import bit/core and then follow the function structure.

```javascript
const core = require('bit/core');

// Log ERROR as Bit Example plugin
core.log(2, "Bit Example", false, "Something Broke")
// ^ Will output "[ERROR] Bit Example: Something Broke"

// Log WARNING as Bit Example Plugin
core.log(1, "Bit Example", false, "Something Broke")
// ^ Will output "[WARNING] Bit Example: Something Broke"

// Log INFO as Bit Example Plugin
core.log(0, "Bit Example", false, "Something Broke")
// ^ Will output "[INFO] Bit Example: Something Broke"
```

You can also force the log to appear in the bots console regardless of the users settings

```javascript
const core = require('bit/core');

// Force ERROR from Bit Example Plugin to appear in the bots console
core.log(2, "Bit Example", true, "Something Broke")
// ^ Will ALWAYS output "[ERROR] Bit Example: Something Broke"

// Don't Force ERROR from Bit Example Plugin to appear in the bots console
core.log(2, "Bit Example", false, "Something Broke")
// ^ Will only output "[ERROR] Bit Example: Something Broke" if the user has error logs turned on for the console
```
