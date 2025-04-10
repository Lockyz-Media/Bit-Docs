---
icon: plug
---

# bit/plugins

As part of Bit 2025.2 we added a brand new suit of functions to interact with Bits plugin system.

These functions can be imported with the following code at the top of your code

```javascript
const plugins =  require("bit/plugins");
```

Theres a few different functions you can run with this import...

### [.is\_active(id, version)](.is_active-id-version.md)

Gets whether the plugin defined by the id of version is active

### [.find(id)](./#find-id)

Find a specific plugin defined by id

### [.list()](.list.md)

Shows a list of all installed plugins

### [.count()](.count.md)

Counts all the plugins installed, and outputs the number.
