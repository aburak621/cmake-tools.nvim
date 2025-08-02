# ToggleTerm Integration

cmake-tools.nvim now supports integration with the popular [toggleterm.nvim](https://github.com/akinsho/toggleterm.nvim) plugin for enhanced terminal management.

## Requirements

- [toggleterm.nvim](https://github.com/akinsho/toggleterm.nvim) plugin installed

## Configuration

To enable toggleterm integration, configure cmake-tools with the following options:

```lua
require('cmake-tools').setup({
  cmake_terminal_opts = {
    name = "Main Terminal",
    prefix_name = "[CMakeTools]: ",
    split_direction = "horizontal", -- Used as fallback if toggleterm is not available
    split_size = 11,
    
    -- ToggleTerm integration options
    use_toggleterm = true, -- Enable toggleterm integration (default: true)
    toggleterm_direction = "horizontal", -- "horizontal", "vertical", "tab", "float"
    toggleterm_close_on_exit = false, -- Close terminal when process exits
    toggleterm_auto_scroll = true, -- Auto scroll to bottom on new output
    
    -- Other options...
    start_insert_in_launch_task = false,
    start_insert_in_other_tasks = false,
    focus_on_main_terminal = false,
    focus_on_launch_terminal = false,
  },
})
```

## ToggleTerm Direction Options

- `"horizontal"` - Terminal opens as a horizontal split at the bottom
- `"vertical"` - Terminal opens as a vertical split on the side  
- `"tab"` - Terminal opens in a new tab
- `"float"` - Terminal opens as a floating window

## Features

When toggleterm is available and enabled:

1. **Enhanced Terminal Management**: Uses toggleterm's powerful terminal management features
2. **Persistent Terminals**: Terminals persist across sessions and can be toggled easily
3. **Multiple Terminal Support**: Better support for multiple terminal instances
4. **Floating Terminals**: Option to use floating terminals for a cleaner workspace
5. **Better Focus Management**: Improved focus handling when launching tasks

## Fallback Behavior

If toggleterm is not installed or `use_toggleterm` is set to `false`, cmake-tools will automatically fall back to using Neovim's built-in terminal functionality with the existing behavior.

## Example with Different Directions

### Horizontal Terminal (Default)

```lua
cmake_terminal_opts = {
  use_toggleterm = true,
  toggleterm_direction = "horizontal",
  split_size = 15,
}
```

### Vertical Terminal

```lua
cmake_terminal_opts = {
  use_toggleterm = true,
  toggleterm_direction = "vertical", 
  split_size = 80,
}
```

### Floating Terminal

```lua
cmake_terminal_opts = {
  use_toggleterm = true,
  toggleterm_direction = "float",
}
```

### Tab Terminal

```lua
cmake_terminal_opts = {
  use_toggleterm = true,
  toggleterm_direction = "tab",
}
```

## Troubleshooting

If you encounter issues:

1. Ensure toggleterm.nvim is properly installed and configured
2. Check that `use_toggleterm = true` in your cmake-tools configuration
3. Verify toggleterm is loaded before cmake-tools in your plugin manager
4. Check the cmake-tools log for any error messages

The plugin will automatically detect if toggleterm is available and log a warning if it falls back to the default terminal.
