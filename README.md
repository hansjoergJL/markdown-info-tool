# Info Script

A lightweight, portable command-line tool for managing ad hoc information snippets in markdown files.

## Overview

The Info Script is a bash utility that provides a simple interface for quickly capturing, organizing, and retrieving information in markdown format. Perfect for developers, system administrators, and anyone who needs to maintain quick reference notes across multiple machines.

## Features

- **Quick Note-Taking**: Append text to markdown files with a single command
- **Multi-File Management**: Create and manage multiple topic-specific markdown files
- **Search Functionality**: Find content within files using pattern matching
- **Directory Listing**: View all available markdown files with metadata
- **Content Management**: Edit files in nano or delete the last line (undo mistakes)
- **Portable Configuration**: Use environment variables for custom directory locations
- **Cross-Platform**: Works on macOS, Linux, and other Unix-like systems

## Installation

### Quick Install

```bash
# Download the script
curl -O https://raw.githubusercontent.com/hansjoergJL/markdown-info-tool/main/info

# Make it executable
chmod +x info

# Move to a directory in your PATH
sudo mv info /usr/local/bin/info
```

### Manual Install

1. Download or clone this repository
2. Copy the `info` script to a directory in your PATH:
   ```bash
   sudo cp info /usr/local/bin/info
   sudo chmod +x /usr/local/bin/info
   ```

## Configuration

### Default Directory

By default, the script uses `~/Development/info/` as the storage directory.

### Custom Directory

Set the `INFO_BASE_DIR` environment variable to use a different location:

```bash
# Temporary override
INFO_BASE_DIR="/path/to/my/notes" info "my note"

# Permanent setting (add to ~/.bashrc, ~/.zshrc, etc.)
export INFO_BASE_DIR="/path/to/my/notes"
```

### Custom Editor

Set the `INFO_EDITOR` environment variable to use a different editor (default: nano):

````bash
# Temporary override
INFO_EDITOR="vim" info edit

# Permanent setting (add to ~/.bashrc, ~/.zshrc, etc.)
export INFO_EDITOR="vim"        # Use vim
export INFO_EDITOR="code"       # Use VS Code
export INFO_EDITOR="emacs"      # Use Emacs

## Usage

### Basic Commands

```bash
# Show help and current configuration
info help
info --help

# Show version
info --version

# List all available markdown files
info list

# Quick note to default file (common.md)
info "Remember to update the documentation"

# Note to specific file
info docker.md "Docker container restart command: docker restart container_name"

# Note to local file in current directory
info ./project-notes.md "Meeting notes from today"
````

### Viewing Content

```bash
# Show all content from default file
info show

# Search within default file
info show "docker"
info search "docker"

# Show specific file
info network.md show

# Search within specific file
info network.md show "IP address"
info network.md search "IP address"
```

### Editing Files

```bash
# Edit default file
info edit

# Edit specific file
info docker.md edit

# Edit local file
info ./local-notes.md edit
```

### Content Management

```bash
# Delete last line from default file (undo last entry)
info delete

# Delete last line from specific file
info docker.md delete
```

## File Organization

- **Storage Location**: Configurable via `INFO_BASE_DIR` (default: `~/Development/info/`)
- **Default File**: `common.md` - used when no specific file is mentioned
- **Topic Files**: `filename.md` - organized by topic (e.g., `docker.md`, `ssh.md`, `network.md`)
- **Local Files**: `./filename.md` - files in current working directory

## Examples

### Quick Reference System

```bash
# System administration notes
info ssh.md "SSH tunnel: ssh -L 8080:localhost:80 user@server"
info network.md "Check open ports: netstat -tuln"
info docker.md "Remove all containers: docker rm $(docker ps -aq)"

# Development notes
info git.md "Undo last commit: git reset --soft HEAD~1"
info vim.md "Search and replace: :%s/old/new/g"

# Daily notes
info "Meeting with team scheduled for 3pm"
info project.md "Bug fix deployed to staging"
```

### Multi-Machine Setup

```bash
# Work machine
export INFO_BASE_DIR="$HOME/work-notes"

# Personal machine
export INFO_BASE_DIR="$HOME/personal-notes"

# Server environment
export INFO_BASE_DIR="/opt/admin-notes"
```

## Advanced Usage

### Integration with Shell Aliases

```bash
# Add to your shell profile
alias n="info"                    # Quick note
alias nl="info list"              # List notes
alias ns="info show"              # Show notes
alias ne="info edit"              # Edit notes
```

### Backup and Sync

Since all data is stored in standard markdown files, you can easily:

- **Version control**: `git init` in your info directory
- **Sync across machines**: Use cloud storage (Dropbox, Google Drive, etc.)
- **Backup**: Simple file copying or rsync

## Error Handling

The script includes comprehensive error handling:

- **File existence checks** before operations
- **Empty file validation** for delete operations
- **Clear error messages** with color coding
- **Safe operations** - no risk of data loss beyond intended deletions
- **Automatic directory creation** when using custom paths

## Requirements

- **Bash**: Version 3.0 or higher
- **Standard Unix utilities**: `find`, `grep`, `sed`, `ls`, `awk`
- **Text Editor**: `nano` (can be modified to use other editors)
- **Operating System**: macOS, Linux, or Unix-like systems

## Version History

- **1.6.0**: Version banner goes to stderr so stdout stays clean for data; fixed wildcard-search quote; simplified append.
- **1.5.1**: Merged features from Linux and macOS versions, added cross-platform compatibility.
- **1.5.0**: Added `--version` flag and `search` command.
- **1.4.2**: macOS-specific `sed` command.
- **1.3.0**: Added configurable editor support via INFO_EDITOR environment variable
- **1.2.0**: Added configurable directory support via environment variables
- **1.1.1**: Improved file filtering to exclude project files
- **1.1.0**: Added `delete` command for content management
- **1.0.2**: Added `list` command for file overview
- **1.0.1**: Initial release with basic functionality

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Make your changes
4. Test thoroughly
5. Commit your changes: `git commit -am 'Add feature'`
6. Push to the branch: `git push origin feature-name`
7. Create a Pull Request

## License

MIT License - feel free to use, modify, and distribute.

## Support

- **Issues**: Report bugs or request features via GitHub Issues
- **Documentation**: This README and built-in help (`info help`)
- **Examples**: See the examples section above

## Author

**© Joedike, JL Software Solutions**

---

_Simple tools for complex workflows._
