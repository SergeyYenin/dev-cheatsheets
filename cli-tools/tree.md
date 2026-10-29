# tree — Directory Structure

A command-line utility for displaying directory structures in a tree-like format.

## Installation

```bash
brew install tree
```

Verify:

```bash
tree --version
```

## Quick Reference

| Command | Description |
|---|---|
| `tree` | Display the current directory tree |
| `tree -L 2` | Limit output to 2 levels |
| `tree -d` | Show directories only |
| `tree -a` | Include hidden files |
| `tree -h` | Show human-readable file sizes |
| `tree -s` | Display file sizes in bytes |
| `tree -f` | Print paths for each entry |
| `tree --dirsfirst` | List directories before files |
| `tree -P '*.md'` | Include matching Markdown files |
| `tree -I 'node_modules\|.git'` | Exclude specified files or directories |
| `tree --prune` | Remove empty directories from filtered results |
| `tree --help` | Show all options |

## Practical Examples

### Display a clean project structure

```bash
tree -L 3 -I 'node_modules|.git|dist|build|coverage'
```

### Display only directories

```bash
tree -d -L 3
```

### List Markdown documentation

```bash
tree -P '*.md' --prune
```

### Include hidden files, excluding dependencies

```bash
tree -a -L 2 -I '.git|node_modules'
```

### Display file sizes

```bash
tree -h -L 2
```

### Inspect a specific directory

```bash
tree -L 3 ~/Documents/GitHub
```

### Save directory structure to a file

```bash
tree -L 3 > structure.txt
```

### Copy project structure to macOS clipboard

```bash
tree -L 3 -I 'node_modules|.git|dist|coverage' | pbcopy
```

Paste the result into ChatGPT, Claude Code, or documentation using `Cmd + V`.

### Export structure as JSON

```bash
tree -J -L 3 > structure.json
```

### Display full paths

```bash
tree -f -L 2
```

## Example Output

```text
project/
├── README.md
├── src/
│   ├── components/
│   └── utils/
├── tests/
│   └── app.test.js
└── package.json
```

## Maintenance

```bash
brew upgrade tree
brew uninstall tree
```

## Documentation

- [Homebrew Formula](https://formulae.brew.sh/formula/tree)
- [tree Manual](https://linux.die.net/man/1/tree)