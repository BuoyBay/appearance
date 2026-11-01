---
title: "appearance typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["AppearanceSnapshot"]
dependencies: []
symbols: ["AppearanceSnapshot"]
related: ["api.md", "getting-started.md", "index.md"]
---

# appearance typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## AppearanceSnapshot

`Public Class AppearanceSnapshot`

Read-only snapshot; Refresh explicitly updates it after OS settings change.

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `DarkMode` | `Boolean` | Yes | No | — | — |
| `AccessibilityAvailable` | `Boolean` | Yes | No | — | — |
| `ReduceMotion` | `Boolean` | Yes | No | — | — |
| `ReduceTransparency` | `Boolean` | Yes | No | — | — |
| `IncreaseContrast` | `Boolean` | Yes | No | — | — |
| `DifferentiateWithoutColor` | `Boolean` | Yes | No | — | — |
| `InvertColors` | `Boolean` | Yes | No | — | — |
| `VoiceOver` | `Boolean` | Yes | No | — | — |

### Constructor

`Public Sub Constructor()`

No parameters.

Returns: no value.

### Refresh

`Public Sub Refresh()`

No parameters.

Returns: no value.

### ColorScheme

`Public Function ColorScheme() As String`

No parameters.

#### Returns

| Type |
| --- |
| `String` |

### AnimationDuration

`Public Function AnimationDuration(preferredSeconds As Double) As Double`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `preferredSeconds` | `Double` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Double` |
