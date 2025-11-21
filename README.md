# Scene Source Sequencer (SSS)

**Scene Source Sequencer (SSS)** is an OBS Lua script that automatically
displays specific sources in a scene **one after another**, using
configurable durations, gaps, cooldowns, and optional random triggers.

This script is ideal for rotating overlays, banners, widgets, images, or
any element you want to show sequentially in OBS.

Current version: **1.2.1**\
License: **MIT**

## Features

-   Sequential display of sources inside OBS scenes\
-   Per-source duration using the format `HH:MM:SS.mmm`\
-   Optional gap between each source\
-   Cooldown after each full sequence\
-   Random automatic trigger with probability control\
-   Manual hotkey to start a sequence\
-   Per-scene independent configuration\
-   Option: apply only to the currently active scene\
-   Built-in configuration UI inside OBS Script settings\
-   Flexible duration parsing (`00:00:06.000`, `1m30s`, `5s`, `750ms`,
    etc.)

## Installation

1.  Download the script file:\
    `scene_source_sequencer.lua`

2.  In OBS, open:\
    **Tools → Scripts**

3.  Click **+** and select the Lua file.

4.  Select the script in the left panel and configure each scene.

## Usage

### 1. Define the source list

Each line represents a source and the duration for which it should be
shown:

``` text
SourceName|00:00:06.000
AnotherSource|00:00:03.500
ThirdSource|00:00:05.250
```

-   `SourceName` must match exactly the name of the source in OBS.
-   Durations are always parsed into milliseconds.

You may also: - Select a source from the dropdown\
- Enter a duration\
- Click **Add** to append it to the list

### 2. Timing parameters

The script exposes the following timing fields for each scene:

-   **Gap between sources**\
    Delay after hiding one source and before showing the next.

-   **Cooldown after sequence**\
    Delay after the entire sequence completes.

-   **Random tick interval**\
    How often the script checks if it should randomly start a sequence.

-   **Random trigger chance (%)**\
    Probability that the sequence will start at each tick.

All timing fields accept multiple formats:

-   `HH:MM:SS.mmm` → `00:00:06.000`\
-   `MM:SS.mmm` → `01:30.500`\
-   `SS.mmm` → `05.250`\
-   Durations with tokens → `1h30m`, `20m`, `3s`, `750ms`, `1m20s`

### 3. Manual hotkey

To trigger the sequence manually:

1.  Open OBS → **Settings → Hotkeys**
2.  Search for: **"Start source sequence (SSS)"**
3.  Assign any key combination (e.g. `Ctrl + Shift + S`)

Pressing the hotkey starts the sequence immediately.

## Example use cases

-   Rotate sponsor banners or social media panels\
-   Show multiple overlay widgets in sequence\
-   Custom slideshow with precise timing\
-   Cycle through animated sources during live scenes\
-   Display periodic info panels (rules, tips, commands, etc.)

## Technical notes

-   Scheduler runs every **100 ms** via `obs.timer_add`\
-   Each scene is configured individually\
-   All sequence sources are hidden before the first appears\
-   "Only affect active scene" ensures only the current scene is
    processed\
-   No external files are written; all config is stored in OBS

## Files

-   `scene_source_sequencer.lua` --- main script\
-   `LICENSE` --- MIT license

## License

This project is released under the **MIT License**.\
See the `LICENSE` file for details.

## Contributing

Bug reports, feature ideas, and pull requests are welcome.
