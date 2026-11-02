# Appearance · 0.1.0

`Import appearance` exposes `AppearanceSnapshot`, a read-only OS sampling helper
whose returned properties can also be copied/customized as a view-policy model.
Create a snapshot or call `Refresh()` to sample settings again.

Properties: `DarkMode`, `AccessibilityAvailable`, `ReduceMotion`,
`ReduceTransparency`, `IncreaseContrast`, `DifferentiateWithoutColor`,
`InvertColors`, `VoiceOver`. `ColorScheme()` returns `"dark"` or `"light"`.
`AnimationDuration(preferredSeconds)` returns zero when Reduce Motion is set,
otherwise the requested nonnegative duration. Negative durations throw.

Dark appearance uses Buoy's live `System.IsDarkMode` on all three platforms.
The accessibility options use native `NSWorkspace` queries on macOS, guarded by
selector availability. `AccessibilityAvailable` means a native workspace could
be queried; an individual unavailable selector reports false. On Windows/Linux,
accessibility flags are false and `AccessibilityAvailable` is false; false must
not be interpreted as verified preference support there.

No preferences are changed and no Accessibility permission is requested. This is
explicit snapshot refresh, not an observer. Refresh on application activation or
when handling OS appearance notifications. UI apps should sample on the main thread.

[Apple's accessibility display preferences](https://developer.apple.com/documentation/appkit/nsworkspace/accessibilitydisplayshouldreducemotion)
describe the native settings and their intended effect.
