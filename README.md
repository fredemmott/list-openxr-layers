# Downloading and running the scripts

Download the signed scripts from [the latest release](https://github.com/fredemmott/openxr-layer-scripts/releases/latest).

A fresh install of Windows will refuse to run any PowerShell scripts; to run these scripts, open an administrator terminal, then:

```
powershell -ExecutionPolicy RemoteSigned
```

... then run the scripts from inside the Powershell.

# list-openxr-layers

This is a small PowerShell script for listing OpenXR API layers, in load order, and whether or not they're active.

It is a debugging tool, originally part of [Hand Tracked Cockpit Clicking](https://github.com/fredemmott/hand-tracked-cockpit-clicking).

![screenshot](doc/screenshot.png)

# edit-openxr-layers

This script supports enabling, disabling, and re-ordering OpenXR API layers; it is intended to be used in conjunction with `list-openxr-layers`.

**edit-openxr-layers must be ran as administrator.**

## Enabling, disabling, and removing layers

```
edit-openxr-layers -Mode Enable|Disable|Remove -LayerPath "C:\... path to API layer"
```

`-Mode` and `-LayerPath` can be ommitted when there are no other arguments, for example:

```
edit-openxr-layers Disable "C:\Program Files\Ultraleap\OpenXR\UltraleapHandTracking.json"
```

## Re-ordering layers

If you want a layer to be the first or last layer, use:

```
edit-openxr-layers -Mode First|Last -LayerPath "C:\... path to API layer"
```

If you want LayerA to be before LayerB:

```
edit-openxr-layers -Mode Before "C:\...path to LayerA" -RelativeTo "C:\...path to LayerB"
```

`-Mode After` is also supported.

# License

These scripts are licensed under [the MIT license](LICENSE).
