# CrystalDiskInfo Basic Theme

A Basic Theme is a CrystalDiskInfo theme built around a set of
character illustrations, a background image, and a `theme.ini`.

The basic theme focuses on the character/status presentation and
does not necessarily provide every visual resource used by a
complete CrystalDiskInfo interface.

---

## Theme Structure

A basic theme contains:

```text
Basic Theme
├── theme.ini
├── ShizukuBackground-300.png
│
├── SDdiskStatusBad-*.png
├── SDdiskStatusCaution-*.png
├── SDdiskStatusGood-*.png
├── SDdiskStatusGood100-*.png
└── SDdiskStatusUnknown-*.png
````

Each status family normally has six resource variants:

```text
100
125
150
200
250
300
```

For example:

```text
SDdiskStatusGood100-100.png
SDdiskStatusGood100-125.png
SDdiskStatusGood100-150.png
SDdiskStatusGood100-200.png
SDdiskStatusGood100-250.png
SDdiskStatusGood100-300.png
```

---

# Character Illustrations

The `SDdiskStatus*` resources are **character illustrations**, not
generic status icons.

They are usually transparent-background character or mascot
illustrations displayed as part of CrystalDiskInfo's disk-health
presentation.

A typical character asset uses a canvas of approximately:

```text
256 × 384 px
```

For example:

```text
SDdiskStatusGood100-200.png
```

contains a complete character illustration rather than a small
symbol or badge.

The character itself is an important part of the theme's visual
identity.

---

## Status Families

The basic theme contains five status families:

| Resource              | Meaning               |
| --------------------- | --------------------- |
| `SDdiskStatusGood100` | 100% / perfect health |
| `SDdiskStatusGood`    | Good / healthy        |
| `SDdiskStatusCaution` | Caution / warning     |
| `SDdiskStatusBad`     | Bad / critical        |
| `SDdiskStatusUnknown` | Unknown health state  |

The exact artistic representation is determined by the theme.

For a character-based theme, the status can be communicated through
the character's:

* facial expression
* pose
* gesture
* accessories
* visual effects
* surrounding decorations
* overall emotional state

For example:

```text
Good100  → especially happy / perfect condition
Good     → normal / healthy
Caution  → worried / warning
Bad      → distressed / critical
Unknown  → confused / uncertain
```

These are examples of visual direction, not mandatory character
expressions.

---

# Character Consistency

All `SDdiskStatus*` illustrations belonging to the same theme should
look like members of the same character set.

Maintain consistency in:

* character identity
* proportions
* hairstyle
* clothing
* rendering style
* line art
* color palette
* lighting
* perspective
* overall art style

The character may change pose or expression between health states,
but should remain recognizably the same character unless the theme
explicitly calls for different characters.

Do not generate five unrelated illustrations.

---

# Status Variants

The six variants of a status represent the same character design at
different CrystalDiskInfo resource scales.

For example:

```text
SDdiskStatusGood-100.png
SDdiskStatusGood-125.png
SDdiskStatusGood-150.png
SDdiskStatusGood-200.png
SDdiskStatusGood-250.png
SDdiskStatusGood-300.png
```

These should depict the same character and the same status.

Do not redesign the character independently for each variant.

The source artwork should be created at sufficient quality to produce
all required variants.

---

# Background

The basic theme uses:

```text
ShizukuBackground-300.png
```

The background is a large square image with a typical canvas size of:

```text
3000 × 3000 px
```

Unlike the character illustrations, the background is intended to
provide the large-scale visual environment behind the CrystalDiskInfo
interface.

The background should therefore be designed with:

* sufficient resolution
* appropriate composition
* suitable negative space
* visual compatibility with the character
* consistent lighting and color palette

Do not treat the background as simply an enlarged character image.

It should function as a complete scene or visual backdrop.

---

# Character and Background Relationship

The character illustrations and background should be designed as one
theme.

For example:

```text
        Theme Concept
             │
       ┌─────┴─────┐
       ▼           ▼
   Character     Background
   256×384       3000×3000
       │           │
       └─────┬─────┘
             ▼
       CrystalDiskInfo
          Basic Theme
```

The character should visually fit into the environment established by
the background.

Keep consistent:

* color palette
* lighting direction
* atmosphere
* artistic style
* visual motifs
* character design

---

# `theme.ini`

`theme.ini` controls the theme's metadata, colors, transparency, and
optional parent themes.

Example:

```ini
[Info]
Author=My Theme

[Color];RGB
LabelText=0xFFFFFF;
ButtonText=0x000000;
ListText1=0xFFFFFF;
ListText2=0xFFFFFF;
ListBk1=0x202020;
ListBk2=0x333333;
ListLine1=0x535353;
ListLine2=0x444444;
Glass=0x202020;

[Alpha]
GlassAlpha=128;
```

A theme may also inherit resources from other themes:

```ini
[Info]
Author=My Theme
ParentTheme1=ShizukuMiko
ParentTheme2=ShizukuHotaru
```

See [`theme_ini.md`](./theme_ini.md) for the complete configuration
and inheritance specification.

---

# AI Generation Rules

When generating a Basic Theme:

1. Design the theme concept first.
2. Design the main character or mascot.
3. Create a coherent set of five health-state illustrations.
4. Keep the character identity consistent across all states.
5. Treat `SDdiskStatus*` as character illustrations, not icons.
6. Prepare the character artwork for a 256×384 canvas.
7. Generate all six CrystalDiskInfo variants for each status.
8. Create a 3000×3000 background.
9. Make the background visually compatible with the character.
10. Keep transparent backgrounds for character assets where required.
11. Do not place unnecessary UI elements inside character assets.
12. Preserve all required filenames exactly.
13. Generate `theme.ini` with colors matching the artwork.
14. Do not generate unrelated visual styles for different resources.

---

# Required Resources

A complete Basic Theme should provide:

```text
theme.ini

SDdiskStatusBad
    × 6

SDdiskStatusCaution
    × 6

SDdiskStatusGood
    × 6

SDdiskStatusGood100
    × 6

SDdiskStatusUnknown
    × 6

ShizukuBackground-300.png
```

This gives:

```text
5 status families × 6 variants
+ 1 background
+ 1 theme.ini
```

for the basic resource set.

---

# Validation Checklist

Before considering a Basic Theme complete:

* [ ] `theme.ini` exists
* [ ] `ShizukuBackground-300.png` exists
* [ ] Background is approximately 3000×3000
* [ ] `SDdiskStatusGood100` exists
* [ ] `SDdiskStatusGood` exists
* [ ] `SDdiskStatusCaution` exists
* [ ] `SDdiskStatusBad` exists
* [ ] `SDdiskStatusUnknown` exists
* [ ] Every status has all six variants
* [ ] Character artwork is approximately 256×384
* [ ] Character assets use the appropriate transparent background
* [ ] All status illustrations belong to the same visual theme
* [ ] Statuses are visually distinguishable
* [ ] Background and character share the same visual language
* [ ] Filenames are unchanged
* [ ] `theme.ini` matches the visual theme

---

# Design Principle

A Basic Theme should be understood as:

> **A consistent character-based visual theme for CrystalDiskInfo,
> consisting of health-state character illustrations, a large
> background, and theme configuration.**

The most important requirement is not merely producing all files.

The entire resource set should feel like **one character, one world,
and one coherent theme**.
