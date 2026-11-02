---
title: "Appearance API"
summary: "Read system appearance and adapt motion without changing preferences."
category: "Reference"
order: 20
keywords: ["appearance", "API", "lifecycle"]
symbols: ["AppearanceSnapshot", "AppearanceSnapshot.Refresh", "AppearanceSnapshot.DarkMode", "AppearanceSnapshot.AccessibilityAvailable", "AppearanceSnapshot.ReduceMotion", "AppearanceSnapshot.ReduceTransparency", "AppearanceSnapshot.IncreaseContrast", "AppearanceSnapshot.DifferentiateWithoutColor", "AppearanceSnapshot.InvertColors", "AppearanceSnapshot.VoiceOver", "AppearanceSnapshot.ColorScheme", "AppearanceSnapshot.AnimationDuration"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# Appearance API

Import the `appearance` package. Constructors below use the class name; invoke them with `New`. Listed members are public client APIs; native declarations and trampoline helpers are implementation details.

## Public surface

| Symbol | Contract |
| --- | --- |
| `AppearanceSnapshot` | Constructs and immediately samples the current settings. |
| `AppearanceSnapshot.Refresh()` | Explicitly resamples all properties; there is no automatic observer. |
| `AppearanceSnapshot.DarkMode` | Read-only Boolean; true for a dark system appearance. |
| `AppearanceSnapshot.AccessibilityAvailable` | True when native workspace accessibility settings can be queried. |
| `AppearanceSnapshot.ReduceMotion` | Read-only motion preference. Used by AnimationDuration. |
| `AppearanceSnapshot.ReduceTransparency` | Read-only preference for less translucent presentation. |
| `AppearanceSnapshot.IncreaseContrast` | Read-only contrast preference. |
| `AppearanceSnapshot.DifferentiateWithoutColor` | Read-only preference to avoid color-only distinctions. |
| `AppearanceSnapshot.InvertColors` | Read-only color inversion preference. |
| `AppearanceSnapshot.VoiceOver` | Read-only VoiceOver state where the native selector exists. |
| `AppearanceSnapshot.ColorScheme() As String` | Returns dark or light. |
| `AppearanceSnapshot.AnimationDuration(preferredSeconds As Double) As Double` | Returns zero for Reduce Motion, otherwise the nonnegative preferred value. |

## Ownership and timing

Construction samples once. Call Refresh when the application activates or when your app receives an appearance notification. Sample from the UI main thread. The properties cannot be assigned; keep app-specific presentation policy separately.

## Errors and result interpretation

AnimationDuration rejects negative seconds with InvalidArgumentException. A native preference selector that is unavailable reports false. AccessibilityAvailable says a workspace was available, not that every individual selector exists.

## Platform behavior

Dark mode uses System.IsDarkMode on macOS, Windows, and Linux. The additional accessibility preferences are queried through NSWorkspace on macOS. On Windows and Linux they are false and AccessibilityAvailable is false; that is an unsupported measurement, not proof that the user disabled a preference.

See the [complete usage example](getting-started.md) and the [package overview](index.md).

[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
