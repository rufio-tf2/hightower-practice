# Hightower Practice

## Features

- Stationary bots to practice market gardening
- Teleport around using numpad 0-9 (numpad period `.` to return to spawn)
- Press `T` for Quick Action: reset you/bots for practicing jumps
- Control Quick Action using arrow keys LEFT, RIGHT, and DOWN
- Toggle `noclip` using arrow key UP

## API

- `echoCoords`
- `heal` (self)
- `healBots`
- `kickAllBots`
- `quickAction`: Repeat last teleport action
- `resetBots`: Kicks, re-adds, and teleports them
- `spawnAllBots`: Add bots

## Install & Use TL;DR

1. Install the scripts
1. Load hightower: `ht`
1. Load different "stages" (currently only two available): `htez` or `htog`
1. Numpad keys teleport you around the map
1. Use `T` (or change it) to use `quickAction` to repeat your last spawn, respawn the bots, or both
1. Control `quickAction` using the arrow keys LEFT, RIGHT, DOWN
1. Arrow key UP to toggle `noclip`

## Install

1. [Download](https://github.com/rufio-tf2/hightower-practice/archive/master.zip) this ZIP, extract it, and navigate into any outer `hightower-practice` folders until you see the inner `hightower-practice` folder, the `listenserver.cfg` file, and this `README.md` file.
1. Move the inner `hightower-practice` folder into your `tf/custom/YOUR_CONFIG/cfg/scripts` folder. If you don't have any of those folders, make them (you can call "YOUR_CONFIG" anything without spaces).
1. Move the `listenserver.cfg` file into your `tf/custom/YOUR_CONFIG/cfg` folder.
1. Wire-up the `scripts/hightower-practice/load.cfg` script in your `autoexec.cfg` file (located at `tf/custom/YOUR_CONFIG/cfg/autoexec.cfg`). Add this line anywhere:

   ```go
   // autoexec.cfg
   exec scripts/hightower-practice/load
   ```

### listenserver.cfg

If you already have a `listenserver.cfg` file you'll need to copy the contents of mine and paste it into yours.

## Use

Load hightower by entering `ht` into the console. Be patient while it loads:

```go
ht
// Loading Hightower. Please wait...
```

_Note: There's nothing special about the `ht` command. It's just an alias for `map plr_hightower`._

Once you're into the map, load one of the practice stages:

```go
htez
// or
htog
```

You can switch between these whenever you want. They change the bots' spawns (in order to practice different jumps).

**Join team RED**.

### Num Pad

The num pad teleports you around the map to practice different common jumps.

The num pad period key <kbd>.</kbd> (`KP_DEL`) will teleport you to the RED spawn.

- <kbd>1</kbd> and <kbd>4</kbd> spawn you on the BLU side
- The keys in the middle: <kbd>0</kbd>, <kbd>2</kbd>, <kbd>5</kbd>, and <kbd>8</kbd> spawn you around the hightower
- The keys on the right, <kbd>3</kbd>, <kbd>6</kbd>, and <kbd>9</kbd> spawn you on the RED side.
- <kbd>1</kbd> spawns on the red side for the montage jump

All of the keys respawn the bots to their starting locations.

### Quick Action

This script creates a `quickAction` that you can bind to a key. **By default `quickAction` is bound to <kbd>T</kbd>** `quickAction` by default teleports you to your last spawn (changed using the num pad keys) and it resets the bots health and locations.

#### Arrow Keys

You can use the arrow keys to control what `quickAction` does, or use `UPARROW` to toggle noclip:

- DOWNARROW: QA moves you and bots (default)
- LEFTARROW: QA only moves bots
- RIGHTARROW: QA only moves you
- UPARROW: `noclip` toggle

To change the key to which `quickAction` is bound, edit [quickAction.cfg](./base/quickAction.cfg). Change `T` to the [key of your choice](https://wiki.teamfortress.com/wiki/Scripting#List_of_key_names).

```go
// quickAction.cfg
bind T quickAction
```

### Defaults

This script usurps a lot of your key bindings:

- <kbd>T</kbd>
- <kbd>MOUSE1</kbd> (heals you with every fire)
- Num pad keys
- Arrow keys

You should update [defaults.cfg](./defaults.cfg) to return these keys to the default behavior that you want when not using this script.

For example, I use the <kbd>T</kbd> key to toggle my viewmodel.

```go
// defaults.cfg
bind T r_drawviewmodel
```

I use the arrow keys to switch loadouts. I use the num pad keys to switch classes. **If you use any of those keys in your normal gameplay, you'll need to set them to YOUR defaults.**

## Troubleshooting

If shit goes cray, try reloading the stage:

```go
htez
// or
htog
```

Or try resetting the bots using the `resetBots` command:

```go
resetBots
```
