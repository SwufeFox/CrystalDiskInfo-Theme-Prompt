# CrystalDiskInfo Full Theme

A **Full Theme** is a self-contained CrystalDiskInfo theme that provides its own complete set of visual resources instead of relying on parent themes for the main UI assets.

Unlike a lightweight or inherited theme, a Full Theme should contain the resources required to render the CrystalDiskInfo interface independently.

---

## Full Theme Structure

A Full Theme is composed of:

```text
Full Theme
├── theme.ini
│
├── Disk Health
│   ├── diskBad
│   ├── diskCaution
│   ├── diskGood
│   ├── diskGoodGreen
│   ├── diskUnknown
│   ├── diskBadMini
│   ├── diskCautionMini
│   ├── diskGoodMini
│   ├── diskGoodGreenMini
│   └── diskUnknownMini
│
├── Disk Status
│   ├── diskStatusBad
│   ├── diskStatusCaution
│   ├── diskStatusGood
│   ├── diskStatusGoodGreen
│   └── diskStatusUnknown
│
├── Temperature
│   ├── temperatureBad
│   ├── temperatureCaution
│   ├── temperatureGood
│   ├── temperatureGoodGreen
│   └── temperatureUnknown
│
├── Volume
│   ├── volumeL
│   ├── volumeM
│   ├── volumeS
│   └── volumeZ
│
├── Navigation / Controls
│   ├── nextDisk
│   ├── preDisk
│   ├── playSound
│   └── selectSound
│
├── Branding
│   ├── logo
│   ├── ShizukuBackground
│   ├── ShizukuAbout
│   └── ShizukuCopyright
│
└── Other resources
```

## The resource families above are based on an existing full CrystalDiskInfo theme. The reference theme contains these resource groups and their six standard size variants.

# Standard Image Sizes

Most UI image resources use six size variants:

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
logo-100.png
logo-125.png
logo-150.png
logo-200.png
logo-250.png
logo-300.png
```

The reference Full Theme follows this six-size pattern for `logo`, navigation controls, status resources, temperature resources, and volume resources.
A resource family should normally provide all six variants unless the CrystalDiskInfo resource itself has a different specification.

---

# Disk Health Resources

The main disk-health resources are:

```text
diskBad
diskCaution
diskGood
diskGoodGreen
diskUnknown
```

Each uses six sizes:

```text
-100
-125
-150
-200
-250
-300
```

For example:

```text
diskBad-100.png
diskBad-125.png
diskBad-150.png
diskBad-200.png
diskBad-250.png
diskBad-300.png
```

The reference theme contains the corresponding `diskBad`, `diskCaution`, `diskGood`, and related resource families.

---

# Mini Disk Health Resources

Some disk-health resources also have a `Mini` variant:

```text
diskBadMini
diskCautionMini
diskGoodMini
diskGoodGreenMini
diskUnknownMini
```

For example:

```text
diskGoodMini-100.png
diskGoodMini-125.png
diskGoodMini-150.png
diskGoodMini-200.png
diskGoodMini-250.png
diskGoodMini-300.png
```

These should be treated as a separate resource family.

## The `Mini` assets should visually correspond to their normal counterparts while being designed for the smaller UI representation.

# Disk Status Resources

The Full Theme provides status indicators:

```text
diskStatusBad
diskStatusCaution
diskStatusGood
diskStatusGoodGreen
diskStatusUnknown
```

Each has six sizes:

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
diskStatusBad-100.png
diskStatusBad-125.png
diskStatusBad-150.png
diskStatusBad-200.png
diskStatusBad-250.png
diskStatusBad-300.png
```

The reference theme contains all five status families.

---

# Temperature Resources

Temperature indicators use the following families:

```text
temperatureBad
temperatureCaution
temperatureGood
temperatureGoodGreen
temperatureUnknown
```

Each uses six standard sizes.

Example:

```text
temperatureGood-100.png
temperatureGood-125.png
temperatureGood-150.png
temperatureGood-200.png
temperatureGood-250.png
temperatureGood-300.png
```

The visual semantics should correspond to the disk-health status colors and overall theme design.

The reference theme contains all five temperature states.

---

# Volume Resources

Volume indicators use four resource families:

```text
volumeL
volumeM
volumeS
volumeZ
```

Each provides six sizes:

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
volumeL-100.png
volumeL-125.png
volumeL-150.png
volumeL-200.png
volumeL-250.png
volumeL-300.png
```

The reference theme contains all four volume families.

---

# Navigation and Control Resources

The Full Theme can provide resources for disk navigation and sound controls:

```text
nextDisk
preDisk
playSound
selectSound
```

Each uses the six standard sizes:

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
nextDisk-100.png
nextDisk-125.png
nextDisk-150.png
nextDisk-200.png
nextDisk-250.png
nextDisk-300.png
```

## The reference theme contains all four control families.

# Logo

The theme may provide its own CrystalDiskInfo logo:

```text
logo-100.png
logo-125.png
logo-150.png
logo-200.png
logo-250.png
logo-300.png
```

The logo should visually match the rest of the theme.

The reference Full Theme contains all six logo sizes.

---

# Shizuku Resources

Themes using the Shizuku-style interface may provide additional resources:

```text
ShizukuBackground-300.png
ShizukuAbout-300.png

ShizukuCopyright-100.png
ShizukuCopyright-125.png
ShizukuCopyright-150.png
ShizukuCopyright-200.png
ShizukuCopyright-250.png
ShizukuCopyright-300.png
```

The reference theme contains `ShizukuAbout-300.png`, `ShizukuBackground-300.png`, and six `ShizukuCopyright` variants.

These resources are not interchangeable with ordinary disk-status assets.

---

# No Parent Theme Required

A Full Theme is intended to be self-contained.

Therefore, it should normally **not depend on `ParentTheme<N>` for its primary resources**.

A standalone Full Theme can use:

```ini
[Info]
Author=My Theme
```

rather than:

```ini
[Info]
Author=My Theme
ParentTheme1=SomeOtherTheme
```

If a theme intentionally inherits resources, it should generally be classified as an **Inherited Theme** rather than a fully standalone Full Theme.

---

# Resource Consistency

All resources must belong to the same visual design system.

For example, if the theme is:

> Cyberpunk neon

then:

```text
diskGood
diskCaution
diskBad
temperatureGood
temperatureBad
logo
volume
navigation
background
```

should all use the same visual language.

Do not generate each resource family as an unrelated illustration.

Maintain consistency in:

* color palette
* lighting
* line style
* rendering style
* character / mascot design
* iconography
* perspective
* visual density
* transparency
* decorative elements

---

# Status Consistency

Related states should be visually distinguishable.

At minimum, the following semantic distinction should remain clear:

```text
Good
GoodGreen
Caution
Bad
Unknown
```

For example:

```text
Good       → normal / healthy
GoodGreen  → healthy / positive variant
Caution    → warning
Bad        → critical
Unknown    → unknown / unavailable
```

The exact artistic representation may vary according to the theme.

A cute character theme could express the states through character expressions.

A cyberpunk theme could express them through colors and warning symbols.

A minimalist theme could express them through simple geometric indicators.

---

# Resolution Consistency

The six size variants are not six independent designs.

They are different resolutions of the same resource.

For example:

```text
diskGood-100.png
diskGood-125.png
diskGood-150.png
diskGood-200.png
diskGood-250.png
diskGood-300.png
```

must represent the same `diskGood` design.

Do not alter the character, icon, composition, or semantic meaning between resolutions.

Higher-resolution assets may contain more detail, but should remain visually equivalent.

---

# Filename Rules

Filenames are part of the CrystalDiskInfo theme resource interface.

**Do not rename resource files.**

Correct:

```text
diskGood-100.png
```

Incorrect:

```text
disk-good-100.png
DiskGood100.png
diskGood_100.png
goodDisk-100.png
```

The resource family name and size suffix must remain exactly as specified.

---

# `theme.ini`

A Full Theme must include:

```text
theme.ini
```

The configuration defines:

* theme metadata
* optional inheritance
* interface colors
* glass color
* glass transparency

See [`theme_ini.md`](./theme_ini.md) for the complete `theme.ini` specification.

---

# Full Theme Generation

When an AI is asked to generate a Full Theme, it should follow this workflow:

```text
Theme Concept
      │
      ▼
Visual Identity
      │
      ├── Color Palette
      ├── Typography / Icon Style
      ├── Character / Mascot
      ├── Lighting
      └── Decorative Elements
      │
      ▼
Generate Resource Families
      │
      ├── Disk Health
      ├── Disk Status
      ├── Temperature
      ├── Volume
      ├── Navigation
      ├── Logo
      └── Shizuku Resources
      │
      ▼
Generate All Required Size Variants
      │
      ▼
Generate theme.ini
      │
      ▼
Validate Filenames
      │
      ▼
Complete Full Theme
```

---

# AI Generation Rules

When generating a Full Theme:

1. Treat the theme as one coherent visual system.
2. Generate all required resource families.
3. Generate all required size variants.
4. Preserve exact filenames.
5. Do not replace missing assets with placeholders.
6. Do not silently omit resource families.
7. Do not use parent themes for resources that the Full Theme is expected to provide itself.
8. Keep all resolution variants visually consistent.
9. Keep status semantics consistent.
10. Ensure `theme.ini` matches the generated visual palette.
11. Ensure the background, logo, icons, indicators, and status graphics belong to the same theme.
12. Validate the final directory against the resource specification before considering generation complete.

---

# Full Theme Checklist

```text
[ ] theme.ini

[ ] diskBad × 6
[ ] diskCaution × 6
[ ] diskGood × 6
[ ] diskGoodGreen × 6
[ ] diskUnknown × 6

[ ] diskBadMini × 6
[ ] diskCautionMini × 6
[ ] diskGoodMini × 6
[ ] diskGoodGreenMini × 6
[ ] diskUnknownMini × 6

[ ] diskStatusBad × 6
[ ] diskStatusCaution × 6
[ ] diskStatusGood × 6
[ ] diskStatusGoodGreen × 6
[ ] diskStatusUnknown × 6

[ ] temperatureBad × 6
[ ] temperatureCaution × 6
[ ] temperatureGood × 6
[ ] temperatureGoodGreen × 6
[ ] temperatureUnknown × 6

[ ] volumeL × 6
[ ] volumeM × 6
[ ] volumeS × 6
[ ] volumeZ × 6

[ ] logo × 6

[ ] nextDisk × 6
[ ] preDisk × 6
[ ] playSound × 6
[ ] selectSound × 6

[ ] ShizukuBackground-300.png
[ ] ShizukuAbout-300.png
[ ] ShizukuCopyright × 6
```

The exact resource set may be extended when additional CrystalDiskInfo resources are identified. A Full Theme should follow the actual resource specification rather than assuming that every theme contains exactly the same files.

---

# Design Principle

A Full Theme is:

> **A complete replacement resource set for the CrystalDiskInfo interface, with every visual component designed as part of one coherent theme.**

Unlike an inherited theme, it should be possible to install the Full Theme without relying on another theme's image resources.
