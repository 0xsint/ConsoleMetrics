# Console Metrics

Combat metrics for The Elder Scrolls Online, built for **console and gamepad** first and also usable on PC.
Console Metrics records your fights and shows them in a fight viewer: DPS and HPS, damage taken, per-ability
breakdowns, buff and debuff uptimes, set procs, resources and ping, resistance and damage-reduction estimates,
your build, and a Combat Metrics style full fight report.

- **Author:** Vixen Hunny
- **Version:** 1.1.0
- **API version:** 101050

---

## Contents

- [Requirements](#requirements)
- [Installation](#installation)
- [Opening the fight viewer](#opening-the-fight-viewer)
- [Gamepad / console viewer](#gamepad--console-viewer)
- [PC window](#pc-window)
- [Pages](#pages)
- [Full Fight Report (LibFights)](#full-fight-report-libfights)
- [Saved fights](#saved-fights)
- [Settings](#settings)
- [Chat commands](#chat-commands)
- [Performance notes](#performance-notes)
- [Troubleshooting](#troubleshooting)
- [File layout](#file-layout)

---

## Requirements

Console Metrics has no required dependencies. These optional add-ons unlock extra features:

| Add-on | What it adds |
|---|---|
| **LibFights** | The **Full Fight Report**: damage and healing done and received by unit and ability, buffs and debuffs with stacks, resources by source, stats, graph, combat log, casts, deaths, posting to chat and a fight list. |
| **LibHarvensAddonSettings** | The settings page in the gamepad / console add-on settings menu. |
| **LibAddonMenu-2.0** | The settings page on PC (keyboard UI). |
| **LibConsoleDialogs** | A **Console Metrics** button on the keybind strip of the Journal screens. |
| **PvPCooldownTracker** | Import of its set data as Console Metrics custom set rules. |
| **LMB** (Link My Bars) | Richer skill / champion / gear links when sharing your build to chat. |

The gamepad fight viewer itself needs none of these; it is a screen of its own.

## Installation

1. Copy the `ConsoleMetrics` folder into your `AddOns` folder:
   - PC: `Documents\Elder Scrolls Online\live\AddOns\` (or `pts\AddOns\` for the test server)
   - Console: install through the in-game add-on manager.
2. Optionally install LibFights and the other libraries listed above.
3. Enable the add-ons in the add-on menu and log in (or `/reloadui`).

## Opening the fight viewer

| Where | How |
|---|---|
| Gamepad main menu | **Journal → Console Metrics** |
| Journal screens | **Console Metrics** keybind button (needs LibConsoleDialogs) |
| Add-on settings | **Console Metrics → Open Fight Viewer** |
| Chat (PC) | `/cm view` |

On PC, `/cm view` opens the gamepad viewer while the gamepad UI is active and the PC window otherwise.
If the Journal entry is missing, `/cm inject` retries adding it.

## Gamepad / console viewer

The viewer is a gamepad list screen with the page name and the viewed fight's numbers in the header, details
for the selected row in the left tooltip panel, and these controls:

| Button | Action |
|---|---|
| **A** | Run the selected row (the keybind strip says what it does: Open, Toggle, Post, …) |
| **B** | Back one page; on the Main Menu, close the viewer |
| **Y** | Main Menu (from any page) |
| **X** | Live: jump back to the current fight |
| **LB / RB** | Older / newer fight |

- Every page has a **Back** row at the top and bottom; deeper pages also have a **Main Menu** row, and the
  Main Menu has **Close**.
- Back follows your page history, so it always returns to the page you came from.
- The list refreshes live during combat, keeping the cursor on the same row; refreshes pause for two seconds
  after you move or press a button so presses land on the row you aimed at.
- On Full Fight Report pages, LB / RB / X step through **LibFights** fights instead of Console Metrics history.

## PC window

A keyboard / mouse window styled after the base-game UI: category list on the left, content on the right, and
a footer with **Previous / Next / Live** and **Save Fight**. ESC closes it. It does not auto-close while the
cursor is over it, and it reopens on the page you had open.

## Pages

| Page | Shows |
|---|---|
| **Main Menu** | Fight summary (damage, healing, taken, crit, duration, FPS) and links to every page |
| **Overview** | Totals, hit range, peak DPS / HPS, burst windows |
| **Abilities** | Damage and healing per ability (hits, crit %, max) |
| **Buffs & Sets** | Major / Minor uptimes and tracked set procs |
| **Mitigation & Healing** | Blocked and shielded damage, top healing and mitigation moments |
| **Resistance** | Resistance and damage-reduction estimates, inferred Major / Minor Protection |
| **Resources** | Health / Magicka / Stamina averages, regen and drain, ultimate, ping dips and spikes |
| **Build** | Action bars, gear, sets, mundus, champion points |
| **Behavior Model** | Predicted next DPS / HPS / damage taken and resistance from your fight history |
| **LibFights** | LibFights summary and model predictions (when LibFights is installed) |
| **Formulas** | ESO stat math used by the add-on |
| **Share to Chat** | Fight stats, top skills, sustain and build links |
| **Saved Fights / Save Fight** | Keep fights across sessions, load or delete them |
| **Options** | Auto hide, auto hide delay, jump to live on new fight, clear data, help |

## Full Fight Report (LibFights)

**Main Menu → Combat Metrics Report → Full Fight Report** opens a Combat Metrics style report built from the
fight LibFights recorded. LibFights must be installed and logging; the report offers a **Start LibFights
Logging** button, and the **Start LibFights Logging** setting starts it at every login.

| Page | Contents |
|---|---|
| **Damage Done** | Total (normal / crit / DoT / direct), DPS, active DPS, boss DPS, crit rate, blocked, shielded, overkill; targets; ability table (Total, %, DPS, Hits, Crit %, Avg, Avg Normal, Avg Crit, Max, Min, ticks); damage types |
| **Damage Received** | Incoming DPS, blocked, shielded, mitigated (shield / block / armor / avoid), dodges, misses; attackers; abilities; damage types |
| **Healing Done** | HPS, HPS + overheal, overheal %, self healing, crit; heal targets; abilities |
| **Healing Received** | Incoming HPS, shields gained; healers; abilities |
| **Buffs & Debuffs** | Buffs on you and debuffs you applied: uptime, gains, max stacks; procs per minute |
| **Resources** | Magicka / Stamina / Health / Ultimate gained and spent, averages, time at zero, top sources |
| **Stats & Performance** | Spell / weapon damage, crit, penetration, resistances (average and max), crit damage, target resistance, missing and over-penetration, FPS, ping |
| **Graph** | Damage, healing, damage taken or shield absorbed over the fight; boss health and time to kill |
| **Combat Log** | Every recorded event with filters, 25 per page |
| **Skills & Casts** | Casts, APM, light-attack weaving, time between skills, bar time, casts per ability, bars |
| **Deaths** | Each death with the hits before it |
| **Post to Chat** | Single-target, boss, total DPS, HPS and buff uptime lines |
| **Fight List** | Recent and saved LibFights fights: view, save, delete |

Not covered: group members' numbers, status-effect proc counts and skill desync (LibFights does not record them).

## Saved fights

- **Save This Fight** (Main Menu, or the PC footer) stores the viewed fight in a saved slot, kept across sessions
  (`maxSavedFights`, default 10).
- **Saved Fights** loads a slot into the fight history or deletes it.
- Saved fights are restored into history on login.
- On the gamepad viewer the save name is generated automatically (text entry is not available there);
  on PC you can type a name, or use `/cm savefight <name>`.

## Settings

Available in the add-on settings menu (LibHarvensAddonSettings / LibAddonMenu-2.0) and partly in the viewer's
**Options** page.

| Section | Option |
|---|---|
| General | Auto Clear on Next Fight, Max Fight History |
| Fight Dialog | Dialog Auto Hide, Auto Hide Delay (seconds), Open Fight Viewer |
| Performance | Performance Mode, Low Memory Mode |
| Behavior Model (ML) | Enable Behavior Model, Model Refresh (ms) |
| LibFights | Start LibFights Logging (turns LibFights logging on now and at every login) |
| Actions | Apply Performance Preset, Clear All Fight Data |
| Custom Set Rules | Import PvPCooldownTracker Rules, Clear Custom Set Rules |

Dialog auto hide waits while you are using the viewer and only closes it after the delay passes without input.

## Chat commands

`/cm` and `/consolemetrics` are the same. Chat commands are PC only; on console use the viewer and settings.

| Command | Description |
|---|---|
| `/cm help` | List all commands |
| `/cm view` | Open the fight viewer |
| `/cm close` | Close the viewer |
| `/cm settings` | Open the settings panel |
| `/cm prev` / `/cm next` | Previous / next fight in history |
| `/cm clear` | Clear live fight data and history |
| `/cm savefight [name]` | Save the viewed fight |
| `/cm loadfight <name>` | Load a saved fight by name |
| `/cm loadfightexact <name>` | Load a saved fight by exact name |
| `/cm loadsaves` | Load all saved fights into history |
| `/cm share [fight\|build\|skills\|sustain\|all]` | Pre-fill chat with stats or your build |
| `/cm linkbuild` | Pre-fill chat with a compact build summary |
| `/cm autoclear on\|off` | Jump back to live when a new fight starts |
| `/cm autohide on\|off` | Auto close the viewer after combat |
| `/cm perf on\|off\|status` | Console performance preset |
| `/cm lf [status\|start\|stop\|view\|print\|all\|models\|next\|prev\|auto on\|off]` | LibFights controls |
| `/cm importpct` | Import custom set rules from PvPCooldownTracker |
| `/cm addset <label>\|<scene>\|<abilityId>\|<abilityName>` | Add a custom set matcher |
| `/cm clearsets` | Remove all custom set rules |
| `/cm inject` | Retry the Journal menu / keybind integration |
| `/cm reset` | Reset options (keeps saved fights and set rules) |
| `/cm debug on\|off` | Diagnostic chat output |
| `/cm debugbuild` | Print build snapshot details |
| `/cm dumpsets` | Dump item sets and observed ability IDs |
| `/cm dumpcpslottables` | Dump champion slottable IDs |
| `/cm trace …` | Live event / resource trace (`on\|off`, `mode`, `target`, `focus`, `samples`, `min`, `cap`, `summary`, `status`) |

> Trace logging is expensive on console. Keep it short and turn it off with `/cm trace off`.

## Performance notes

- **Performance Mode** lowers refresh rates and trims what LibFights records (no raw events, no target
  effects), so the Combat Log and Debuffs Out pages stay empty while it is on.
- **Low Memory Mode** trims stored fight history lists.
- The gamepad viewer refreshes at most every 1.5 s and pauses while you navigate.

## Troubleshooting

| Problem | What to do |
|---|---|
| No Console Metrics entry in the Journal | Wait a few seconds after loading in, or `/cm inject`; use the settings button otherwise |
| Full Fight Report says "Needs LibFights" | Install and enable LibFights |
| Full Fight Report says "LibFights is not logging" | Press **Start LibFights Logging** on that page, or turn on **Start LibFights Logging** in the settings so it starts at every login |
| Combat Log is empty | Turn off Performance Mode (it disables LibFights raw events) |
| Chat shows "Fight viewer: row label not found …" | Report the message; it lists the row template's controls |
| Chat shows "Could not create the gamepad fight viewer: …" | Report the message; the viewer falls back to the PC window on PC |
| A page shows "This page failed to build." | The tooltip on that row has the error; report it |

New or changed XML files are only loaded after `/reloadui` or a game restart.

## File layout

```
ConsoleMetrics/
├── ConsoleMetrics.addon             manifest
├── README.md
└── src/
    ├── ConsoleMetrics_Core.lua          namespace, defaults, constants, helpers
    ├── ConsoleMetrics_Build.lua         action bars, gear, sets, boons
    ├── ConsoleMetrics_Champion.lua      champion points
    ├── ConsoleMetrics_Sets.lua          set catalog, proc classification, custom rules
    ├── ConsoleMetrics_FightData.lua     fight model, summaries, history, saved fights, behavior model
    ├── ConsoleMetrics_Combat.lua        combat event processing and trace
    ├── ConsoleMetrics_Chat.lua          chat sharing (links and text)
    ├── ConsoleMetrics_LibFights.lua     optional LibFights bridge
    ├── ConsoleMetrics_Dialog.lua        viewer pages and shared open / close / refresh
    ├── ConsoleMetrics_DialogCMX.lua     Full Fight Report pages (LibFights)
    ├── ConsoleMetrics_GamepadScreen.xml top-level template for the gamepad viewer
    ├── ConsoleMetrics_GamepadScreen.lua gamepad viewer screen, page history, keybinds
    ├── ConsoleMetrics_PCDialog.lua      PC window
    ├── ConsoleMetrics_Integration.lua   Journal menu and keybind integration
    ├── ConsoleMetrics_Debug.lua         diagnostic dumps
    ├── ConsoleMetrics_Settings.lua      settings schema and menu
    ├── ConsoleMetrics_Commands.lua      /cm commands
    └── ConsoleMetrics_Init.lua          startup, events, update loop
```

`ConsoleMetrics_UIInit.lua` is an older file that is not loaded by the manifest.
