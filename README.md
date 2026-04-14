# agent-sound

A Claude Code plugin that plays a sound when Claude finishes its turn or needs your input.

- **Stop** (turn finished) → `sounds/stop.mp3`
- **Notification** (permission prompt / idle) → `sounds/notification.mp3`

Bundled sound files are included — no system dependencies beyond macOS `afplay`.

## Requirements

- macOS (uses the built-in `afplay` CLI)

## Install as a plugin

1. Add this repo as a marketplace:

   ```
   /plugin marketplace add noodleweapon/agent-sound
   ```

2. Install the plugin:

   ```
   /plugin install agent-sound@agent-sound
   ```

3. Restart Claude Code (or open `/hooks` once) so the hooks are picked up.

## Manual install (no plugin system)

Clone the repo somewhere permanent, then add these hooks to `~/.claude/settings.json`, replacing `/path/to/agent-sound` with the absolute path to your clone:

```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "afplay \"/path/to/agent-sound/sounds/stop.mp3\" &"
          }
        ]
      }
    ],
    "Notification": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "afplay \"/path/to/agent-sound/sounds/notification.mp3\" &"
          }
        ]
      }
    ]
  }
}
```

If `settings.json` already has a `hooks` block, merge these entries in rather than replacing it. Open `/hooks` or restart Claude Code to pick up the changes.

## Customize the sounds

Replace `sounds/stop.mp3` or `sounds/notification.mp3` with any `.aiff`/`.wav`/`.mp3` file `afplay` can play. If you change the extension, also update the paths in `hooks/hooks.json`. macOS ships a set of built-in sounds at `/System/Library/Sounds/` (Basso, Blow, Bottle, Frog, Funk, Glass, Hero, Morse, Ping, Pop, Purr, Sosumi, Submarine, Tink).
