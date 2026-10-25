# Farcal UI

Patched build of the Farcal UI library (original by samet).

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/vbbi33jkllljcvvbjkqw89fjjkjhkjzsdaih/farcal-ui/main/Farcal.lua"))()
```

The usage is the same as the original, see the example in the original download. The font and the spring helper are fetched from this repository the first time the library loads.

## Options

Pass a table as the first argument to change how the library behaves:

```lua
local Library = loadstring(game:HttpGet(".../Farcal.lua"))({
	Report = function(Context, Message) end,
	Directory = "MyFolder",
})
```

| Option | Use |
| --- | --- |
| `Report` | Called instead of printing. The library never writes to the console, errors and warnings go here |
| `Directory` | Workspace folder for configs and the font cache, default `Farcal` |
| `Fetch` | `function(Path)` that returns a file, replaces the default download |
| `Base` | Url prefix the font and spring are downloaded from |

## What was changed

- Silent: every callback, delayed task, thread and event connection is protected, `warn` goes to `Report`.
- Own global (`FarcalLibrary`) so it does not clash with other libraries, and `Exit` no longer breaks delayed callbacks.
- A working font (the original link is dead) and the spring helper are bundled.
- Key system accepts a `Validate` function, for example to check a key with your own server.
- Notification cards accept `MaxHeight` and measure long text correctly.
- Sliders without a step no longer return NaN, single choice dropdowns close after a pick.
