<p align="center">
  <img src="docs/hero.png" alt="RuneMonitor" width="520" />
</p>

Watches your bot client's log folder and sends you a Discord message when something worth
knowing happens — a level milestone, the script pausing or dying, a valuable drop, someone
talking to your bot, or the bot going quiet.

It reads log files and nothing else. It never touches the game, never types, never clicks.

![Overview](docs/overview.png)

## What it does

**Reads any client's logs.** The file pattern, the line format and the wording it looks for are
all settings. Four line shapes work out of the box — `2026-08-18 11:37:31 [INFO] text`,
`[11:37:31] INFO text`, `11:37:31 INFO - text` and ISO timestamps — and a line matching none of
them still shows up, stamped with its arrival. Rotated copies (`.log.1`, `.log.2026-08-19`,
`.log.gz`) are skipped.

**Classifies instead of grepping.** Every line becomes one of ten event types — task, level up,
chat, error, drop, death, quest, script, break, system — with the skill, level and coin value
pulled out of it.

**Routes each type on its own.** Per type: whether it notifies at all, whether it carries a
screenshot of the client window, whether it pings you, and which Discord channel it lands in.

**Knows a 99 from a 43.** Notify every Nth level, never below a floor, and a milestone list that
overrides both — so 99s always arrive while the grind stays quiet.

**Notices when nothing happens.** A watchdog fires when an account stops writing lines at all,
which is what a crashed, stuck or logged-out bot looks like from the outside.

**Screenshots the client**, even when its window is behind something else, and attaches the
image to the alert. A failed capture never suppresses the alert.

**Tracks several accounts at once**, discovered as their logs appear — one folder per account or
one flat folder, both work.

**Keeps history on disk** so restarts do not lose it, and charts levels per day and per skill.

**Drops are filtered by worth.** A bot killing for hours drops the same 20k rune over and over,
so a coin floor decides which ones reach Discord. Untradeables carry no price and have their own
switch.

**Players follow themselves.** A character found on a running client is tracked on Wise Old Man
automatically, and the Players view re-reads the hiscores whenever you open it: hours to max,
total level, and the skills closest to 99.

**Dry run by default.** Everything is classified and shown, nothing is sent, until you turn it
off.

**English only.** There is no language setting, and numbers, dates and dialogs stay English on a
machine set to any other language.

## Install

1. Download `RuneMonitor-vX.Y.Z.zip` from the [latest release](../../releases/latest).
2. Unzip it anywhere and run `RuneMonitor.exe`.
3. Windows 10 and 11 already have what it needs. Nothing is installed; it writes only to
   `%APPDATA%\RuneMonitor`.

## First run

1. It offers the log folder of whichever client it finds — DreamBot, OSBot, TRiBot, RuneLite,
   Microbot or Powbot. Use **Browse** for anything else.
2. Under **Settings**, paste a Discord webhook URL and press **Send test message**.
   (Discord: Server Settings → Integrations → Webhooks → New Webhook → Copy URL.)
3. Leave **Dry run** on until the event stream shows the right lines firing on the right events.
4. Turn dry run off to go live.

![Settings](docs/settings.png)

## Players

Characters found on running clients are followed on Wise Old Man without being typed in. Opening
the view re-reads the hiscores, so the numbers are current: hours to max, total level, how many
99s are done, and the skills closest to finishing, ordered by the experience actually left.

![Players](docs/players.png)

## Accounts

State, how long each account has been silent, levels and errors so far, and which window title
its screenshots come from.

![Accounts](docs/accounts.png)

## Stats and history

Levels per day and per skill, merged from the running session and everything recorded earlier.

![Stats](docs/stats.png)

History is written as one file per account per day and stays searchable after a restart.

![History](docs/history.png)

## Tuning it to your client

Game messages — levels, drops, deaths, chat — are written by the game itself, so those patterns
work in every client. The task, activity and script lifecycle lines come from your client or
script, and those live under **Settings → Client profile**: edit the pattern, or press **Reset
to defaults** if an edit goes wrong.

**Custom rules** cover anything the classifier does not: a substring or a regular expression, an
optional numeric threshold, a per-account cooldown, its own message and channel. **Replay a log
file** runs an existing log through those rules and reports what would have fired, without
sending anything.

## Updates

Each launch asks this repository for the newest release and offers you the download page if it
is newer. Nothing is downloaded or installed behind your back, and the check stays silent when
GitHub is unreachable.
