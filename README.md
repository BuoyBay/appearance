# Dark mode and accessibility snapshot

`Import appearance` exposes `AppearanceSnapshot`, a read-only OS sampling helper
whose returned properties can also be copied/customized as a view-policy model.
Create a snapshot or call `Refresh()` to sample settings again.

Properties: `DarkMode`, `AccessibilityAvailable`, `ReduceMotion`,
`ReduceTransparency`, `IncreaseContrast`, `DifferentiateWithoutColor`,
`InvertColors`, `VoiceOver`. `ColorScheme()` returns `"dark"` or `"light"`.
`AnimationDuration(preferredSeconds)` returns zero when Reduce Motion is set,
otherwise the requested nonnegative duration. Negative durations throw.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add appearance --git https://github.com/BuoyBay/appearance.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

```basic
Import appearance

Sub Main()
    Dim snapshot As New AppearanceSnapshot()
    Print snapshot.ColorScheme()
    Print snapshot.AnimationDuration(0.25)
    snapshot.Refresh()
End Sub
```

## Platform and scope

Dark mode is sampled on macOS, Windows and Linux. Additional accessibility preferences use macOS APIs; check `AccessibilityAvailable` before interpreting them.

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer appearance
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```


## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
