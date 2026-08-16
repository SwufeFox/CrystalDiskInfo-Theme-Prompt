# CrystalDiskInfo Theme Prompt

[简体中文](./README.zh.md) | [English](./README.md)

> Let AI make your CrystalDiskInfo theme.

A set of specifications for teaching AI agents how to create custom
[CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo/) themes.

You describe what you want.

**The AI handles the rest.**

---

## 🤖 How to Use

Give **[`AGENT.md`](./AGENT.md)** to your AI agent.

Then describe the theme you want.

For example:

```text
Create a CrystalDiskInfo theme based on a cute fox girl.

I want:
- the same character throughout the theme
- different expressions and poses for Good / Caution / Bad / Unknown
- a matching background
- a coherent cute visual style
````

The agent will read `AGENT.md` and the relevant specifications,
then create the required theme resources.

You can also ask it to modify an existing theme:

```text
Create a dark variant of ShizukuMiko.

Only change the background and colors.
Don't duplicate resources that can be inherited.
```

---

## 📚 Specifications

| File                                     | Description                                |
| ---------------------------------------- | ------------------------------------------ |
| [`AGENT.md`](./AGENT.md)                 | Instructions and workflow for AI agents    |
| [`basic_theme.md`](./basic_theme.md)     | Character-focused themes                   |
| [`minimal_theme.md`](./minimal_theme.md) | Themes based on existing themes            |
| [`full_theme.md`](./full_theme.md)       | Completely self-contained themes           |
| [`theme_ini.md`](./theme_ini.md)         | `theme.ini`, colors, alpha and inheritance |

---

## 🎨 Theme Types

### Basic Theme

A character-focused theme with:

* character illustrations
* different expressions / poses for disk states
* a matching background
* `theme.ini`

Character artwork is generated as a high-resolution master first,
then smaller variants are generated programmatically.

### Minimal Theme

Modify an existing theme without copying everything.

```text
Parent Theme
     +
Changed Resources
     =
Minimal Theme
```

This is useful for recolors, alternate backgrounds, seasonal variants,
and other small modifications.

### Full Theme

A completely independent theme containing all resources required by the
theme.

---

## 📂 Installation

Themes must be placed under:

```text
<software>\CdiResource\themes\<theme name>\
```

For example:

```text
CrystalDiskInfo\
└── CdiResource\
    └── themes\
        └── ShizukuMyTheme\
            ├── theme.ini
            ├── ...
            └── ShizukuBackground-300.png
```

### ⚠️ Theme Name Requirement

**The theme directory name must start with `Shizuku`.**

CrystalDiskInfo's theme scanner only recognizes themes whose directory
name begins with:

```text
Shizuku
```

Therefore, use names such as:

```text
ShizukuFox
ShizukuFoxNight
ShizukuMikoNight
ShizukuMyTheme
```

and not:

```text
FoxTheme
MyTheme
NightTheme
```

If the directory does not start with `Shizuku`, CrystalDiskInfo will
not discover it as a theme.

---

## 🔄 Restart CrystalDiskInfo

CrystalDiskInfo does **not** hot-reload themes.

After installing or modifying a theme, restart CrystalDiskInfo for the
changes to take effect.

If a newly created theme does not appear:

1. Check that the theme directory is under
   `CdiResource\themes\`.
2. Check that the directory name starts with `Shizuku`.
3. Restart CrystalDiskInfo.

---

## 🧠 For AI Agents

This repository is designed to be **AI-first**.

Humans do not need to memorize CrystalDiskInfo's resource names,
dimensions, or inheritance rules.

Just give your agent:

```text
AGENT.md
```

The agent can then use the other `.md` files as its specification.

The intended workflow is:

```text
Human describes theme
        ↓
AI reads AGENT.md
        ↓
AI reads relevant specification
        ↓
Generate master artwork
        ↓
Generate derived variants
        ↓
Create theme.ini
        ↓
Validate
        ↓
Install under CdiResource\themes\Shizuku*
        ↓
Restart CrystalDiskInfo
```

---

## ✨ The Idea

Don't manually draw every size variant.

Don't duplicate an entire theme just to change one image.

Don't make six independent generations of the same character.

Instead:

> **Describe the theme. Let the agent handle the format.**

One character.

One world.

One coherent visual language.

---

## ⭐ Contributing

Contributions are welcome!

You can contribute:

* better resource documentation
* new theme examples
* improved AI generation rules
* corrections
* new theme specifications
* generation tools

Pull requests are welcome.

---

## 📄 License

See the repository license for details.

CrystalDiskInfo is developed by **hiyohiyo**.

CrystalDiskInfo is developed by **hiyohiyo**.
