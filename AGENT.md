# CrystalDiskInfo Theme Prompt

This repository provides specifications for creating custom themes for
CrystalDiskInfo with AI.

The human should describe the desired theme.
The agent is responsible for understanding the CrystalDiskInfo theme
format, selecting the appropriate theme type, generating the required
assets, and assembling the final theme.

---

## Core Rules

### 1. Read the relevant specification first

Before creating or modifying a theme, determine which specification
applies:

- `basic_theme.md` — character-focused themes
- `minimal_theme.md` — themes inheriting from an existing theme
- `full_theme.md` — complete, self-contained themes
- `theme_ini.md` — `theme.ini` configuration and inheritance

Read the relevant specification before generating resources.

Do not invent resource names, dimensions, or formats.

---

### 2. Master artwork first

When a resource has multiple size variants, **do not independently
generate every size with an image-generation model**.

Generate the highest-resolution source artwork first, then derive the
smaller variants programmatically.

For the character resources described in `basic_theme.md`:

```text
-300
  ↓
-250
-200
-150
-125
-100
````

The `-300` image is the master artwork.

Use Python/Pillow or another lossless image-processing workflow to create
the smaller variants.

This is a hard requirement.

Do NOT do this:

```text
AI → -300
AI → -250
AI → -200
AI → -150
AI → -125
AI → -100
```

Do this instead:

```text
AI → -300 master artwork
             │
             ▼
        image processing
             │
       ┌─────┼─────┬─────┬─────┬─────┐
       ▼     ▼     ▼     ▼     ▼     ▼
     -250  -200  -150  -125  -100
```

This prevents visual inconsistencies between scale variants.

---

### 3. Preserve transparency

Character illustrations are transparent-background assets unless the
relevant specification explicitly says otherwise.

Do not add a solid background to character assets.

The background is a separate resource.

---

### 4. Character states are variations of one character

When a theme contains multiple character status resources, they should
represent the same character and visual identity.

Different states should primarily be communicated through:

* facial expression
* pose
* gesture
* action
* emotional state
* small props or effects

Do not generate five unrelated characters merely because they correspond
to five different status states.

---

### 5. Backgrounds are different from character assets

A theme background is a complete scene/environment, not a character
illustration.

For Basic Themes, the background should be designed together with the
character composition.

Unless the specification says otherwise, leave suitable visual space
for the character to be displayed on the left side of the background.

---

## Theme Selection

Choose the theme type according to the user's request.

### Basic Theme

Use when the user wants a new character-focused theme.

Read:

```text
basic_theme.md
theme_ini.md
```

Typical workflow:

```text
Theme concept
    ↓
Character design
    ↓
Five status variations
    ↓
Generate master character artwork
    ↓
Generate derived size variants
    ↓
Generate background
    ↓
Create theme.ini
```

---

### Minimal Theme

Use when the user wants to modify, recolor, reskin, or extend an
existing theme.

Read:

```text
minimal_theme.md
theme_ini.md
```

Do not copy resources that can be inherited.

Only generate or include resources that actually need to change.

If a changed resource has multiple size variants, generate its master
variant first and derive the remaining variants programmatically.

---

### Full Theme

Use when the user explicitly wants a completely independent theme.

Read:

```text
full_theme.md
theme_ini.md
```

A Full Theme must provide every resource required by its specification.

Do not assume that every resource family has the same dimensions or
scale variants. Follow the resource-specific rules in
`full_theme.md`.

---

## Image Generation Workflow

When image generation is required:

1. Identify the resource being generated.
2. Read its specification.
3. Determine the master resolution and required derived resolutions.
4. Generate the master artwork.
5. Verify the master artwork's dimensions and transparency.
6. Generate smaller variants using Python/Pillow.
7. Verify every generated file.
8. Preserve the exact required filename.
9. Continue with the next resource.

Do not ask an image-generation model to repeatedly redraw the same asset
at different resolutions.

---

## Python Image Processing

Pillow is the preferred tool for generating derived image variants.

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

Preserve the source image's alpha channel.

Do not apply unnecessary transformations while generating size
variants.

---

## Resource Names

Resource filenames are part of the CrystalDiskInfo theme format.

Preserve them exactly as specified.

Do not:

* rename resources for convenience
* invent alternative filenames
* change capitalization
* omit required variants
* add arbitrary suffixes

---

## Theme Directory

A completed theme is installed at:

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
            └── ShizukuBackground-300.png
```

The final generated files should form a valid theme directory.

---

## Validation

Before declaring a theme complete:

* Verify all required files exist.
* Verify filenames exactly match the specification.
* Verify image dimensions.
* Verify transparency where required.
* Verify that derived variants were generated from their master artwork.
* Verify that no unnecessary resources were duplicated in Minimal Themes.
* Verify `theme.ini`.
* Verify parent-theme relationships.
* Verify that the final directory can be placed under:

```text
<software>\CdiResource\themes\<theme name>\
```

---

## Important

The specifications in this repository are authoritative for their
respective resource types.

When a user asks for a theme, do not merely describe what should be
generated.

Actually follow the specification and produce the required resources or
generation steps.

The intended workflow is:

```text
Human describes the theme
        ↓
Agent reads AGENT.md
        ↓
Agent reads the relevant specification
        ↓
Agent designs the theme
        ↓
Generate master artwork
        ↓
Programmatically derive variants
        ↓
Assemble theme.ini and resources
        ↓
Validate
        ↓
Complete CrystalDiskInfo theme
```
