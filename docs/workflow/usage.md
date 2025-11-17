# Usage Guide

## Launching wlr-which-key

Currently, wlr-which-key must be launched manually or via a custom keybinding:

```bash
wlr-which-key
```

**Future**: A niri keybinding will be added after initial adoption.

## Navigating the Menu

1. **Launch** wlr-which-key
2. **Press** the key shown next to the desired action
3. **Navigate** submenus by pressing the corresponding key
4. **Execute** commands by selecting the final menu item
5. **Cancel** by pressing `Escape` or clicking outside the menu

## Menu Structure

```
w - Windows
  f - Focus Window (QAT picker)
  u - Focus Urgent
  b - Bring Window Here

s - Workspaces
  g - Goto Workspace (QAT picker)
  b - Bring Workspace (QAT picker)
  s - Send to Workspace (QAT picker)
  n - New Workspace
  r - Rename Workspace

m - System Menu (QAT menu)

a - Applications
  f - Firefox
  k - Kitty
  r - Rofi

n - Niri Actions
  f - Fullscreen
  t - Toggle Floating
  m - Maximize Column
  c - Close Window

p - Screenshot
  s - Screen
  w - Window
  a - Area (Interactive)
```

## Customizing the Menu

### Adding Commands

Edit `.config/wlr-which-key/config.yaml`:

```yaml
menu:
  - key: x
    desc: My Custom Command
    cmd: my-command --args
```

### Adding Submenus

```yaml
menu:
  - key: x
    desc: My Category
    submenu:
      - key: a
        desc: Action A
        cmd: command-a
      - key: b
        desc: Action B
        cmd: command-b
```

### Changing Theming

Modify the theming section in `config.yaml`:

```yaml
font: FiraCode Nerd Font Mono 12
background: "#282828d0"
color: "#fbf1c7"
border: "#8ec07c"
```

## Testing Changes

After modifying `config.yaml`:

1. **Restow** the configuration:
   ```bash
   cd ~/Environment
   stow -R wlr-which-key
   ```

2. **Relaunch** wlr-which-key to see changes

3. **Verify** menu structure and commands work as expected

## Troubleshooting

### Menu doesn't appear
- Check if wlr-which-key is installed: `which wlr-which-key`
- Check config syntax: `wlr-which-key --validate` (if supported)

### Commands don't execute
- Verify commands are in PATH: `which <command>`
- Check QAT services are running: `systemctl --user status qat-control.service`
- Check niri scripts are available: `ls ~/.local/bin/niri-*`

### Font doesn't render correctly
- Verify FiraCode Nerd Font is installed: `fc-list | grep FiraCode`
- Install if missing: `sudo dnf install fira-code-fonts` (or equivalent)

## Related Documentation

- [Configuration Choices](../implementation/configuration.md)
- [Niri Integration](../implementation/niri-integration.md)
- [QAT Integration](../implementation/qat-integration.md)
