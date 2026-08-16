# CrystalDiskInfo Basic Theme

A Basic Theme is a character-focused CrystalDiskInfo theme consisting
of character illustrations, a large background, and a `theme.ini`.

The character illustrations represent different disk-health states
through different expressions, poses, and actions.

They are transparent-background character assets, not generic status
icons.

---

## Theme Structure

A Basic Theme contains:

```text
Basic Theme
├── theme.ini
├── ShizukuBackground-300.png
│
├── SDdiskStatusGood100-*.png
├── SDdiskStatusGood-*.png
├── SDdiskStatusCaution-*.png
├── SDdiskStatusBad-*.png
└── SDdiskStatusUnknown-*.png
````

There are five character status families:

```text
SDdiskStatusGood100
SDdiskStatusGood
SDdiskStatusCaution
SDdiskStatusBad
SDdiskStatusUnknown
```

Each family has six size variants:

```text
-300
-250
-200
-150
-125
-100
```

This results in:

```text
5 status families × 6 variants = 30 character images
30 character images + 1 background + 1 theme.ini = 32 files
```

---

# Character Illustrations

All `SDdiskStatus*` resources are transparent-background character
illustrations.

They are used to visually communicate the disk-health state.

The illustrations may change:

* facial expression
* pose
* gesture
* action
* emotional state
* props
* decorative effects

between different status families.

However, they should remain visually recognizable as the same character
and belong to the same theme.

Do not design the five status families as unrelated characters.

---

# Status Families

| Resource              | Meaning                      |
| --------------------- | ---------------------------- |
| `SDdiskStatusGood100` | 100% / perfect health        |
| `SDdiskStatusGood`    | Good / healthy               |
| `SDdiskStatusCaution` | Caution / warning            |
| `SDdiskStatusBad`     | Bad / critical               |
| `SDdiskStatusUnknown` | Unknown / unavailable status |

The artistic interpretation is flexible.

For example:

```text
Good100  → especially happy / energetic
Good     → relaxed / cheerful
Caution  → worried / concerned
Bad      → distressed / shocked
Unknown  → confused / uncertain
```

These are examples, not mandatory expressions.

The important requirement is that the states are visually
distinguishable while remaining part of one coherent character set.

---

# Image Sizes

The numeric suffix in the filename is a **predefined size variant**.

It does not mean that each image should be independently designed.

For character resources, the dimensions are:

| Suffix | Canvas Size |
| ------ | ----------: |
| `-300` |   384 × 576 |
| `-250` |   320 × 480 |
| `-200` |   256 × 384 |
| `-150` |   192 × 288 |
| `-125` |   160 × 240 |
| `-100` |   128 × 192 |

For example:

```text
SDdiskStatusGood100-300.png
384 × 576

SDdiskStatusGood100-200.png
256 × 384

SDdiskStatusGood100-100.png
128 × 192
```

All six variants represent the same artwork at different sizes.

---

# Master Artwork

The `-300` variant is the master artwork.

For every status family, generate the `-300` image first:

```text
SDdiskStatusGood100-300.png
SDdiskStatusGood-300.png
SDdiskStatusCaution-300.png
SDdiskStatusBad-300.png
SDdiskStatusUnknown-300.png
```

Each master image should be:

```text
384 × 576 px
```

Do not independently generate the six size variants with an image
generation model.

Instead:

```text
Generate -300
     ↓
Python / Pillow
     ↓
-250
-200
-150
-125
-100
```

This keeps every size variant pixel-consistent with the original
artwork.

---

# Character Composition

Design the character specifically for the `384 × 576` master canvas.

The character should:

* fit completely inside the canvas
* retain important details after downscaling
* have reasonable transparent margins
* avoid important details touching the canvas edges
* remain recognizable at the smallest size

Transparent space is expected.

The character does not need to fill the entire canvas.

---

# Generating Size Variants

Use the `-300` master image as the source for all smaller variants.

Python/Pillow is recommended.

Example:

```python
from PIL import Image

sizes = {
    300: (384, 576),
    250: (320, 480),
    200: (256, 384),
    150: (192, 288),
    125: (160, 240),
    100: (128, 192),
}

source = Image.open("SDdiskStatusGood100-300.png")

for scale, size in sizes.items():
    image = source.resize(size, Image.Resampling.LANCZOS)
    image.save(f"SDdiskStatusGood100-{scale}.png")
```

The alpha channel must be preserved.

Apply the same process to every status family.

---

# Background

The Basic Theme contains:

```text
ShizukuBackground-300.png
```

This is the theme's large background image.

The background is fundamentally different from the character assets:

* it is not transparent
* it is a complete scene/environment
* it provides the visual setting for the character
* it should be designed independently from the character asset

The typical background canvas is:

```text
3000 × 3000 px
```

---

## Background Composition

The background should be designed with the character's placement in
mind.

Reserve suitable visual space on the **left side** for the character
illustration.

For example:

```text
┌──────────────────────────────────────┐
│                                      │
│  Character Area       Scene /        │
│  relatively           Environment    │
│  uncluttered                         │
│                                      │
│                                      │
└──────────────────────────────────────┘
```

The exact composition depends on the theme.

Do not place important visual elements directly behind the character
unless the composition intentionally calls for it.

The background should match the character's:

* color palette
* lighting
* atmosphere
* rendering style
* setting
* visual motifs

---

# Visual Consistency

The entire Basic Theme should feel like one artwork.

Maintain consistency between the character states and background in:

* character identity
* art style
* line art
* rendering
* color palette
* lighting
* proportions
* costume
* environment
* overall atmosphere

The status illustrations should look like different moments or states
of the same character.

---

# Required Files

A complete Basic Theme contains:

```text
theme.ini

ShizukuBackground-300.png

SDdiskStatusGood100-300.png
SDdiskStatusGood100-250.png
SDdiskStatusGood100-200.png
SDdiskStatusGood100-150.png
SDdiskStatusGood100-125.png
SDdiskStatusGood100-100.png

SDdiskStatusGood-300.png
SDdiskStatusGood-250.png
SDdiskStatusGood-200.png
SDdiskStatusGood-150.png
SDdiskStatusGood-125.png
SDdiskStatusGood-100.png

SDdiskStatusCaution-300.png
SDdiskStatusCaution-250.png
SDdiskStatusCaution-200.png
SDdiskStatusCaution-150.png
SDdiskStatusCaution-125.png
SDdiskStatusCaution-100.png

SDdiskStatusBad-300.png
SDdiskStatusBad-250.png
SDdiskStatusBad-200.png
SDdiskStatusBad-150.png
SDdiskStatusBad-125.png
SDdiskStatusBad-100.png

SDdiskStatusUnknown-300.png
SDdiskStatusUnknown-250.png
SDdiskStatusUnknown-200.png
SDdiskStatusUnknown-150.png
SDdiskStatusUnknown-125.png
SDdiskStatusUnknown-100.png
```

---

# Recommended Workflow

```text
Theme Concept
      ↓
Character Design
      ↓
Design five character states
      │
      ├── Good100
      ├── Good
      ├── Caution
      ├── Bad
      └── Unknown
      ↓
Generate five 384 × 576 master artworks
      ↓
Generate the 3000 × 3000 background
      ↓
Use Python/Pillow to create all smaller variants
      ↓
Create theme.ini
      ↓
Validate the complete theme
```

---

# AI Generation Rules

When generating a Basic Theme:

1. Design one coherent character first.
2. Create five variations of that character for the five status states.
3. Generate only the `-300` character artwork with the image-generation
   model.
4. Make every `-300` character image exactly `384 × 576`.
5. Generate all smaller variants programmatically from the `-300`
   artwork.
6. Never independently redraw the same character at different sizes.
7. Preserve transparency in all character images.
8. Keep the character identity consistent between all states.
9. Use expressions, poses, and actions to communicate different states.
10. Generate the background separately at approximately `3000 × 3000`.
11. Reserve suitable space on the left side of the background for the
    character.
12. Do not put UI elements or arbitrary text into character images.
13. Preserve all filenames exactly.
14. Do not omit any required variant.
15. Keep the character and background visually consistent.

---

# Validation Checklist

Before considering a Basic Theme complete:

* [ ] `theme.ini` exists
* [ ] `ShizukuBackground-300.png` exists
* [ ] Background is 3000 × 3000
* [ ] All five status families exist
* [ ] Every status has a `-300` master
* [ ] Every `-300` image is 384 × 576
* [ ] `-250` images are 320 × 480
* [ ] `-200` images are 256 × 384
* [ ] `-150` images are 192 × 288
* [ ] `-125` images are 160 × 240
* [ ] `-100` images are 128 × 192
* [ ] Smaller variants were generated from the corresponding `-300`
  master
* [ ] Character images have transparent backgrounds
* [ ] All five states use the same character design
* [ ] States have visually different expressions or actions
* [ ] Background provides suitable space for the character
* [ ] Background and character share the same visual style
* [ ] All filenames are correct
* [ ] No required resource is missing
