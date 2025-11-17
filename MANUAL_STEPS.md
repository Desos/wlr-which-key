# Manual Steps to Complete wlr-which-key Adoption

The wlr-which-key configuration has been created and committed locally. Due to authentication restrictions, you need to complete these manual steps:

## Step 1: Push to GitHub

The GitHub repository has been created at: https://github.com/Desos/wlr-which-key

Push the local commits:

```bash
cd ~/Environment/wlr-which-key
git push -u origin main
```

## Step 2: Convert to Submodule

Once pushed, convert the directory to a proper submodule in the Environment repository:

```bash
cd ~/Environment

# Remove the directory (it's already committed and pushed)
rm -rf wlr-which-key

# Add it back as a submodule
git submodule add git@github.com:Desos/wlr-which-key.git wlr-which-key

# Commit the submodule addition
git add .gitmodules wlr-which-key
git commit -m "feat: add wlr-which-key submodule"
```

## Step 3: Deploy Configuration

Remove the old config and stow the new one:

```bash
# Backup old config (optional)
mv ~/.config/wlr-which-key/config.yaml ~/.config/wlr-which-key/config.yaml.backup

# Or just remove it
rm -rf ~/.config/wlr-which-key

# Stow the new configuration
cd ~/Environment
stow wlr-which-key

# Verify the symlink
ls -la ~/.config/wlr-which-key/
# Should show: config.yaml -> ../../Environment/wlr-which-key/.config/wlr-which-key/config.yaml
```

## Step 4: Test

Launch wlr-which-key to verify it works:

```bash
wlr-which-key
```

Test the menu:
- Press `w` for Windows menu
- Press `s` for Workspaces menu
- Press `m` for System Menu
- Press `a` for Applications
- Press `n` for Niri Actions
- Press `p` for Screenshot

Verify commands execute correctly (especially qatpipe commands require QAT services running).

## Step 5: Future Integration (Optional)

When ready to add a keybinding, edit `niri/.config/niri/config.kdl`:

```kdl
Super+Alt+Ctrl+Shift+<YourKey> { spawn "wlr-which-key"; }
```

Then restow niri:

```bash
cd ~/Environment
stow -R niri
```

## Verification Checklist

- [ ] wlr-which-key pushed to GitHub
- [ ] Converted to submodule in Environment
- [ ] Old config removed
- [ ] New config stowed successfully
- [ ] wlr-which-key launches without errors
- [ ] Menu navigation works
- [ ] Commands execute (test a few)
- [ ] QAT commands work (qatpipe)
- [ ] Niri commands work (niri-*)

## Troubleshooting

### Commands don't execute
- Check QAT services: `systemctl --user status qat-control.service`
- Check niri scripts: `ls ~/.local/bin/niri-*`
- Verify PATH includes `~/.local/bin`

### Font doesn't render
- Check font installation: `fc-list | grep FiraCode`
- Install if needed: `sudo dnf install fira-code-fonts`

### Menu doesn't appear
- Check wlr-which-key is installed: `which wlr-which-key`
- Check config syntax is valid

## Files Created

- `.config/wlr-which-key/config.yaml` - Main configuration
- `docs/implementation/configuration.md` - Configuration choices
- `docs/implementation/niri-integration.md` - Niri integration details
- `docs/implementation/qat-integration.md` - QAT integration details
- `docs/workflow/usage.md` - Usage guide
- `docs/reference/config-options.md` - Reference documentation
- `README.md` - Overview
- `.stow-local-ignore` - Stow exclusions
- `.gitignore` - Git exclusions
