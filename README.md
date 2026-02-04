# pr-status

A lightweight bash utility to check GitHub PR status on the fly using the GitHub CLI.

## Installation

### Option 1: Add to PATH
```bash
curl -o ~/.local/bin/pr-status https://raw.githubusercontent.com/chinmayrelkar/pr-status/main/pr-status
chmod +x ~/.local/bin/pr-status
export PATH="$HOME/.local/bin:$PATH"
```

### Option 2: Manual Installation
Clone this repo and copy the script to your PATH:
```bash
git clone https://github.com/chinmayrelkar/pr-status.git
cp pr-status/pr-status ~/.local/bin/
chmod +x ~/.local/bin/pr-status
```

## Prerequisites

- `gh` (GitHub CLI) - [Install](https://cli.github.com/)
- `git` - For repo-based context (optional)
- `bash` - Version 4+

## Usage

### Scenario 1: All PRs across all repos
```bash
pr-status
```

### Scenario 2: All PRs in a specific repo
```bash
pr-status owner/repo
```

### Scenario 3: Specific PR in current repo
Must be inside a git repository:
```bash
cd ~/repos/myrepo
pr-status 42
```

### Scenario 4: Specific PR in any repo
```bash
pr-status owner/repo 42
```

## Examples

```bash
# All your open PRs across all repos
$ pr-status
Fetching all open PRs for current user across all repos...

[owner/repo-1]
Fetching PR #10 status...

PR #10: Add feature

✅ SUCCESS - Tests
✅ SUCCESS - Linting
✅ All checks passed!

[owner/repo-2]
Fetching PR #42 status...

PR #42: Fix bug

✅ SUCCESS - Tests
⏳ PENDING - Build
⏳ Some checks are still pending

Reviews:
  - reviewer: APPROVED
```

```bash
# All PRs in a specific repo
$ pr-status owner/repo
Fetching all open PRs in owner/repo...

Fetching PR #42 status...
PR #42: Fix bug
...
```

```bash
# Specific PR in current repo
$ cd ~/repos/myrepo
$ pr-status 42
Fetching PR #42 status...
...
```

```bash
# Specific PR in any repo
$ pr-status owner/repo 42
Fetching PR #42 status...
...
```

## Error Handling

```bash
# Error: PR number without context
$ cd /tmp && pr-status 42
Error: Cannot find PR #42 without repository context
Usage:
  pr-status                              (all PRs across all repos)
  pr-status <owner/repo>                 (all PRs in repo)
  pr-status <pr_number>                  (must be in a git repo)
  pr-status <owner/repo> <pr_number>     (specific PR in repo)
```

## Features

- ✅ Color-coded output (green/yellow/red)
- ✅ Shows all status checks
- ✅ Displays review status
- ✅ Works across all repos or single repo
- ✅ Works with git repo context or explicit repo
- ✅ No external dependencies (except `gh` CLI)
- ✅ Pure bash (no Python required)

## License

MIT
