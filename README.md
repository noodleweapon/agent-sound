# agent-sound

A Claude Code plugin that plays a sound when Claude finishes its turn or needs your input.

- **Stop** (turn finished) → `sounds/stop.aiff`
- **Notification** (permission prompt / idle) → `sounds/notification.aiff`

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
            "command": "afplay \"/path/to/agent-sound/sounds/stop.aiff\" &"
          }
        ]
      }
    ],
    "Notification": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "afplay \"/path/to/agent-sound/sounds/notification.aiff\" &"
          }
        ]
      }
    ]
  }
}
```

If `settings.json` already has a `hooks` block, merge these entries in rather than replacing it. Open `/hooks` or restart Claude Code to pick up the changes.

## Customize the sounds

Replace `sounds/stop.aiff` or `sounds/notification.aiff` with any `.aiff`/`.wav`/`.mp3` file `afplay` can play. The defaults are copies of the macOS system sounds Glass and Funk from `/System/Library/Sounds/`.
