<p align="center">
  <img src="assets/icon.png" width="128" height="128" alt="Claude Profiles icon">
</p>

<h1 align="center">Claude Profiles</h1>

<p align="center">
  Desktop app for managing several Claude Code accounts on one Mac: profiles,
  live sessions, plan usage limits, startup context, memory, skills, settings and MCP servers in one place.
</p>

<p align="center">
  <a href="https://github.com/e-nagornyak/claude-profiles-releases/releases/latest"><img src="https://img.shields.io/github/v/release/e-nagornyak/claude-profiles-releases?label=latest&color=6366f1" alt="Latest release"></a>
  <img src="https://img.shields.io/badge/platform-macOS-111111" alt="Platform: macOS">
  <a href="https://github.com/e-nagornyak/claude-profiles-releases/releases"><img src="https://img.shields.io/github/downloads/e-nagornyak/claude-profiles-releases/total?color=111111" alt="Downloads"></a>
</p>

<p align="center">
  <a href="https://github.com/e-nagornyak/claude-profiles-releases/releases/latest"><b>⬇ Download the latest version</b></a>
  &nbsp;·&nbsp;
  <a href="https://github.com/e-nagornyak/claude-profiles-releases/releases">All releases</a>
</p>

---

## What it does

Each Claude Code profile is a `CLAUDE_CONFIG_DIR` plus a command, e.g. `claude` → `~/.claude`,
`claude-work` → `~/.claude-work`. Claude Profiles finds the profiles you already have and
shows everything about each of them side by side.

## Features

- 👤 **Profiles found automatically** — `~/.claude`, `~/.claude-*` folders and
  `CLAUDE_CONFIG_DIR=… claude` aliases in zsh, bash and fish
- 📊 **Plan usage limits** like `/usage`: current session, weekly limits, extra usage,
  and all profiles compared
- 🔔 **Menu bar item** with session and weekly use, plus notifications at 80% and 100%
- 🟢 **Live sessions** per profile with resume commands
- 🥧 **Startup context** — what a session sends before Claude's first reply: system prompt,
  built-in tools, MCP servers, skills, agents, CLAUDE.md, rules and memory, in tokens against
  the model's context window and what stays free. For the whole profile and for each project
- 🎛️ **What sets each part's size** — pick a part on the chart to see the least and the most it
  can take, what it got and what it's allowed, and change it:
  - **Skills**: the skill listing budget (1% of the window by default; with many skills Claude Code
    drops descriptions, and the app shows which), the description limit, each skill listed,
    by name only, only as `/name` or off, and the skills that ship with Claude Code
  - **MCP servers**: tool definitions loaded on demand, while they fit in a share of the window,
    or always; claude.ai connectors; each server on or off in a project
  - **Built-in tools, system prompt, CLAUDE.md and rules, memory**: the Artifact and SendFeedback
    tools, commit and PR instructions, single instruction files, auto memory and the MEMORY.md cut-off
  - Changes save to the profile or to a project's own settings, and the chart previews them first
- 📈 **Recent sessions** — how the startup context grew or shrank, and which part moved
- 🧠 **Memory, CLAUDE.md, rules, skills, agents, commands and output styles**, all editable
- ⚙️ **settings.json, plugins, MCP servers and connectors**
- 📁 **Projects** across all profiles with their Claude files and token usage
- 🔐 **Login, logout and `claude setup-token`** in a built-in terminal
- 🔄 **Automatic updates**

## Download

| File | Requirements |
| --- | --- |
| `Claude-Profiles-<version>.dmg` — disk image | macOS 10.13+, Intel or Apple Silicon |

Get it from the **[latest release](https://github.com/e-nagornyak/claude-profiles-releases/releases/latest)**.

## Installation

1. Open the `.dmg` and drag **Claude Profiles** into **Applications**.
2. Launch it. The app is not signed or notarized by Apple, so macOS blocks the first launch
   with *“Apple could not verify ‘Claude Profiles.app’ is free of malware”*.
   Click **Done** — **not** *Move to Trash*.
3. Allow it in one of two ways:

   **System Settings**
   1. Open **System Settings → Privacy & Security** and scroll down to **Security**.
   2. Next to *“Claude Profiles.app was blocked…”* click **Open Anyway** and confirm with
      your password or Touch ID.
   3. Launch the app again and click **Open**.

   **Terminal**

   ```bash
   xattr -dr com.apple.quarantine "/Applications/Claude Profiles.app"
   ```

   After that the app opens normally.

This is needed only the first time.

On first use macOS may ask to let Claude Profiles read the Keychain item
`Claude Code-credentials` — that is how it reads plan usage with each profile's own login.
Click **Always Allow**. After an update macOS may ask once more.

## Updates

The app checks this repository on launch and every 6 hours. When a new version is out,
an update button appears at the bottom of the sidebar: **Install and restart** downloads it,
replaces the app and restarts it.

To check manually, use **Check for Updates…** in the menu bar item.

## Troubleshooting

### Update fails with *“Read-only file system (os error 30)”*

The error names a path with `AppTranslocation` in it. macOS runs an app that came from the
internet and wasn't moved with Finder from a temporary **read-only** copy (App Translocation),
so the update can't replace it. It happens when the app is opened straight from the `.dmg` or
from Downloads, or was copied into Applications some other way than dragging in Finder.

1. Quit Claude Profiles (**⌘Q**) and eject the `.dmg` if it's mounted.
2. In Finder, drag **Claude Profiles** into **Applications** (replace the old copy if asked).
3. Remove the quarantine flag:

   ```bash
   xattr -dr com.apple.quarantine "/Applications/Claude Profiles.app"
   ```

4. Open it from **Applications** and click **Install and restart** again.

To check, `xattr "/Applications/Claude Profiles.app"` should no longer list
`com.apple.quarantine`. If the update still fails, download the latest `.dmg`, drag the app
into Applications over the old one and run step 3 — your profiles and settings stay as they are.

### macOS says the app can't be verified

See step 3 of [Installation](#installation): **Open Anyway** in Privacy & Security, or the
same `xattr` command.

## Good to know

- Closing the window keeps the app in the menu bar; **⌘Q** quits.
- Profile commands are small scripts in `~/.local/bin`, so they work in any shell.
- Deletions go to the Trash, and removing a profile never deletes its folder.

---

<sub>This repository hosts release builds only; the source code is private.</sub>
