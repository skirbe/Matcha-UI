# Matcha UI

UI library for Matcha. Everything is drawn with the Drawing API, so it doesn't need any instances.

`library.lua` is the library. `demo.lua` is an example menu that loads it.

## Loading it

```lua
loadstring(game:HttpGet("https://raw.githubusercontent.com/xposn/Matcha-UI/main/library.lua"))()
local library = _G.InterceptionUI
```

Matcha's loadstring doesn't hand back return values, so grab the library from `_G` after it loads.

## Example

```lua
local window = library:window({ name = "my menu", size = UDim2.new(0, 500, 0, 450) })
local main = window:tab({ name = "main" })
local aim = main:section({ name = "aimbot", side = "left" })

aim:toggle({ name = "enabled", flag = "aim_enabled" })
aim:keybind({ flag = "aim_key", key = Enum.KeyCode.E, mode = "hold" })
aim:colorpicker({ flag = "aim_color", color = Color3.fromRGB(255, 255, 255) })
aim:slider({ name = "fov", flag = "aim_fov", min = 0, max = 500, default = 120, suffix = "px" })
aim:dropdown({ name = "hitpart", flag = "aim_part", items = { "head", "torso" }, default = "head" })
aim:button({ name = "test", callback = function()
    library:notification({ text = "it works" })
end })
```

The keybind and colorpicker there have no name, so they sit on the right side of the toggle above them. A slider or dropdown with no name goes under that toggle instead.

Every element keeps its value in `library.flags` under its flag, so you can check things like `library.flags.aim_enabled` from anywhere. Keybinds store a table with `key`, `mode` and `active`.

## Other stuff

- `window.toggle_watermark(true)` and `window.set_watermark_position("top right")`
- `window.toggle_list(true)` shows the keybind list
- `window.set_info(title, lines)` and `window.toggle_info_list(true)` for the info box
- `window.set_menu_visibility(false)` hides the menu
- `library:get_config()` and `library:load_config(text)` for saving and loading

The demo saves configs to `Pepsi UI/configs` in your Matcha workspace.

Run `demo.lua` to see all of it. Insert opens and closes the menu.
