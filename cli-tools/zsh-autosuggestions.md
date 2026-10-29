# zsh-autosuggestions — Terminal Autocomplete

A Zsh plugin that suggests commands as you type, based on your command history and optional completion strategies.

Suggestions appear as faded text after the cursor.

## Installation

```bash
brew install zsh-autosuggestions
```

Edit the Zsh configuration:

```bash
code ~/.zshrc
```

Add:

```bash
source "$(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh"
```

Reload:

```bash
source ~/.zshrc
```

## Quick Reference

| Shortcut | Description |
|---|---|
| `→` | Accept the entire suggestion at the end of the line |
| `End` | Move to the end and accept the suggestion |
| `Ctrl + E` | Move to the end and accept the suggestion with standard bindings |
| `Ctrl + F` | Move forward and accept at the end of the line |
| `Ctrl + A` | Move to the beginning of the command |
| `Ctrl + U` | Delete text before the cursor |
| `Ctrl + C` | Cancel the current input |
| `↑ / ↓` | Browse command history |

*Keyboard behavior may vary depending on custom Zsh bindings.*

## How It Works

First, execute a command:

```bash
git status --short
```

Next time, start typing:

```text
git
```

The plugin may suggest the previously used command:

```text
git status --short
```

Press `→` to accept the suggestion.

Suggestions are not executed automatically. You still need to press `Enter`.

## Configuration

Optional settings should be added to `~/.zshrc` **before** the plugin's `source` command.

### Change suggestion color

```bash
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=8'
```

### Use command history only

```bash
ZSH_AUTOSUGGEST_STRATEGY=(history)
```

### Use history and Zsh completion

```bash
ZSH_AUTOSUGGEST_STRATEGY=(history completion)
```

The completion strategy can be slower than history-only suggestions.

### Ignore specific history entries

For example, ignore commands beginning with `cd `:

```bash
ZSH_AUTOSUGGEST_HISTORY_IGNORE='cd *'
```

## Example .zshrc Configuration

```bash
# Autosuggestion settings
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=8'
ZSH_AUTOSUGGEST_STRATEGY=(history)

# Load plugin
source "$(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh"
```

After editing:

```bash
source ~/.zshrc
```

## Troubleshooting

### Suggestions do not appear

Check installation:

```bash
brew list --versions zsh-autosuggestions
```

Check the configured plugin path:

```bash
ls "$(brew --prefix)/share/zsh-autosuggestions/"
```

Verify that `~/.zshrc` contains the plugin initialization:

```bash
grep 'zsh-autosuggestions' ~/.zshrc
```

Reload the shell:

```bash
exec zsh
```

### Suggestions are difficult to see

Try a brighter suggestion color:

```bash
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=245'
```

Place this setting before the plugin initialization.

### Suggestions are outdated

The plugin primarily suggests commands from your shell history. Execute the desired command once, then try typing its prefix again.

## Maintenance

```bash
brew upgrade zsh-autosuggestions
```

To uninstall, remove its initialization line from `~/.zshrc`, then run:

```bash
brew uninstall zsh-autosuggestions
```

## Documentation

- [GitHub Repository](https://github.com/zsh-users/zsh-autosuggestions)
- [Configuration Reference](https://github.com/zsh-users/zsh-autosuggestions/blob/master/README.md)