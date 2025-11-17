# Niri Integration

## Overview

wlr-which-key provides a discoverable menu interface for niri commands, complementing niri's native hotkey overlay.

## Commands Used

### Direct niri Commands
Located in `niri/.local/bin/`:

- `niri-window-focus-urgent` - Focus window marked urgent
- `niri-window-bring` - Bring window to current workspace
- `niri-workspace-create-terminal` - Create new workspace interactively
- `niri-workspace-rename-terminal` - Rename workspace interactively

### Native niri msg Commands
- `niri msg action fullscreen-window` - Toggle fullscreen
- `niri msg action toggle-window-floating` - Toggle floating mode
- `niri msg action maximize-column` - Maximize column width
- `niri msg action close-window` - Close focused window
- `niri msg action screenshot-*` - Screenshot operations

## Dependency

**Hard dependency**: All niri commands must be available in PATH.

These commands are provided by the `niri` submodule in Environment. When `niri` is stowed, scripts are symlinked to `~/.local/bin/`.

**This is unavoidable hardcoding** - wlr-which-key's configuration format does not support dynamic loading from directories, so commands must be explicitly specified in `config.yaml`.

## Integration Points

### Menu Categories Using Niri

1. **Windows → Focus Urgent** - `niri-window-focus-urgent`
2. **Windows → Bring Window Here** - `niri-window-bring`
3. **Workspaces → New Workspace** - `niri-workspace-create-terminal`
4. **Workspaces → Rename Workspace** - `niri-workspace-rename-terminal`
5. **Niri Actions** - All native `niri msg action` commands
6. **Screenshot** - All screenshot commands

## Relationship to Niri Hotkey Overlay

- **Niri's overlay** (`Super+Alt+Ctrl+Shift+Slash`): Shows currently bound hotkeys
- **wlr-which-key**: Provides hierarchical menu for discovering and executing commands
- **Complementary**: wlr-which-key exposes commands that may not have hotkeys

## Future Integration

When a hotkey is bound to launch wlr-which-key, it will be added to `niri/.config/niri/config.kdl`. This will be done after initial adoption is complete.

## Related Files

- `niri/.config/niri/config.kdl` - Niri keybindings (future integration point)
- `niri/.local/bin/niri-*` - Niri helper scripts
- `niri/docs/README.md` - Niri documentation index
