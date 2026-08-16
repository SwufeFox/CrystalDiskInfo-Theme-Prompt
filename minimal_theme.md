# CrystalDiskInfo Minimal Theme

A **Minimal Theme** is a lightweight CrystalDiskInfo theme that inherits most of its resources from one or more parent themes and only provides the resources that need to be changed.

The purpose of a Minimal Theme is to create a new visual variant without duplicating resources that already exist in an existing theme.

---

## Concept

A Minimal Theme should contain only:

1. `theme.ini`
2. Resources that intentionally override inherited resources

Everything else should be inherited from the parent theme.

For example:

```text
ShizukuMiko/
├── SDdiskStatusBad-100.png
├── SDdiskStatusBad-125.png
├── ...
├── SDdiskStatusUnknown-300.png
├── ShizukuBackground-300.png
└── theme.ini
````

A dark variant can be:

```text
ShizukuMikoNight/
├── ShizukuBackground-300.png
└── theme.ini
```

The new theme does not need to copy the status images from `ShizukuMiko`.

---

# Minimal Theme Structure

The general structure is:

```text
Minimal Theme
├── theme.ini
└── [overridden resources]
```

The overridden resources are optional.

Therefore, a Minimal Theme may contain only:

```text
theme.ini
```

if its only purpose is to change configuration such as colors.

It may also contain one or more image resources:

```text
MyTheme/
├── theme.ini
└── ShizukuBackground-300.png
```

---

# Parent Theme

A Minimal Theme should normally specify at least one parent theme.

Example:

```ini
[Info]
Author=My Theme
ParentTheme1=ShizukuMiko
```

`ParentTheme1` identifies the primary source of inherited resources.

Additional parent themes may be specified:

```ini
[Info]
Author=My Theme
ParentTheme1=ShizukuMiko
ParentTheme2=ShizukuHotaru
```

Parent themes are:

* optional
* ordered
* sequentially numbered

See [`theme_ini.md`](./theme_ini.md) for the complete inheritance specification.

---

# Resource Override

A resource existing in the Minimal Theme overrides the corresponding inherited resource.

For example, if the parent theme contains:

```text
ShizukuBackground-300.png
```

and the child theme also contains:

```text
ShizukuBackground-300.png
```

the child theme's resource is the one intended for the new theme.

Conceptually:

```text
Parent Theme
│
├── SDdiskStatusBad-100.png
├── SDdiskStatusBad-125.png
├── ...
├── SDdiskStatusUnknown-300.png
└── ShizukuBackground-300.png
             │
             │ inherited
             ▼
Minimal Theme
├── theme.ini
└── ShizukuBackground-300.png
          ▲
          │
       override
```

The child theme therefore only needs to contain the resources that are different.

---

# Typical Minimal Theme

A common use case is creating a dark or light variant of an existing theme.

For example:

```text
ShizukuMikoNight/
├── ShizukuBackground-300.png
└── theme.ini
```

with:

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

This theme changes:

* the background
* interface colors
* glass color
* glass transparency

while reusing the parent's status and UI assets.

---

# Do Not Duplicate Inherited Resources

The primary rule of a Minimal Theme is:

> **Do not copy a resource unless you intend to change it.**

For example, if `ShizukuMiko` already provides:

```text
SDdiskStatusGood-100.png
SDdiskStatusGood-125.png
SDdiskStatusGood-150.png
SDdiskStatusGood-200.png
SDdiskStatusGood-250.png
SDdiskStatusGood-300.png
```

and the new theme does not change these images, do not copy them.

Avoid:

```text
MyTheme/
├── SDdiskStatusGood-100.png
├── SDdiskStatusGood-125.png
├── SDdiskStatusGood-150.png
├── SDdiskStatusGood-200.png
├── SDdiskStatusGood-250.png
├── SDdiskStatusGood-300.png
├── ...
└── theme.ini
```

Prefer:

```text
MyTheme/
├── ShizukuBackground-300.png
└── theme.ini
```

---

# What Can Be Overridden?

Any resource that is intentionally different from the parent theme may be included in the Minimal Theme.

Examples include:

```text
ShizukuBackground-300.png
logo-300.png
diskGood-300.png
diskStatusGood-300.png
temperatureGood-300.png
```

If only one resolution needs to be changed, only that resolution needs to be provided.

For example:

```text
MyTheme/
├── theme.ini
└── logo-300.png
```

The other logo resolutions can remain inherited.

---

# Partial Resource Families

A Minimal Theme does **not** have to provide a complete resource family.

For example, if only the `300` version of `logo` is changed:

```text
logo-300.png
```

is sufficient.

There is no requirement to also provide:

```text
logo-100.png
logo-125.png
logo-150.png
logo-200.png
logo-250.png
```

unless those resources are also intentionally modified.

This is one of the main differences between a Minimal Theme and a Full Theme.

---

# Configuration-Only Theme

A Minimal Theme may contain no image resources at all.

For example:

```text
MyDarkTheme/
└── theme.ini
```

with:

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

This creates a configuration-only variant that inherits all image resources from its parent.

---

# Minimal Theme vs Full Theme

|                      | Minimal Theme            | Full Theme            |
| -------------------- | ------------------------ | --------------------- |
| `theme.ini`          | Required                 | Required              |
| Parent theme         | Normally required        | Normally unnecessary  |
| Image resources      | Only changed resources   | Complete resource set |
| Inherited resources  | Yes                      | No                    |
| Resource duplication | Avoided                  | Expected              |
| Typical size         | Small                    | Large                 |
| Main purpose         | Variants / modifications | Independent themes    |

A useful rule is:

```text
Full Theme
= complete resource set

Minimal Theme
= parent theme + changes only
```

---

# Recommended Generation Strategy

When generating a Minimal Theme from an existing theme:

```text
Existing Theme
      │
      ▼
Identify desired changes
      │
      ├── Background?
      ├── Colors?
      ├── Logo?
      ├── Status graphics?
      └── Other resources?
      │
      ▼
Keep unchanged resources inherited
      │
      ▼
Generate only changed resources
      │
      ▼
Generate theme.ini
      │
      ▼
Minimal Theme
```

The AI should first determine **what actually changes**.

It should not regenerate the entire parent theme.

---

# AI Generation Rules

When generating a Minimal Theme:

1. Identify a suitable parent theme.
2. Set it as `ParentTheme1`.
3. Add additional parents only when necessary.
4. Preserve the order of parent themes.
5. Identify which resources actually need to change.
6. Generate only those resources.
7. Do not duplicate unchanged resources.
8. Do not generate unnecessary resolution variants.
9. Keep exact CrystalDiskInfo filenames.
10. Keep all overridden resources visually consistent with the parent theme.
11. Generate `theme.ini` with the appropriate color and alpha values.
12. Keep inherited resources untouched.
13. Prefer the smallest valid resource set.

---

# Minimal Theme Philosophy

A Minimal Theme should follow:

> **Inherit everything. Override only what changes.**

For example:

```text
                     ShizukuMiko
                          │
            ┌─────────────┴─────────────┐
            │                           │
      inherited assets             inherited config
            │                           │
            ▼                           ▼
      ┌────────────────────────────────────┐
      │        ShizukuMikoNight            │
      │                                    │
      │  + new background                  │
      │  + new colors                     │
      │  + new alpha                      │
      └────────────────────────────────────┘
```

The result is a small theme that reuses an existing visual foundation while allowing targeted customization.

---

# Validation Checklist

Before considering a Minimal Theme complete:

* [ ] `theme.ini` exists
* [ ] A suitable `ParentTheme<N>` is specified when inheritance is required
* [ ] Parent theme numbering is sequential
* [ ] Parent theme order is intentional
* [ ] Only intentionally changed resources are included
* [ ] Unchanged resources are not duplicated
* [ ] All filenames exactly match CrystalDiskInfo's resource names
* [ ] Overridden resources remain visually compatible with the parent theme
* [ ] `theme.ini` contains the intended color and alpha configuration
* [ ] The theme remains functional using inherited resources

A Minimal Theme should be **the smallest set of files necessary to express the intended changes**.
