# Configuration Choices

## Theming

### Font: FiraCode Nerd Font Mono 12
- **Why**: Consistency with kitty, helix, and other terminal tools
- **Benefit**: Nerd Font icons for visual consistency
- **Mono variant**: Ensures proper alignment in menu layout

### Colors (Gruvbox)
- **Background**: `#282828d0` - Semi-transparent dark background
- **Foreground**: `#fbf1c7` - Gruvbox light foreground
- **Border**: `#8ec07c` - Gruvbox aqua accent
- **Why**: Matches system-wide Gruvbox/Catppuccin theme

### Layout
- **Anchor**: `center` - Accessible from any screen position
- **Rows per column**: 5 - Balances readability with screen space
- **Border radius**: 10px - Modern, rounded appearance
- **Padding**: 15px - Comfortable spacing

## Menu Structure

### Top-Level Categories
1. **Windows (w)** - Most frequent operation
2. **Workspaces (s)** - Second most frequent
3. **System Menu (m)** - Quick access to QAT menu
4. **Applications (a)** - Common app launchers
5. **Niri Actions (n)** - Window management
6. **Screenshot (p)** - Capture operations

### Display Settings
Three complementary options for screen adjustment:

1. **Luminance (l)** - Brightness only (0-9 levels)
2. **Hue (h)** - Color temperature only (0-9 levels)
3. **Both (b)** - Adjusts luminance and hue simultaneously

**Design rationale**:
- **Mnemonic keys**: l=luminance, h=hue, b=both
- **Parallel execution**: `set-both` runs brightness and temperature adjustments concurrently (independent systems)
- **Efficiency**: Common case (adjusting both) requires same keypresses as individual adjustments
- **Flexibility**: Can still adjust independently when needed
- **Consistent interface**: All three use 0-9 number scheme with `keep_open: true`

### Key Assignment Logic
- Single-letter mnemonics (w=windows, s=spaces, a=apps)
- Consistent with muscle memory from other tools
- Avoids conflicts with common compositor bindings

## Configuration Options

### Keyboard Layout Detection
- `auto_kbd_layout: true` - Automatically detect keyboard layout
- **Why**: Multi-layout support without manual configuration

### Compositor Shortcuts
- `inhibit_compositor_keyboard_shortcuts: false` - Don't override niri bindings
- **Why**: wlr-which-key complements niri, doesn't replace it
