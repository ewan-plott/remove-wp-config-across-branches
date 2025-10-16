# WP-Config File History Removal Documentation

## Overview
This document records the process of removing the `wp-config.php` file from the entire git history while preserving the local working copy.

## Using
 `git filter-repo` 

## Commands Executed

### 1. Stash Current Changes
```bash
git stash push -m "Stash before removing wp-config from history"
```

### 2. Remove wp-config.php from All History
```bash
git filter-repo --invert-paths --path wp-config.php --force
```

### 3. Restore Working Directory Changes
```bash
git stash pop
```

### 4. Restore Local wp-config.php
```bash
cp wp-config-old.php wp-config.php
```

## File Status After Process
- `wp-config.php`: Untracked (local only)
- `wp-config-old.php`: Untracked backup
- `wp-config-ddev.php`: Untracked development config
- `wp-config-sample.php`: Modified (tracked)
