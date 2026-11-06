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
- Optional **LibFights** integration: when the bundled `LibFights` library is installed, Console Metrics starts its logging and adds a LibFights panel (fight metrics, top abilities, crit/DR/resistance/TTK predictions) to both viewers.
- Optional debugging tools (live trace, build snapshot, set dump). These are heavy and meant for short debugging sessions only.

## Installation

The addon lives in the `ConsoleMetrics/` folder (manifest: `ConsoleMetrics/ConsoleMetrics.addon`, addon title "Console Metrics", APIVersion `101050`, saved variables `ConsoleMetricsSavedVars`).

1. Download or clone this repository.
2. Copy the inner `ConsoleMetrics/` folder (the one containing `ConsoleMetrics.addon` and `src/`) into your ESO `AddOns` directory.
   - PC: typically `Documents/Elder Scrolls Online/live/AddOns/`.
   - Console: the platform-specific method for loading custom addons is **not documented here** and is not determined by this repository.
3. Optional: also copy the `LibFights/` folder from this repository into the same `AddOns` directory to enable the LibFights panel and `/cm lf` commands.
4. Install the optional dependencies listed in the manifest if you need them: `LibConsoleDialogs` and `LibHarvensAddonSettings` (needed for the console viewer, `/cm view` reports an error without them), `LibAddonMenu-2.0`, `LMB`, `PvPCooldownTracker`, `LibFights`.
5. Enable the addon in the in-game Add-Ons menu and reload the UI.

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
| `/cm lf [status\|start\|stop\|view\|print\|all\|models\|next\|prev]` | LibFights controls: logging, open the LibFights panel, print reports and model predictions, browse LibFights fights |
| `/cm lf auto on\|off` | Start LibFights logging automatically on load (default on) |
| `/cm dumpsets`, `/cm debugbuild`, `/cm trace ...` | Debugging; trace output is heavy and can hurt performance |

Run `/cm help` in game for the authoritative, current list of commands.

## LibFights

[`LibFights/`](LibFights/README.md) is a separate library addon in this repository. It logs nothing until `Start_Logging()` is called. When it is installed, Console Metrics:

- starts LibFights logging on load (turn this off with `/cm lf auto off` or the "Start LibFights Logging" setting) and only stops a session it started itself;
- passes lighter options (no raw event log, no target effect tracking, 2s stat sampling) while Performance Mode is on, and restarts its session when Performance Mode changes;
- adds a **LibFights** panel to the console and PC viewers with the fight summary, top damage abilities and the library's predictions, plus start/stop, fight browsing and "print report" buttons.

Console Metrics' own fight tracking is unchanged and works the same without LibFights. Running both loggers costs extra CPU and memory, so on Series S consider Performance Mode or `/cm lf auto off`.

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
