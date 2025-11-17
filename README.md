# wlr-which-key Configuration

Hierarchical hotkey menu for Niri compositor, providing discoverable access to window management, workspace operations, and system functions.

## Dependencies

- **Required**: wlr-which-key, niri
- **Optional**: quick-access-term (for qatpipe commands), kitty
- **Font**: FiraCode Nerd Font Mono

## Installation

```bash
cd ~/Environment
stow wlr-which-key
```

## Usage

Launch wlr-which-key to see the menu overlay. Navigate using the displayed key hints.

## Documentation

- [Configuration Choices](docs/implementation/configuration.md) - Why we configured it this way
- [Niri Integration](docs/implementation/niri-integration.md) - How it integrates with Niri
- [Quick-Access-Term Integration](docs/implementation/qat-integration.md) - How it integrates with QAT
- [Usage Guide](docs/workflow/usage.md) - How to use and customize
- [Reference](docs/reference/config-options.md) - Official wlr-which-key documentation

## Quick Reference

- **Windows**: `w` - Focus, bring, or manage windows
- **Workspaces**: `s` - Navigate and manage workspaces
- **System Menu**: `m` - Access system menu via quick-access-term
- **Applications**: `a` - Launch common applications
- **Niri Actions**: `n` - Window and layout management
- **Screenshot**: `p` - Capture screen, window, or area
