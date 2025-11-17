# Quick-Access-Term Integration

## Overview

wlr-which-key provides alternative access to quick-access-term (QAT) features through a hierarchical menu interface.

## Commands Used

All QAT commands use `qatpipe` to communicate with the control script:

- `qatpipe "windows-open"` - Open windows picker
- `qatpipe "workspaces-select goto"` - Goto workspace picker
- `qatpipe "workspaces-select bring"` - Bring workspace picker
- `qatpipe "workspaces-select send"` - Send to workspace picker
- `qatpipe "menu-open"` - Open system menu

## Dependency

**Hard dependency**: quick-access-term must be running.

Quick-access-term is managed by systemd services:
- `qat-control.service` - Control script (persistent)
- `qat-watcher.service` - Event watcher

These services are started automatically with niri via systemd drop-ins in `quick-access-term/.config/systemd/user/niri.service.d/qat.conf`.

**Since QAT is managed by systemd, it can be assumed to be available** when niri is running.

**This is unavoidable hardcoding** - wlr-which-key's configuration format does not support dynamic loading from directories, so commands must be explicitly specified in `config.yaml`.

## Integration Points

### Menu Categories Using QAT

1. **Windows → Focus Window** - Opens QAT windows picker
2. **Workspaces → Goto Workspace** - Opens QAT workspace picker (goto mode)
3. **Workspaces → Bring Workspace** - Opens QAT workspace picker (bring mode)
4. **Workspaces → Send to Workspace** - Opens QAT workspace picker (send mode)
5. **System Menu** - Opens QAT system menu directly

## Relationship to QAT Panel

- **QAT Panel** (`Super+Alt+Ctrl+Shift+Tab`, `Super+Alt+Ctrl+Shift+F12`): Direct hotkey access
- **wlr-which-key**: Menu-driven access to same functionality
- **Complementary**: wlr-which-key provides discoverable access for users who forget hotkeys

## Architecture

QAT uses a stateless tabs architecture:
- **Control script**: Runs in separate window, manages state
- **Panel**: Ephemeral UI that can be killed/restarted
- **qatpipe**: Communication channel between wlr-which-key and control script

See `quick-access-term/docs/implementation/stateless-tabs-architecture.md` for details.

## Error Handling

If QAT services are not running, `qatpipe` commands will fail silently. Users should ensure services are active:

```bash
systemctl --user status qat-control.service
systemctl --user status qat-watcher.service
```

## Related Files

- `quick-access-term/.local/bin/qatpipe` - Communication utility
- `quick-access-term/.config/systemd/user/qat-*.service` - Service definitions
- `quick-access-term/docs/implementation/stateless-tabs-architecture.md` - Architecture docs
