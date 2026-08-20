# RuneMonitor

Watches your bot client's log folder and sends you a Discord message when something worth
knowing happens — a level milestone, the script pausing or dying, a valuable drop, someone
talking to your bot, or the bot going quiet.

It reads log files and nothing else. It never touches the game, never types, never clicks.

## Install

1. Download `RuneMonitor-vX.Y.Z.zip` from the [latest release](../../releases/latest).
2. Unzip it anywhere and run `RuneMonitor.exe`.
3. Windows 11 and 10 already have everything it needs. The app is not installed and writes only
   to `%APPDATA%\RuneMonitor`.

## First run

1. It offers the log folder of whichever client it finds — DreamBot, OSBot, TRiBot, RuneLite,
   Microbot or Powbot. Use **Browse** for anything else.
2. Under **Settings**, paste a Discord webhook URL and press **Send test message**.
   (Discord: Server Settings → Integrations → Webhooks → New Webhook → Copy URL.)
3. Leave **Dry run** on until the event stream shows the right lines. Turn it off to go live.

## Works with any client

The log file pattern, the line format and the wording the app looks for are all settings. Game
messages — levels, drops, deaths, chat — read the same in every client, so those work out of the
box; the task and lifecycle lines your client or script writes can be adjusted under
**Settings → Client profile** without waiting for a new build.

## Updates

Each launch checks this repository for a newer release and offers you the download page. Nothing
is downloaded or installed behind your back, and the check is silent when GitHub is unreachable.
