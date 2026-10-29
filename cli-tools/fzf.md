# fzf — Interactive Fuzzy Finder

A command-line fuzzy finder for files, directories, command history, Git branches, and other lists.

## Installation

```bash
brew install fzf
```

Enable Zsh integration in `~/.zshrc`:

```bash
source <(fzf --zsh)
```

Reload:

```bash
source ~/.zshrc
```

Check version:

```bash
fzf --version
```

## Keyboard Shortcuts

| Shortcut | Description |
|---|---|
| `Ctrl + R` | Search command history |
| `Ctrl + T` | Search files and directories |
| `Option + C` | Select and switch to a directory |
| `↑ / ↓` | Navigate results |
| `Enter` | Confirm selection |
| `Esc` | Cancel |
| `Tab` | Select item in multi-selection mode |
| `Shift + Tab` | Deselect item |

**macOS note:** `Option + C` may require enabling **Use Option as Meta key** in Terminal settings.

## Quick Reference

| Command | Description |
|---|---|
| `fzf` | Start interactive fuzzy search |
| `fzf --multi` | Allow multiple selections |
| `fzf --height 40%` | Limit interface height |
| `fzf --reverse` | Place prompt at the top |
| `fzf --query 'config'` | Start with a search query |
| `fzf --preview 'cat {}'` | Preview the highlighted file |
| `fzf --border` | Show an interface border |
| `fzf --version` | Print installed version |
| `fzf --help` | Show available options |

## Practical Examples

### Search command history

Press:

```text
Ctrl + R
```

Type part of a previously executed command, select it, and press `Enter` to bring it back to the command line.

### Search files

Press:

```text
Ctrl + T
```

The selected file path will be inserted into the current command.

### Navigate directories

Press:

```text
Option + C
```

Search for a directory and press `Enter` to navigate into it.

### Find and open a file in VS Code

```bash
file=$(fzf) && code "$file"
```

Requires the VS Code `code` command to be installed in your PATH.

### Find Markdown documents

```bash
find . -type f -name '*.md' | fzf
```

### Open a selected Markdown file

```bash
file=$(find . -type f -name '*.md' | fzf) && code "$file"
```

### Search directories

```bash
find . -type d -not -path '*/.git/*' | fzf
```

### Navigate to a selected directory

```bash
dir=$(find . -type d -not -path '*/.git/*' | fzf) && cd "$dir"
```

### Preview selected files

```bash
fzf --preview 'head -100 {}'
```

### Search and switch Git branches

```bash
branch=$(git branch --format='%(refname:short)' | fzf) && git switch "$branch"
```

### Select multiple files

```bash
fzf --multi
```

Use `Tab` to mark selections and `Enter` to confirm them.

## Fuzzy Tab Completion

With shell integration enabled, type the following command prefix and press `Tab`.

### Find files

```text
code **
```

### Find directories

```text
cd **
```

### Find SSH hosts

```text
ssh **
```

The examples show what to type before pressing `Tab`.

## Advanced Configuration

### Change default interface layout

Add to `~/.zshrc`:

```bash
export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'
```

### Directory preview with tree

Add before the fzf shell integration line:

```bash
export FZF_ALT_C_OPTS="--preview 'tree -C -L 2 {}'"
```

Now `Option + C` shows a directory preview.

Requires `tree` to be installed.

### File preview with bat

Install `bat`:

```bash
brew install bat
```

Configure a preview for `Ctrl + T`:

```bash
export FZF_CTRL_T_OPTS="--preview 'bat --color=always --style=numbers --line-range=:100 {}'"
```

### Example .zshrc Configuration

```bash
# fzf defaults
export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'

# Directory preview
export FZF_ALT_C_OPTS="--preview 'tree -C -L 2 {}'"

# Load fzf integration
source <(fzf --zsh)
```

Reload:

```bash
source ~/.zshrc
```

## Troubleshooting

### Ctrl + R does not open fzf

Check whether integration is enabled:

```bash
grep 'fzf --zsh' ~/.zshrc
```

Restart the shell:

```bash
exec zsh
```

### Option + C does not work

In macOS Terminal:

1. Open **Terminal → Settings → Profiles → Keyboard**.
2. Enable **Use Option as Meta key**.
3. Try `Option + C` again.

### VS Code command not found

In VS Code, open the Command Palette:

```text
Cmd + Shift + P
```

Run:

```text
Shell Command: Install 'code' command in PATH
```

Restart Terminal.

## Maintenance

```bash
brew upgrade fzf
```

To uninstall, remove the initialization line from `~/.zshrc` and run:

```bash
brew uninstall fzf
```

## Documentation

- [fzf GitHub Repository](https://github.com/junegunn/fzf)
- [Shell Integration](https://junegunn.github.io/fzf/shell-integration/)
- [Homebrew Formula](https://formulae.brew.sh/formula/fzf)