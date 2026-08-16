# CrystalDiskInfo Full Theme

A Full Theme is a completely self-contained CrystalDiskInfo theme.

Unlike a Minimal Theme, a Full Theme should not rely on another theme to
provide its required resources.

---

## Basic Concept

A Full Theme contains all resources required by its theme definition:

```text
Full Theme
├── theme.ini
├── required image resources
└── all required variants
````

The exact resources depend on the resource families supported by the
theme.

Do not assume that every resource uses the same dimensions or the same
set of size variants.

---

# Resource Variants

Some CrystalDiskInfo resources use numeric filename suffixes such as:

```text
-300
-250
-200
-150
-125
-100
```

These suffixes represent predefined size variants for the corresponding
resource family.

They do **not** mean that every resource in a Full Theme necessarily
uses the same dimensions.

Always follow the dimensions specified for the particular resource
family.

---

# Master Artwork

When a resource family uses multiple size variants, create one master
artwork at the highest required resolution whenever the specification
defines such a master.

For the character resources used by Basic Themes:

```text
-300
```

is the master artwork.

Its dimensions are:

```text
384 × 576
```

The smaller character variants are:

| Suffix | Canvas Size |
| ------ | ----------: |
| `-300` |   384 × 576 |
| `-250` |   320 × 480 |
| `-200` |   256 × 384 |
| `-150` |   192 × 288 |
| `-125` |   160 × 240 |
| `-100` |   128 × 192 |

Generate the master first:

```text
Generate master artwork
        ↓
Python / Pillow
        ↓
-250
-200
-150
-125
-100
```

Do not independently redraw the same artwork at every size.

---

# Resource-Specific Dimensions

The numeric suffix must not be treated as a universal image dimension.

For example, the character resources use:

```text
-300 → 384 × 576
-250 → 320 × 480
-200 → 256 × 384
-150 → 192 × 288
-125 → 160 × 240
-100 → 128 × 192
```

Other CrystalDiskInfo resources may have different dimensions or may
not use these variants at all.

Therefore:

> Always determine the dimensions from the specification of the
> resource being generated.

Never infer a resource's dimensions solely from its filename.

---

# Character Resources

When the Full Theme contains character status illustrations, they
should follow the character-resource rules defined by
`basic_theme.md`.

Character images should:

* use transparent backgrounds
* preserve the same character identity
* use different expressions, poses, or actions for different states
* remain visually consistent
* use a master artwork for their size variants

Do not create unrelated characters for different disk-health states.

---

# Background Resources

A theme background is a separate scene/environment resource.

For the Basic Theme background:

```text
ShizukuBackground-300.png
```

is typically:

```text
3000 × 3000 px
```

The background should be designed as a complete environment and should
visually match the character assets.

When used with a character-focused theme, reserve suitable space for the
character, particularly on the left side where appropriate.

The background is not a transparent character asset.

---

# `theme.ini`

A Full Theme requires its own `theme.ini`.

Example:

```ini
[Info]
Author=YourName

[Color]
LabelText=0x000000;
ButtonText=0x000000;
ListText1=0x000000;
ListText2=0x000000;
ListBk1=0xFFFFFF;
ListBk2=0xF8F8F8;
ListLine1=0xE0E0E0;
ListLine2=0xF0F0F0;
Glass=0xFFFFFF;

[Alpha]
GlassAlpha=128;
```

The actual sections and values depend on the desired theme.

See:

```text
theme_ini.md
```

for the complete `theme.ini` rules.

---

# Inheritance

A Full Theme is intended to be self-contained.

Do not use parent-theme inheritance merely to avoid including resources
that a Full Theme is expected to contain.

If the user wants to reuse existing resources through inheritance,
create a Minimal Theme instead.

Conceptually:

```text
Full Theme:

Theme
 ├── theme.ini
 ├── resource A
 ├── resource B
 ├── resource C
 └── resource D


Minimal Theme:

Theme
 ├── theme.ini
 └── changed resource A
          │
          └── inherited from Parent Theme
```

---

# Recommended Workflow

```text
Theme Concept
      ↓
Determine required resource families
      ↓
Read the corresponding specifications
      ↓
Design the visual system
      ↓
Generate master artworks
      ↓
Generate derived size variants
      ↓
Create remaining resources
      ↓
Create theme.ini
      ↓
Verify all required resources
      ↓
Validate the complete theme
```

For character-focused themes:

```text
Character Design
      ↓
Five Status Variations
      ↓
Generate 384 × 576 Masters
      ↓
Generate Smaller Variants
      ↓
Generate 3000 × 3000 Background
```

---

# AI Generation Rules

When generating a Full Theme:

1. Read `full_theme.md` and the specifications for each resource family.
2. Determine every resource required by the selected theme.
3. Do not assume that every resource uses the same dimensions.
4. Generate master artwork before derived variants.
5. Generate smaller variants programmatically whenever applicable.
6. Preserve transparency for resources that require it.
7. Preserve exact filenames.
8. Do not omit required resources.
9. Do not duplicate unrelated resources.
10. Keep all assets visually consistent.
11. Create an independent `theme.ini`.
12. Do not rely on a parent theme unless the theme specification
    explicitly allows it.

---

# Installation

Place the completed theme in:

```text
<software>\CdiResource\themes\<theme name>\
```

For example:

```text
CrystalDiskInfo\
└── CdiResource\
    └── themes\
        └── MyTheme\
            ├── theme.ini
            ├── ...
            └── required resources
```

---

# Validation Checklist

Before considering a Full Theme complete:

* [ ] `theme.ini` exists
* [ ] All required resource families are present
* [ ] Every resource uses the correct filename
* [ ] Every resource uses the correct dimensions
* [ ] Multi-size resources have all required variants
* [ ] Master artwork exists where applicable
* [ ] Smaller variants were derived from the master artwork
* [ ] Transparent resources preserve transparency
* [ ] Character resources remain visually consistent
* [ ] Background resources are correctly sized
* [ ] The theme does not unnecessarily depend on another theme
* [ ] `theme.ini` follows `theme_ini.md`
* [ ] The complete theme can be placed under
  `<software>\CdiResource\themes\<theme name>\`

