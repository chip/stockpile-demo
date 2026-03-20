# Stockpile

A terminal UI application for managing and tracking software packages on macOS.
Linux support coming soon.

## Demo

### Help with ? key

![Help with ? key](./assets/demo-help.gif)

### Navigation with j and k keys

![Navigation with j and k keys](./assets/demo-nav.gif)

### Filter package listing with /

*(Type search term after forward slash)*

![Filter package listing with /](./assets/demo-filter.gif)

### View package details

*(Press Enter key for selected package)*

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
- RatatuiRuby gem (1.4.1+)

## Installation

**AFTER LICENSE PURCHASE** (buy now button coming soon)

### Quick Install

```bash
# Install dependencies
bundle install

# Make the executable runnable
chmod +x bin/stockpile

# Run the application
./bin/stockpile
```

For detailed installation options, see [INSTALL.md](INSTALL.md).

## Usage

### Navigation
- `j` / `k` / `↓` / `↑` - Move up/down in lists
- `Enter` - View package details
- `Esc` / `Backspace` - Go back to list
- `?` - Toggle help view
- `q` - Quit

### Package Management
- `/` - Filter packages (type to search)
- `u` - Check for updates on selected package
- `U` - Upgrade selected package
- `r` - Check and upgrade all packages
- `x` - Uninstall selected package
- `i` - View brew info (in details view)
- `R` - Rebuild package registry

## Data Storage

Stockpile follows platform conventions for data storage:

**macOS:**
- Registry: `~/Library/Application Support/Stockpile/registry.json`
- Debug log: `~/Library/Application Support/Stockpile/State/debug.log`
- Error log: `~/Library/Application Support/Stockpile/State/last_error.txt`

**Linux:**
- Registry: `~/.local/share/stockpile/registry.json`
- Debug log: `~/.local/state/stockpile/debug.log`
- Error log: `~/.local/state/stockpile/last_error.txt`

## Debugging

Enable debug logging:

```bash
export STOCKPILE_DEBUG=1
./bin/stockpile
```

View debug logs:

```bash
# Using the helper script (auto-detects OS)
./bin/stockpile-debug-log

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

## Development

See [DEVELOPMENT.md](DEVELOPMENT.md) for:
- Project structure and architecture
- Adding new package detectors
- Adding new views
- Code style guidelines
- Error handling patterns

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

see [LICENSE.txt](LICENSE.txt) file for details

## Author

Built with ❤️ by [@chip](https://github.com/chip) using [Ruby](https://www.ruby-lang.org/) and [RatatuiRuby](https://www.ratatui-ruby.dev)
