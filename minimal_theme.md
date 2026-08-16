# CrystalDiskInfo Minimal Theme

A Minimal Theme is a CrystalDiskInfo theme that inherits resources from
one or more existing themes and only provides the resources that it
changes.

This avoids duplicating unchanged assets.

---

## Basic Concept

A Minimal Theme consists of:

```text
Parent Theme
     +
Changed Resources
     +
theme.ini
     =
Minimal Theme
````

For example:

```text
ShizukuMiko/
├── theme.ini
├── SDdiskStatusGood-300.png
├── ...
└── ShizukuBackground-300.png

ShizukuMikoNight/
├── theme.ini
└── ShizukuBackground-300.png
```

`ShizukuMikoNight` does not need to contain all of the character
resources from `ShizukuMiko`.

Those resources are inherited from the parent theme.

---

# Parent Themes

Parent themes are specified in `theme.ini`:

```ini
[Info]
Author=My Theme
ParentTheme1=ShizukuMiko
ParentTheme2=ShizukuHotaru
```

Parent themes are:

* optional
* ordered
* sequential

`ParentTheme1` has higher priority than `ParentTheme2`.

Additional parent themes may be specified using the next sequential
number:

```ini
ParentTheme1=ThemeA
ParentTheme2=ThemeB
ParentTheme3=ThemeC
```

Do not skip numbers.

For example, this is invalid:

```ini
ParentTheme1=ThemeA
ParentTheme3=ThemeC
```

If the requested resource is not provided by the current theme,
CrystalDiskInfo can resolve it through the parent theme chain.

---

# Resource Override

A resource included directly in the Minimal Theme overrides an
inherited resource with the same filename.

For example:

```text
Parent:
ShizukuBackground-300.png

Child:
ShizukuBackground-300.png
```

The child's `ShizukuBackground-300.png` replaces the parent's version.

Unchanged resources should not be copied into the child theme.

---

# Character Resources

Character status resources follow the same inheritance principle.

For example, if a child theme only changes the `Good` character:

```text
MyTheme/
├── theme.ini
├── SDdiskStatusGood-300.png
├── SDdiskStatusGood-250.png
├── SDdiskStatusGood-200.png
├── SDdiskStatusGood-150.png
├── SDdiskStatusGood-125.png
└── SDdiskStatusGood-100.png
```

All other status resources can remain inherited from the parent.

However, the character variants must still be generated from a single
master artwork.

---

# Master Artwork Rule

When overriding a resource family with multiple size variants, generate
the highest-resolution master first.

For character resources:

```text
-300
```

is the master artwork.

The required dimensions are:

| Suffix | Canvas Size |
| ------ | ----------: |
| `-300` |   384 × 576 |
| `-250` |   320 × 480 |
| `-200` |   256 × 384 |
| `-150` |   192 × 288 |
| `-125` |   160 × 240 |
| `-100` |   128 × 192 |

Do not independently generate all six images.

Use:

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

This ensures that every variant is derived from exactly the same
artwork.

---

# Example: Changing One Character

Suppose the parent theme contains:

```text
ShizukuMiko/
├── SDdiskStatusGood100-300.png
├── SDdiskStatusGood100-250.png
├── ...
├── SDdiskStatusGood-300.png
├── ...
├── SDdiskStatusCaution-300.png
├── ...
└── ShizukuBackground-300.png
```

The user wants to change only the `Good` character.

The Minimal Theme should contain only:

```text
MyTheme/
├── theme.ini
├── SDdiskStatusGood-300.png
├── SDdiskStatusGood-250.png
├── SDdiskStatusGood-200.png
├── SDdiskStatusGood-150.png
├── SDdiskStatusGood-125.png
└── SDdiskStatusGood-100.png
```

The remaining resources are inherited.

---

# Example: Changing Only the Background

If the user wants to create a dark background variant:

```text
MyTheme/
├── theme.ini
└── ShizukuBackground-300.png
```

No character resources need to be copied.

The child theme inherits all character resources from its parent.

---

# Multiple Parent Themes

Multiple parent themes can be useful when a theme is assembled from
different resource sets.

For example:

```ini
[Info]
Author=My Theme
ParentTheme1=ShizukuMiko
ParentTheme2=ShizukuHotaru
```

The parent order matters.

Resources from earlier parents have priority over resources from later
parents.

The current theme always takes priority over inherited resources.

Conceptually:

```text
Current Theme
      ↓
ParentTheme1
      ↓
ParentTheme2
      ↓
ParentTheme3
      ↓
...
```

When resolving a resource, search from the current theme through the
parent chain in order.

---

# Minimal Theme Workflow

When creating a Minimal Theme:

```text
Existing Theme
      ↓
Identify what needs to change
      ↓
Declare parent theme(s)
      ↓
Generate only changed resources
      ↓
For multi-size assets:
    generate master
          ↓
    derive variants with Python
      ↓
Create / update theme.ini
      ↓
Validate inheritance
```

Do not rebuild the entire parent theme.

---

# AI Generation Rules

When generating a Minimal Theme:

1. Identify the parent theme.
2. Determine which resources actually need to change.
3. Do not duplicate unchanged resources.
4. Add the parent theme to `theme.ini`.
5. Generate only the overridden resources.
6. For multi-size character resources, generate the `-300` master first.
7. Generate smaller variants programmatically from the master.
8. Preserve transparency for character resources.
9. Preserve exact resource filenames.
10. Verify that all required inherited resources remain available through
    the parent chain.
11. Verify the parent order.
12. Keep the Minimal Theme as small as possible.

---

# Installation

A Minimal Theme is installed in the same way as any other CrystalDiskInfo
theme:

```text
<software>\CdiResource\themes\<theme name>\
```

For example:

```text
CrystalDiskInfo/
└── CdiResource/
    └── themes/
        ├── ShizukuMiko/
        └── ShizukuMikoNight/
            ├── theme.ini
            └── ShizukuBackground-300.png
```

The parent theme must also be available to CrystalDiskInfo.

---

# Validation Checklist

Before considering a Minimal Theme complete:

* [ ] `theme.ini` exists
* [ ] At least one valid parent theme is specified when inheritance is
  required
* [ ] `ParentTheme1`, `ParentTheme2`, etc. are sequential
* [ ] Parent order is intentional
* [ ] Changed resources exist in the child theme
* [ ] Unchanged resources are not unnecessarily duplicated
* [ ] Multi-size character resources have a `-300` master
* [ ] `-300` character masters are 384 × 576
* [ ] `-250` variants are 320 × 480
* [ ] `-200` variants are 256 × 384
* [ ] `-150` variants are 192 × 288
* [ ] `-125` variants are 160 × 240
* [ ] `-100` variants are 128 × 192
* [ ] Smaller variants were derived from their corresponding master
* [ ] Character resources preserve transparency
* [ ] All inherited resources can be resolved through the parent chain
* [ ] The theme can be installed under
  `<software>\CdiResource\themes\<theme name>\`
