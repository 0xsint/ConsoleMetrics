# ConsoleMetrics

ConsoleMetrics is a console-friendly combat metrics addon ("CMX"-style) for **The Elder Scrolls Online** that records fight data and shows it in an in-game viewer. It is written in **Lua** and licensed under **GPL-3.0**.

> **Note:** ConsoleMetrics is unstable on **Xbox Series S**.

## Features

Based on the addon source in this repository:

- Records live fight data from combat events and keeps a history of past fights.
- Fight viewer dialog:
  - Console/gamepad: uses `LibConsoleDialogs` and `LibHarvensAddonSettings`.
  - PC (keyboard/mouse): a scrollable window.
- Browse previous fights (`/cm next`, `/cm prev`) and clear history (`/cm clear`).
- Chat sharing of results (skills and gear are sent as clickable ESO links).
- A Journal menu entry for opening the viewer (injected on load; `/cm inject` re-applies it).
- A "Performance Mode" preset intended for lower-memory consoles such as the Series S.
- Optional debugging tools (live trace, build snapshot, set dump). These are heavy and meant for short debugging sessions only.

## Installation

The addon lives in the `ConsoleMetrics/` folder (manifest: `ConsoleMetrics/ConsoleMetrics.addon`, addon title "Console Metrics", APIVersion `101050`, saved variables `ConsoleMetricsSavedVars`).

1. Download or clone this repository.
2. Copy the inner `ConsoleMetrics/` folder (the one containing `ConsoleMetrics.addon` and `src/`) into your ESO `AddOns` directory.
   - PC: typically `Documents/Elder Scrolls Online/live/AddOns/`.
   - Console: the platform-specific method for loading custom addons is **not documented here** and is not determined by this repository.
3. Install the optional dependencies listed in the manifest if you need them: `LibConsoleDialogs` and `LibHarvensAddonSettings` (needed for the console viewer, `/cm view` reports an error without them), `LibAddonMenu-2.0`, `LMB`, `PvPCooldownTracker`.
4. Enable the addon in the in-game Add-Ons menu and reload the UI.

## Usage

Once loaded, the addon prints a message in chat. Use `/cm` or `/consolemetrics`:

| Command | Description |
| --- | --- |
| `/cm` or `/cm help` | Show help |
| `/cm view` (or `menu`) | Open the fight viewer |
| `/cm close` | Close the viewer |
| `/cm next` / `/cm prev` | Step through fight history |
| `/cm clear` | Clear fight history and live data |
| `/cm autoclear on\|off` | Clear data automatically on the next fight |
| `/cm autohide on\|off` | Auto-hide the dialog |
| `/cm perf on\|off\|status` | Performance Mode (applies a Series S preset) |
| `/cm inject` (or `journal`) | Re-apply the Journal menu entry |
| `/cm dumpsets`, `/cm debugbuild`, `/cm trace ...` | Debugging; trace output is heavy and can hurt performance |

Run `/cm help` in game for the authoritative, current list of commands.

## Known limitations / compatibility

- **Unstable on Xbox Series S.** Try `/cm perf on` and avoid the trace/debug commands.
- The console viewer requires `LibConsoleDialogs` and `LibHarvensAddonSettings`.
- Built against ESO APIVersion `101050`; other game versions are untested.
- Console installation steps and any screenshots/example output are unknown/not provided.

## Repository

- **Repository:** `0xsint/ConsoleMetrics`
- **Language:** Lua
- **Author (per addon manifest):** Vixen Hunny
- **License:** GNU General Public License v3.0 (see `LICENSE`)
