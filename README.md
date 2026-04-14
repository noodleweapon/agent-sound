# agent-sound

Claude Code plugin that plays a sound when Claude finishes its turn or needs your input.

- **Stop** (turn done) → `Glass.aiff`
- **Notification** (needs permission / idle prompt) → `Funk.aiff`

Uses macOS `afplay` with built-in system sounds. macOS only.

## Install

Add this repo as a marketplace and enable the plugin, or drop it under `~/.claude/plugins/`.

## Customize

Edit `hooks/hooks.json` to swap the sounds. Any `.aiff` under `/System/Library/Sounds/` works (Basso, Blow, Bottle, Frog, Funk, Glass, Hero, Morse, Ping, Pop, Purr, Sosumi, Submarine, Tink).
