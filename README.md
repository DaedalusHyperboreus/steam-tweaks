# Steam Tweaks

## What is it?
A set of tools that unlock various quality of life improvements for Steam on Linux with a particular focus on SteamOS and GamerOS.

## Installation
On Arch Linux, install `steam-tweaks` from the AUR. On GamerOS, the package is pre-installed.

## Usage
If you use GamerOS or use `steamos-compositor-plus` and have `steam-tweaks` installed all the tools will run automatically when the Steam session starts.

You can also invoke each script listed below manually with the command given in brackets. Alternatively, run the `steam-tweaks` convenience script which runs all the tools. The tools should be invoked when Steam is not running. Any changes the tools make while Steam is running will be overwritten by Steam.

## The Tools
### Steam Config (steam-config)
Configures Steam games according to the automatically downloaded configuration file, or the local override file if found at `~/.config/steam-tweaks.yaml`.

Extends Valve's Steam Play/Proton whitelist, specifying the compatibility tool, launch options and whether Steam Input is enabled on a per-game basis. Many games are already configured to work out of the box, with more being added over time. Please help by testing the games you own and submitting your configurations.

#### Options
 - **compat_tool**: the compatibility tool to be used for the specified game, e.g. `proton_42`, `steamlinuxruntime`
 - **compat_config**: the configuration for the compatibility tool specified, e.g. for proton: `d9vk`, `noesync`, etc; see the [Proton docs](https://github.com/ValveSoftware/Proton#runtime-config-options) for the full list of available options
 - **launch_options**: the launch options to be used
 - **steam_input**: a value of `enabled` will force the use of Steam Input for the specified game

#### Example
```
"321040":
  compat_tool: proton_411
  compat_config: noesync
  launch_options: MY_VARIABLE=1 %command%
  steam_input: enabled
```

Each game is specified by its Steam app id. Note that the app id MUST be quoted.

### Steam Shortcuts (steam-shortcuts)
Reads one or more YAML formatted shortcut definition files stored under `/usr/share/steam-shortcuts/` or `~/.local/share/steam-shortcuts/` and adds the shortcuts to all available Steam accounts.
NOTE: any existing shortcut data will be lost and replaced with shortcuts specified in the shortcut definition files.

#### Single shortcut per file example
```
name: Firefox                   # name of the shortcut as it will appear in Steam (required)
cmd: firefox                    # the command to execute (required)
dir: /full/path/to/working/dir  # the directory from which to execute the command
params: github.com              # any parameters to invoke the command with
banner: /path/to/image.png      # the grid banner image to use (this will be symlinked into Steam's grid directory)
icon: firefox                   # small icon to show in Steam
compat_tool: proton_411         # use the given compatibility tool, useful for running Windows executables
compat_config: noesync          # use the given compatibility tool options
hidden: false                   # 'false' to show the shortcut in Steam, 'true' to hide it
tags:                           # a list of tags to be assigned to the shortcut in Steam
  - Browser
  - Custom Shortcut
```

#### Multiple shortcuts per file example
```
- name: Firefox
  cmd: firefox
  ...
- name: Chromium
  cmd: chromium
  ...
```
