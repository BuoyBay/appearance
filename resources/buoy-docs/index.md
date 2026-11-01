---
title: "Appearance"
summary: "Read system appearance and adapt motion without changing preferences."
category: "Overview"
order: 0
keywords: ["appearance"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# Appearance

AppearanceSnapshot samples dark mode and accessibility display preferences into read-only properties. Use it when choosing an application color scheme or reducing animation. It observes no notifications and changes no OS setting.

## Platform support

Dark mode uses System.IsDarkMode on macOS, Windows, and Linux. The additional accessibility preferences are queried through NSWorkspace on macOS. On Windows and Linux they are false and AccessibilityAvailable is false; that is an unsupported measurement, not proof that the user disabled a preference.

## Start reading

- [Getting started](getting-started.md) walks through installation and a complete example.
- [API reference](api.md) describes public symbols, state, errors, and ownership.

## Scope

Construction samples once. Call Refresh when the application activates or when your app receives an appearance notification. Sample from the UI main thread. The properties cannot be assigned; keep app-specific presentation policy separately.
