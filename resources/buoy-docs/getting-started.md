---
title: "Appearance getting started"
summary: "Install appearance and use its core API with explicit application ownership."
category: "Guides"
order: 10
keywords: ["appearance", "installation", "example"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Appearance getting started

## Install and import

Copy the sealed `appearance-0.1.0.buipkg` archive into your project `packages/` directory, or install a source/registry dependency named `appearance` using BPM and sync it. Then use `Import appearance`. The archive includes this documentation as package resources.

Use a consuming source filename such as `main.bui`; a local module named exactly like the package shadows its import.

## Complete usage example

The example is compiler-checked as a complete Buoy module. Functions and Subs are intended to be called from the consuming app at the appropriate user action or lifecycle event.

```buoy
Import appearance

Sub Main()
    Dim snapshot As New AppearanceSnapshot()
    Print snapshot.ColorScheme()
    Print snapshot.AnimationDuration(0.25)
    snapshot.Refresh()
End Sub
```

## Integrate with the application

Construction samples once. Call Refresh when the application activates or when your app receives an appearance notification. Sample from the UI main thread. The properties cannot be assigned; keep app-specific presentation policy separately.

## Handle failures and unsupported targets

AnimationDuration rejects negative seconds with InvalidArgumentException. A native preference selector that is unavailable reports false. AccessibilityAvailable says a workspace was available, not that every individual selector exists.

Dark mode uses System.IsDarkMode on macOS, Windows, and Linux. The additional accessibility preferences are queried through NSWorkspace on macOS. On Windows and Linux they are false and AccessibilityAvailable is false; that is an unsupported measurement, not proof that the user disabled a preference.

Return to the [overview](index.md) or consult the [API reference](api.md).
