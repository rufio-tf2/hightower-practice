# Hightower Practice

Place stationary bots around Hightower to practice market gardening.

**Join team RED**.

## API

- `tp_1` - `tp_9`: Teleport to different locations around the map
- `tp_spawn`: Teleport to Red spawn
- `heal` (self)
- `healBots`
- `kickAllBots`
- `resetBots`: Kicks, re-adds, and teleports them
- `spawnAllBots`: Add bots
- `quickAction`: Repeat last teleport action
- `echoCoords`

## TL;DR

1. Install the scripts
1. Load Hightower: `ht`
1. Load different stages (currently only two available): `htez` or `htog`

## Install

1. [Download](https://github.com/rufio-tf2/hightower-practice/archive/master.zip) this ZIP, extract it, and navigate into any outer `hightower-practice` folders until you see the inner `hightower-practice` folder, the `listenserver.cfg` file, and this `README.md` file.
1. Move the inner `hightower-practice` folder into your `tf/custom/YOUR_CONFIG/cfg/scripts` folder. If you don't have any of those folders, make them (you can call "YOUR_CONFIG" anything without spaces).
1. Move the `listenserver.cfg` file into your `tf/custom/YOUR_CONFIG/cfg` folder.
1. Wire-up the `scripts/hightower-practice/load.cfg` script in your `autoexec.cfg` file (located at `tf/custom/YOUR_CONFIG/cfg/autoexec.cfg`). Add this line anywhere:

   ```go
   // autoexec.cfg
   exec scripts/hightower-practice/load
   ```

   Note that this doesn't make any changes, it just enables the stage aliases (`htez` and `htog`). Loading a stage makes changes.

### listenserver.cfg

If you already have a `listenserver.cfg` file you'll need to copy the contents of mine and paste it into yours.

## Use

Load Hightower by entering `ht` into the console. Be patient while it loads:

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

## Binds

Enter `ht_binds` to initialize binds. **Careful!** You'll want to go to `defaults.cfg` to ensure you are resetting the binds to whatever you want them to be outside of using this script.

- Teleport around using numpad 0-9 (numpad period `.` to return to spawn)
- Press `T` for Quick Action: reset you/bots for practicing jumps
- Control Quick Action using arrow keys LEFT, RIGHT, and DOWN
- Toggle `noclip` using arrow key UP

### Numpad

_No numpad? See [below](#no-numpad)._

The numpad teleports you around the map to practice different common jumps.

The numpad period key <kbd>.</kbd> (`KP_DEL`) will teleport you to the RED spawn.

- <kbd>1</kbd> and <kbd>4</kbd> spawn you on the BLU side
- The keys in the middle: <kbd>0</kbd>, <kbd>2</kbd>, <kbd>5</kbd>, and <kbd>8</kbd> spawn you around the Hightower
- The keys on the right, <kbd>3</kbd>, <kbd>6</kbd>, and <kbd>9</kbd> spawn you on the RED side.
- <kbd>1</kbd> spawns on the red side for the montage jump

All of the keys respawn the bots to their starting locations.

### Quick Action

This script creates a `quickAction` that you can bind to a key. **By default `quickAction` is bound to <kbd>T</kbd>**. `quickAction` teleports you to your last spawn (changed using the numpad keys) and it resets the bots health and locations. This can be changed using the arrow keys (see below).

### Arrow Keys

You can use the arrow keys to control what `quickAction` does, or use `UPARROW` to toggle `noclip`:

- DOWNARROW: QA moves you and bots (default)
- LEFTARROW: QA only moves bots
- RIGHTARROW: QA only moves you
- UPARROW: `noclip` toggle

To change the key to which `quickAction` is bound, edit [quickAction.cfg](./base/quickAction.cfg). Change `T` to the [key of your choice](https://wiki.teamfortress.com/wiki/Scripting#List_of_key_names).

```go
// quickAction.cfg
bind T quickAction
```

### Defaults (`defaults.cfg`)

You should update [defaults.cfg](./defaults.cfg) to return these keys to the default behavior that you want when not using this script:

- <kbd>T</kbd>
- <kbd>MOUSE1</kbd> (heals you with every fire)
- Numpad keys
- Arrow keys

For example, I use the <kbd>T</kbd> key to toggle my viewmodel.

```go
// defaults.cfg
bind T r_drawviewmodel
```

I use the arrow keys to switch loadouts. I use the numpad keys to switch classes. **If you use any of those keys in your normal gameplay, you'll need to set them to YOUR defaults.**

## Troubleshooting

### You can't move

If you're using a VPK config, a few different things could go wrong. One user found that his VPK config had its own, conflicting `listenserver.cfg` file.

### Bots aren't teleporting correctly

Try reloading the stage:

```go
htez
// or
htog
```

Also, try resetting the bots using the `resetBots` command:

```go
resetBots
```

### No Numpad

If you don't have a numpad, open up [load.cfg](./hightower-practice/load.cfg) and uncomment the line as indicated:

```go
// No Numpad?
// Uncomment the following line to use alternative hotkeys:
alias no_numpad_setting "exec scripts/hightower-practice/base/no-numpad; echo NO NUMPAD;"
```

Then, open [defaults.cfg](./hightower-practice/defaults.cfg) and uncomment those lines. Be sure to adjust any non-default bindings for which you use those keys:

```go
// No Numpad?
// Uncomment:
// bind "-" disguiseteam
// bind "=" ""
// bind BACKSPACE ""
// bind HOME ""
// bind END centerview
// bind 6 slot6
// bind 7 slot7
// bind 8 slot8
// bind 9 slot9
// bind 0 slot10
// bind DEL ""
```
