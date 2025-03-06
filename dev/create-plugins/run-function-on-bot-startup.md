---
icon: play
---

# Run function on bot startup

You can run create features scheduled to run when the bot starts.

In order to allow for this you'll need to fulfill some prerequisites

## plugin.json required parameters

has\_index MUST be marked as true. If you don't mark this true Bit will skip the file

main\_file MUST be set to the FULL name of your file. Bit uses index.js by default, it's highly recommended you keep it that way.

start\_function in your main\_file. The actual function that starts on bot startup MUST be start\_function.



Start index.js example

```javascript
const core = require('bit/core')

// In order to allow the bot to read the start_function it MUST be set as an export.
module.exports = {
    // Defines the start_function
    start_function: function start_function() {
        // Calls bit core and tells it to create an info log telling the user the plugin has loaded.
        core.log(0, "Bit Core", true, "Successfully Loaded!")
    }
}
```

