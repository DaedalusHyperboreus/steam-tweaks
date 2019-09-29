# Steam Tweaks

## What is it?
A set of tools that unlock various quality of life improvements for Steam on Linux with a particular focus on SteamOS and GamerOS.

## Installation
Install to Arch Linux from the AUR as `steam-tweaks`. Available by default on GamerOS.

## Usage
If you use GamerOS or steamos-compositor-plus and have steam-tweaks installed all the tools will run when the Steam session starts.
You can also invoke each script listed below manually with the command given in brackets. Alternatively, run the `steam-tweaks` convenience script which runs all the tools. The tools should be invoked when Steam is not running, otherwise any changes the tools make will be overwritten by Steam.

## The Tools
### Proton Whitelist (proton-whitelist)
Adds games to the proton whitelist in Steam according to the `proton-whitelist.vdf` file downloaded automatically from this repository and a user customized file found at `~/.config/proton-whitelist.vdf`.

### Steam Input Whitelist (steam-input-whitelist)
Enables Steam Input for games according to the `steam-input-whitelist.vdf` file downloaded automatically from this repository and a user customized file found at `~/.config/steam-input-whitelist.vdf`. This allows controllers to be recognized out of the box by the whitelisted games.

### Steam Grid Cache (steam-grid-cache)
Downloads and caches all Steam grid images for all available Steam accounts for use in offline mode.

### Steam Shortcuts (steam-shortcuts)
Reads yaml formatted shortcut definition files from `/usr/share/steam-shortcuts/` and `~/.local/share/steam-shortcuts/` and adds the shortcuts to all available Steam accounts.
NOTE: any existing shortcut data will be lost and replaced with shortcuts specified in the shortcut definition files.

#### Single shortcut per file example
```
name: Firefox                   # name of the shortcut as it will appear in Steam (required)
cmd: firefox                    # the command to execute (required)
dir: /full/path/to/working/dir  # the directory from which to execute the command
params: github.com              # any parameters to invoke the command with
image: /path/to/grid/image.png  # the grid image to use (this will by symlinked into Steam's grid directory)
icon: firefox                   # small icon to show in Steam
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
