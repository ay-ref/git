# Git Stash Cheat Sheet

## Basic Commands

### Stash Changes
```bash
# Stash working directory changes (including untracked files)
git stash push -m "stash message"

# Stash including untracked files
git stash -u

# Stash including ignored files
git stash -a

# Shortcut - stash without message
git stash
```

### View Stashes
```bash
# List all stashes
git stash list

# Show stash content
git stash show stash@{0}

# Show stash content with diff
git stash show -p stash@{0}
```

### Apply Stashes
```bash
# Apply latest stash and keep it in stash list
git stash apply

# Apply specific stash
git stash apply stash@{1}

# Apply and remove from stash list
git stash pop

# Apply specific stash and remove it
git stash pop stash@{1}
```

### Remove Stashes
```bash
# Delete latest stash
git stash drop

# Delete specific stash
git stash drop stash@{2}

# Clear all stashes
git stash clear
```

## Advanced Usage

### Create a Branch from Stash
```bash
# Create new branch from stash
git stash branch branch_name stash@{1}
```

### Partial Stashing
```bash
# Interactive stashing (choose which hunks to stash)
git stash -p

# Stash specific files
git stash push file1.txt file2.txt
```

### Stash Management
```bash
# View stash in detail
git stash show -p

# Check what's in stash without applying
git stash show stash@{0}
```

## Common Workflows

### Quick Context Switch
```bash
# Save current work
git stash push -m "WIP: feature implementation"

# Switch to another branch
git checkout main

# Do some work...

# Return to original branch and restore work
git checkout feature-branch
git stash pop
```

### Testing Clean Working Directory
```bash
# Stash changes to test clean state
git stash

# Run tests on clean codebase
npm test

# Restore changes
git stash pop
```

### Stashing with Message
```bash
git stash push -m "Save before merging main"
git stash list  # Shows descriptive messages
```

## Useful Aliases
Add to your `.gitconfig`:
```ini
[alias]
    sl = stash list
    ss = stash show -p
    sa = stash apply
    sp = stash pop
```

## Key Points to Remember
- Stash is a stack (LIFO - Last In First Out)
- Use descriptive messages for better organization
- `pop` removes the stash, `apply` keeps it
- Untracked files need `-u` flag to be stashed
- Stashes are local to your repository
