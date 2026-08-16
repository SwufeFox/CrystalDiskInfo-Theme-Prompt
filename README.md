# CrystalDiskInfo Theme Prompt

> Use AI to design and generate custom themes for [CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo/).

Generate anime, mascot, character, minimalist, dark, or completely original CrystalDiskInfo themes with AI.

The project provides structured specifications that describe CrystalDiskInfo's theme resources, allowing an AI agent to understand **what each asset is, where it is used, and how the assets should work together**.

---

## 📚 Theme Specifications

Choose the specification according to the type of theme you want to create.

### Basic Theme

A character-focused theme consisting of:

- Character / mascot illustrations
- Disk health status illustrations
- A large background
- `theme.ini`

The status illustrations are character assets rather than generic icons.

👉 **[basic_theme.md](./basic_theme.md)**

---

### Minimal Theme

A lightweight theme based on an existing theme.

Instead of duplicating every resource, a Minimal Theme:

```text
Parent Theme
     +
Only the resources you want to change
````

For example:

```text
ShizukuMiko/
├── ...all original resources...
└── theme.ini

ShizukuMikoNight/
├── ShizukuBackground-300.png
└── theme.ini
```

The unchanged resources are inherited from the parent theme.

👉 **[minimal_theme.md](./minimal_theme.md)**

---

### Full Theme

A completely self-contained theme.

A Full Theme provides its own complete set of CrystalDiskInfo visual resources instead of relying on another theme.

```text
Full Theme
├── theme.ini
├── disk resources
├── disk status resources
├── temperature resources
├── volume resources
├── navigation resources
├── logo
├── background
└── other resources
```

👉 **[full_theme.md](./full_theme.md)**

---

### `theme.ini`

The configuration file of a CrystalDiskInfo theme.

It controls things such as:

* Author information
* Parent themes
* UI colors
* Glass color
* Transparency

Example:

```ini
[Info]
Author=My Theme
ParentTheme1=ShizukuMiko

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

👉 **[theme_ini.md](./theme_ini.md)**

---

## 🧩 Which One Should I Use?

| I want to...                          | Use                                      |
| ------------------------------------- | ---------------------------------------- |
| Create a character-based theme        | [`basic_theme.md`](./basic_theme.md)     |
| Modify an existing theme              | [`minimal_theme.md`](./minimal_theme.md) |
| Create a completely independent theme | [`full_theme.md`](./full_theme.md)       |
| Understand `theme.ini`                | [`theme_ini.md`](./theme_ini.md)         |

---

## 🤖 Using with an AI Agent

You can give the corresponding specification to your AI agent together with your theme concept.

For example:

```text
Read basic_theme.md.

Create a CrystalDiskInfo theme based on:
"Summer festival fox girl"

Design:
- one consistent character
- Good100
- Good
- Caution
- Bad
- Unknown
- a 3000×3000 background
- matching theme.ini

Follow the resource names, dimensions, variants,
and generation rules defined in basic_theme.md.
```

For an existing theme:

```text
Read minimal_theme.md and theme_ini.md.

Create a dark variant of ShizukuMiko.

Keep all unchanged resources inherited from ShizukuMiko.
Only generate resources that actually need to change.
```

For a completely new theme:

```text
Read full_theme.md and theme_ini.md.

Create a complete CrystalDiskInfo theme based on:
"Cyberpunk neon city"

Generate the complete resource set defined by the specification.
```

---

## 🎨 Design Philosophy

The goal is not simply to generate a collection of images.

A good CrystalDiskInfo theme should feel like:

> **one character, one world, and one coherent visual language.**

Character illustrations, status states, backgrounds, colors, and UI
elements should all belong to the same theme.

---

## 📖 Specifications

* [`basic_theme.md`](./basic_theme.md)
* [`minimal_theme.md`](./minimal_theme.md)
* [`full_theme.md`](./full_theme.md)
* [`theme_ini.md`](./theme_ini.md)

---

## CrystalDiskInfo

This project provides prompts and specifications for creating themes for
[CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo/).

CrystalDiskInfo is developed by **hiyohiyo**.
