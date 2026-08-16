# CrystalDiskInfo `theme.ini`

`theme.ini` defines the metadata, colors, transparency, and inheritance
rules of a CrystalDiskInfo theme.

A minimal example is:

```ini
[Info]
Author=YourName

[Color];RGB
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
````

---

# `[Info]`

The `[Info]` section contains theme metadata and optional parent-theme
definitions.

## `Author`

Specifies the theme author.

```ini
[Info]
Author=YourName
```

---

## `ParentTheme<N>`

Specifies an optional parent theme.

```ini
[Info]
Author=YourName
ParentTheme1=ShizukuMiko
ParentTheme2=ShizukuHotaru
```

Parent themes are:

* optional
* ordered
* sequential

The numbering starts at `1`.

Valid:

```ini
ParentTheme1=ThemeA
ParentTheme2=ThemeB
ParentTheme3=ThemeC
```

Invalid:

```ini
ParentTheme1=ThemeA
ParentTheme3=ThemeC
```

because `ParentTheme2` is missing.

---

# Parent Theme Resolution

Parent themes are searched in order.

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

The current theme has priority over all parent themes.

If a resource is not present in the current theme, it may be obtained
from the first parent theme that provides it.

For example:

```text
ShizukuMiko
├── character resources
├── theme.ini
└── background

ShizukuMikoNight
├── theme.ini
└── background
```

If `ShizukuMikoNight` specifies:

```ini
[Info]
ParentTheme1=ShizukuMiko
```

and does not contain the character resources, those resources can be
inherited from `ShizukuMiko`.

This allows a theme to override only the resources it actually changes.

---

# `[Color]`

The `[Color]` section defines the theme's UI colors.

The values use RGB hexadecimal notation.

```ini
[Color];RGB
LabelText=0x000000;
ButtonText=0x000000;
ListText1=0x000000;
ListText2=0x000000;
ListBk1=0xFFFFFF;
ListBk2=0xF8F8F8;
ListLine1=0xE0E0E0;
ListLine2=0xF0F0F0;
Glass=0xFFFFFF;
```

The supported entries are:

| Key          | Purpose                      |
| ------------ | ---------------------------- |
| `LabelText`  | Label text color             |
| `ButtonText` | Button text color            |
| `ListText1`  | First list text color        |
| `ListText2`  | Second list text color       |
| `ListBk1`    | First list background color  |
| `ListBk2`    | Second list background color |
| `ListLine1`  | First list line color        |
| `ListLine2`  | Second list line color       |
| `Glass`      | Glass / translucent UI color |

For example, a dark theme may use:

```ini
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
```

---

# `[Alpha]`

The `[Alpha]` section controls transparency.

```ini
[Alpha]
GlassAlpha=128;
```

## `GlassAlpha`

Controls the alpha value used by the glass UI.

The value is an integer alpha value.

For example:

```ini
GlassAlpha=128;
```

represents a partially transparent glass effect.

---

# Minimal `theme.ini`

A minimal standalone theme can look like:

```ini
[Info]
Author=YourName

[Color];RGB
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

---

# Theme with Inheritance

A Minimal Theme can specify parent themes:

```ini
[Info]
Author=YourName
ParentTheme1=ShizukuMiko
ParentTheme2=ShizukuHotaru

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

This theme can inherit resources from its parent themes while overriding
its own color configuration.

---

# AI Rules

When creating `theme.ini`:

1. Preserve the section names exactly.
2. Preserve supported key names exactly.
3. Use RGB hexadecimal values in `[Color]`.
4. Treat `ParentTheme<N>` as optional.
5. Parent theme numbers must be sequential.
6. Parent theme order matters.
7. The current theme takes priority over inherited resources.
8. Do not add parent themes merely to avoid generating resources when a
   Full Theme is requested.
9. Use inheritance when creating a Minimal Theme.
10. Do not invent undocumented keys.

---

# Validation Checklist

* [ ] `[Info]` exists
* [ ] `Author` is specified where appropriate
* [ ] `ParentTheme<N>` numbering is sequential
* [ ] Parent theme order is intentional
* [ ] `[Color]` uses valid RGB values
* [ ] `[Alpha]` is correctly defined
* [ ] No unsupported keys were invented
* [ ] The inheritance model matches the selected theme type
