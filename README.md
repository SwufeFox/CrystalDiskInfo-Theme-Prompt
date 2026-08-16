# CrystalDiskInfo Theme Prompt

[English](./README.md) | [简体中文](./README.zh.md)

> Let AI make your CrystalDiskInfo theme.

A collection of specifications that teaches AI agents how to create
custom [CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo/) themes.

You describe what you want.

**The AI figures out the rest.**

---

## 🤖 How to Use

Give **[`AGENT.md`](./AGENT.md)** to your AI agent.

Then simply tell it what kind of theme you want.

For example:

```text
Create a CrystalDiskInfo theme based on a cute fox girl.

I want:
- a consistent character
- different expressions for Good / Caution / Bad / Unknown
- a matching background
- a cute visual style
````

That's it.

The agent will read `AGENT.md` and the relevant specifications,
then generate the theme accordingly.

You can also ask it to modify an existing theme:

```text
Create a dark variant of ShizukuMiko.

Only change the background and colors.
Don't duplicate resources that can be inherited.
```

---

## 📚 Specifications

| File                                     | Description                       |
| ---------------------------------------- | --------------------------------- |
| [`AGENT.md`](./AGENT.md)                 | Entry point for AI agents         |
| [`basic_theme.md`](./basic_theme.md)     | Character-focused themes          |
| [`minimal_theme.md`](./minimal_theme.md) | Themes based on an existing theme |
| [`full_theme.md`](./full_theme.md)       | Completely self-contained themes  |
| [`theme_ini.md`](./theme_ini.md)         | `theme.ini` and theme inheritance |

### Basic Theme

Character-focused themes with status illustrations and a background.

### Minimal Theme

Reuse an existing theme and override only what you want to change.

```text
Parent Theme
     +
Changed Resources
     =
Minimal Theme
```

### Full Theme

A completely independent theme containing its own resources.

---

## 📂 Installing a Theme

Place the generated theme under:

```text
<software>\CdiResource\themes\<theme name>\
```

For example:

```text
CrystalDiskInfo/
└── CdiResource/
    └── themes/
        └── MyTheme/
            ├── theme.ini
            ├── SDdiskStatusGood100-100.png
            ├── ...
            └── ShizukuBackground-300.png
```

Then select the theme from CrystalDiskInfo.

---

## 🧠 For AI Agents

This repository is designed to be **AI-first**.

Humans don't need to understand every CrystalDiskInfo resource name,
image variant, or inheritance rule.

Just provide:

```text
AGENT.md
```

to your agent.

The agent can then use the other specification files as its knowledge
base.

---

## ✨ Philosophy

Don't manually draw every CrystalDiskInfo asset.

Don't copy an entire theme just to change one background.

Don't make five completely unrelated character illustrations.

Instead:

> **Describe the theme. Let the agent handle the format.**

One character.

One world.

One coherent visual language.

---

## ⭐ Contributing

Feel free to contribute:

* Better resource documentation
* New theme examples
* Better AI generation rules
* Corrections to existing specifications
* New theme types

Pull requests are welcome!

---

## 📄 License

See the repository license for details.

CrystalDiskInfo is developed by **hiyohiyo**.
