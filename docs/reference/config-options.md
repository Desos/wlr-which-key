# wlr-which-key Configuration Reference

## Official Documentation

For complete and up-to-date configuration options, see the official wlr-which-key documentation:

- **GitHub**: https://github.com/MaxVerevkin/wlr-which-key
- **Configuration Guide**: https://github.com/MaxVerevkin/wlr-which-key#configuration

## Quick Reference

### Theming Options
- `font` - Font family and size
- `background` - Background color (supports alpha)
- `color` - Text color
- `border` - Border color
- `separator` - Separator between key and description
- `border_width` - Border width in pixels
- `corner_r` - Corner radius in pixels
- `padding` - Internal padding in pixels
- `column_padding` - Padding between columns

### Layout Options
- `anchor` - Menu position (center, left, right, top, bottom, etc.)
- `margin_*` - Margins when anchor is not center
- `rows_per_column` - Maximum rows per column

### Behavior Options
- `inhibit_compositor_keyboard_shortcuts` - Override compositor bindings
- `auto_kbd_layout` - Automatically detect keyboard layout
- `namespace` - Layer shell surface namespace

### Menu Structure
- `menu` - Array of menu items
  - `key` - Key to press
  - `desc` - Description shown in menu
  - `cmd` - Command to execute (leaf items)
  - `submenu` - Nested menu items (branch items)

## Example Configuration

See `.config/wlr-which-key/config.yaml` for our complete configuration.
