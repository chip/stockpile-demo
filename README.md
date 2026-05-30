# Stockpile

A terminal UI application for managing and tracking software packages on macOS and Linux.

Supports the following package managers:

* [Homebrew](https://brew.sh) (macOS/Linux)
* [apt](https://salsa.debian.org/apt-team/apt) (Debian/Ubuntu)
* [dnf](https://github.com/rpm-software-management/dnf) (Fedora/RHEL)
* [pacman](https://gitlab.archlinux.org/pacman/pacman) (Arch)
* [Flatpak](https://flatpak.org)
* [Snap](https://snapcraft.io)
* System packages (software installed under `/bin`, `/usr/bin`, `/sbin`, `/usr/sbin`)

## Purchase

<a href="https://chipcastledotcom.gumroad.com/l/stockpile" alt="Buy Stockpile on Gumroad">
    <img src="./assets/gumroad.webp" width="50%" height="50%">
</a>

## Demo

### Help with ? key

![Help with ? key](./assets/demo-help.gif)

### Vim-style navigation

Keys mappings:

* `j` *down*
* `k` *up*
* `Ctrl-f` *down 10 lines*
* `Ctrl-b` *up 10 lines*
* `gg` *top*
* `G` *bottom*

![Vim-style navigation](./assets/demo-nav.gif)

### Filter package listing with / (followed by search term)

![Filter package listing with /](./assets/demo-filter.gif)

### View package details (Press Enter key for selected package)

![View package details](./assets/demo-details.gif)

### Upgrade all brew packages with r key

![Upgrade all brew packages with r key](./assets/demo-upgrade-all.gif)

### Upgrade single brew package with U key (Use u key to check if new version is available)

![Upgrade single brew package with U key (Use u key to check if new version is available)](./assets/demo-upgrade-package.gif)

### Run brew info from package details view

![Run brew info from package details view](./assets/demo-brew-info.gif)

### Uninstall brew package with x key

![Uninstall brew package with x key](./assets/demo-uninstall.gif)

### Rebuild package registry with R key

![Rebuild package registry with R key](./assets/demo-rebuild-registry.gif)

## Features

- 📦 **Package Management**
  - Scans [Homebrew](https://brew.sh) and system packages
  - Package listing with real-time filtering
  - Detailed package information view with two-column layout
  - View installed files and dependencies
  - Package registry persistence with automatic save on exit

- 🎨 **User Interface**
  - Beautiful terminal UI using [RatatuiRuby](https://www.ratatui-ruby.dev)
  - Responsive two-column package details view
  - Optimized rendering with intelligent caching
  - Context-aware navbar with accurate key bindings
  - Built-in help system (press `?`)

- 🔧 **Package Operations**
  - Check for package updates
  - Upgrade individual packages or all at once
  - Uninstall packages
  - View brew info for packages
  - Rebuild registry when needed

- 🐛 **Debugging & Reliability**
  - Debug logging with configurable output
  - Automatic registry backup and recovery
  - Thread-safe lazy loading of package files
  - Error handling with detailed error logs

## Requirements

- Ruby 3.0+
- RatatuiRuby gem (1.5+)

## Installation

Purchase a license from Gumroad and run the installer script included with your download:

```bash
chmod +x stockpile-install.sh
./stockpile-install.sh
```

## Usage

### Vim-style navigation
- `j` / `k` - Move down/up in lists
- `Ctrl-f` / `Ctrl-b` - Move down/up in lists (10 lines at a time)
- `G` / `gg` - Move to bottom/top in lists
- `Enter` - View package details
- `Esc` / `Backspace` - Go back to list
- `?` - Toggle help view
- `q` - Quit

### Package Management
- `/` - Filter packages (type to search)
- `M` - Search package descriptions
- `s` - Sort package list by manager, install date, version, outdated, and name
- `Space` - Mark package for bulk upgrade **(brew onlY)**
- `u` - Check for updates on selected package
- `v` - Detect version of selected package
- `U` - Upgrade selected package
- `x` - Uninstall selected package
- `r` - Check and upgrade all packages
- `R` - Rebuild package registry
- `e` - Export package registry
- `i` - View brew info (in details view)

## Data Locations

Stockpile stores data in OS-appropriate locations following platform conventions:

**macOS:**
- Registry: `~/Library/Application Support/Stockpile/registry.json`
- Debug log: `~/Library/Application Support/Stockpile/State/debug.log`
- Error log: `~/Library/Application Support/Stockpile/State/last_error.txt`

**Linux:**
- Registry: `~/.local/share/stockpile/registry.json`
- Debug log: `~/.local/state/stockpile/debug.log`
- Error log: `~/.local/state/stockpile/last_error.txt`

## Debugging

![Debugging](./assets/demo-debug.gif)

Enable debug logging:

```bash
export STOCKPILE_DEBUG=1
stockpile
```

Or try for single run of stockpile:

```bash
STOCKPILE_DEBUG=1 stockpile
```

View debug logs:

```bash
# Using the helper script (auto-detects OS)
stockpile-debug-log

# Or manually with tail
# macOS:
tail -f ~/Library/Application\ Support/Stockpile/State/debug.log

# Linux:
tail -f ~/.local/state/stockpile/debug.log
```

Debug logging captures:
- All key events and their codes
- View mode transitions
- Filter operations
- Package operations (upgrade, uninstall)
- Performance metrics
- Any errors or unexpected behavior

## View last error

```bash
# Or manually with cat
# macOS:
cat ~/Library/Application Support/Stockpile/State/last_error.txt

# Linux:
cat ~/.local/state/stockpile/last_error.txt
```

## Platform-Specific Notes

### macOS

- Uses native macOS paths for installing stockpile (`~/Library/Application Support/`)
- Homebrew detection requires `/opt/homebrew/Cellar` or `/usr/local/Cellar` installation
- System packages scanned from `/bin`, `/usr/bin`, `/sbin`, and `/usr/sbin`

### Linux

- Follows XDG Base Directory Specification
- Respects `XDG_DATA_HOME`, `XDG_STATE_HOME` environment variables
- System packages scanned from `/bin`, `/usr/bin`, `/sbin`, and `/usr/sbin`

## Getting Help

If you encounter issues:

1. See **Debugging** section. **Enable debug logging** and check the logs.
2. **Review error messages** in `last_error.txt`
3. **Try rebuilding registry** with `R` key or `stockpile-rescan`
4. Contact support via email: support at chipcastle dot com

## License

see LICENSE.txt on Gumroad for details.

## Author

Built with ❤️ by [@chip](https://github.com/chip) using [Ruby](https://www.ruby-lang.org/) and [RatatuiRuby](https://www.ratatui-ruby.dev)
