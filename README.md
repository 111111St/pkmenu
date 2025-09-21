# pkmenu

A PolicyKit agent for window managers, supporting dmenu-compatible launchers for prompts.  
Written entirely in POSIX shell for portability.  
Originally based on [czaplicki/rofi-polkit-agent](https://github.com/czaplicki/rofi-polkit-agent)

## Supported launchers

* [`dmenu`](https://tools.suckless.org/dmenu/) ([password patch](https://tools.suckless.org/dmenu/patches/password/) recommended!)
* [`rofi`](https://github.com/davatorium/rofi)
* [`fuzzel`](https://codeberg.org/dnkl/fuzzel)

## Requirements

* A POSIX-compliant shell (`sh`)
* Any of the three supported launchers
* [`cmd-polkit`](https://github.com/OmarCastro/cmd-polkit)
* `jq`

## Installation

To install, just copy the `pkmenu` script into a location in `$PATH`:
```sh
$ chmod +x pkmenu
$ sudo cp pkmenu /usr/local/bin/
```

## Usage

Basic example:
```sh
# start pkmenu with dmenu as launcher
$ pkmenu -l dmenu
```

Whenever PolicyKit triggers a password authentication, your chosen launcher will prompt you to enter your user password.

Additional arguments to the launcher can be passed with the `-a` option:
```sh
# start pkmenu using fuzzel with red prompt colour and DejaVu Sans Mono font
$ pkmenu -l fuzzel -a "--prompt-color=ff0000ff --font='DejaVu Sans Mono'" 
```

### Autostart

On most systems, you can place `pkmenu.desktop` into your local XDG autostart folder, or you can start the agent
from your init script (`.xinitrc` or WM config)

**Make sure to replace `dmenu` in `pkmenu.desktop` with a launcher you have installed on your computer**

