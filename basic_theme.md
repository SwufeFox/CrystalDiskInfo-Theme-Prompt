# CrystalDiskInfo Basic Theme

This document defines the basic resource structure for a CrystalDiskInfo theme.

When generating a CrystalDiskInfo theme, **all required resources must be generated consistently as one visual theme**.

## Required Files

A basic theme contains **32 files**:

### Configuration

```text
theme.ini
```

### Background

```text
ShizukuBackground-300.png
```

### Disk Status Images

Each status requires six resolutions:

```text
100
125
150
200
250
300
```

The required status groups are:

```text
SDdiskStatusBad
SDdiskStatusCaution
SDdiskStatusGood
SDdiskStatusGood100
SDdiskStatusUnknown
```

Therefore, the complete resource set is:

```text
SDdiskStatusBad-100.png
SDdiskStatusBad-125.png
SDdiskStatusBad-150.png
SDdiskStatusBad-200.png
SDdiskStatusBad-250.png
SDdiskStatusBad-300.png

SDdiskStatusCaution-100.png
SDdiskStatusCaution-125.png
SDdiskStatusCaution-150.png
SDdiskStatusCaution-200.png
SDdiskStatusCaution-250.png
SDdiskStatusCaution-300.png

SDdiskStatusGood-100.png
SDdiskStatusGood-125.png
SDdiskStatusGood-150.png
SDdiskStatusGood-200.png
SDdiskStatusGood-250.png
SDdiskStatusGood-300.png

SDdiskStatusGood100-100.png
SDdiskStatusGood100-125.png
SDdiskStatusGood100-150.png
SDdiskStatusGood100-200.png
SDdiskStatusGood100-250.png
SDdiskStatusGood100-300.png

SDdiskStatusUnknown-100.png
SDdiskStatusUnknown-125.png
SDdiskStatusUnknown-150.png
SDdiskStatusUnknown-200.png
SDdiskStatusUnknown-250.png
SDdiskStatusUnknown-300.png
```

## Status Semantics

The five status groups represent different disk-health states.

| Resource              | Meaning                       |
| --------------------- | ----------------------------- |
| `SDdiskStatusGood`    | Normal / healthy disk         |
| `SDdiskStatusGood100` | Excellent / 100% healthy disk |
| `SDdiskStatusCaution` | Warning / caution             |
| `SDdiskStatusBad`     | Bad / critical condition      |
| `SDdiskStatusUnknown` | Unknown / unavailable status  |

The visual language of these five states should remain consistent.

For example, if the theme uses a character, mascot, icon, or decorative element, each status should be a variation of the same design rather than five unrelated illustrations.

## Resolution Variants

Each status must be provided at six scales:

```text
100
125
150
200
250
300
```

These are **scale variants of the same visual asset**.

Do not redesign the asset independently for each resolution.

The composition, character, visual identity, colors, and major elements should remain consistent across all six variants.

Higher-resolution variants may contain additional detail when necessary, but they must remain visually equivalent.

## Background

The theme uses:

```text
ShizukuBackground-300.png
```

The background should visually match the status assets.

It should be designed as part of the same theme rather than treated as an unrelated wallpaper.

Avoid placing important UI elements or text in areas that may conflict with CrystalDiskInfo's interface.

## Visual Consistency

All generated resources MUST belong to the same visual system.

Maintain consistency in:

* color palette
* lighting
* line style
* rendering style
* character design
* perspective
* typography, if present
* decorative elements
* overall mood

The five health states should communicate their different meanings while clearly belonging to the same theme.

## AI Generation Rules

When using an image-generation model to create the assets:

1. Generate the theme concept first.
2. Establish the visual identity before generating individual status assets.
3. Generate all status variants from the same design language.
4. Preserve important character and object identities between states.
5. Do not introduce unrelated characters or visual styles.
6. Do not add arbitrary text, logos, or UI elements unless explicitly requested.
7. Do not change the required filenames.
8. Do not omit any required resolution.
9. Do not replace missing assets with placeholders.
10. Treat the complete 32-file set as one theme.

## Recommended Generation Workflow

```text
Theme Concept
     │
     ▼
Visual Style Definition
     │
     ├── Color Palette
     ├── Character / Mascot
     ├── Lighting
     ├── Composition
     └── Decorative Elements
     │
     ▼
Status Design
     │
     ├── Good
     ├── Good100
     ├── Caution
     ├── Bad
     └── Unknown
     │
     ▼
Resolution Variants
     │
     ├── 100
     ├── 125
     ├── 150
     ├── 200
     ├── 250
     └── 300
     │
     ▼
Background
     │
     ▼
theme.ini
     │
     ▼
Complete CrystalDiskInfo Theme
```

## Validation Checklist

Before considering a theme complete, verify:

* [ ] `theme.ini` exists
* [ ] `ShizukuBackground-300.png` exists
* [ ] All five status groups exist
* [ ] Every status has all six resolutions
* [ ] All filenames exactly match the required naming scheme
* [ ] All assets share the same visual style
* [ ] Status differences are visually understandable
* [ ] Resolution variants remain visually consistent
* [ ] Background matches the theme
* [ ] No required resource is missing

A valid basic theme must contain **exactly 32 required resources**.
