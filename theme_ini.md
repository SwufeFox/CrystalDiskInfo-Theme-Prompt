# Theme Inheritance

CrystalDiskInfo themes may inherit resources from one or more parent themes.

Parent themes are specified in the `[Info]` section using the sequential keys:

```ini
ParentTheme1=ThemeA
ParentTheme2=ThemeB
ParentTheme3=ThemeC
```

The `ParentTheme<N>` entries are **optional and ordered**.

## `ParentTheme<N>`

The general form is:

```ini
ParentTheme<N>=<ThemeName>
```

where `<N>` is a positive integer starting from `1`.

For example:

```ini
[Info]
Author=My Theme
ParentTheme1=ShizukuMiko
ParentTheme2=ShizukuHotaru
```

### Optional

A theme does not need to specify any parent theme.

A completely standalone theme may simply use:

```ini
[Info]
Author=My Theme
```

A derived theme may specify one or more parents:

```ini
[Info]
Author=My Theme
ParentTheme1=ShizukuMiko
```

Additional parents can be added when necessary:

```ini
[Info]
Author=My Theme
ParentTheme1=ShizukuMiko
ParentTheme2=ShizukuHotaru
ParentTheme3=AnotherTheme
```

## Ordering

Parent themes are **ordered**.

`ParentTheme1` has higher priority than `ParentTheme2`, which has higher priority than `ParentTheme3`, and so on.

Therefore:

```ini
ParentTheme1=ThemeA
ParentTheme2=ThemeB
```

is not equivalent to:

```ini
ParentTheme1=ThemeB
ParentTheme2=ThemeA
```

When resolving an inherited resource, the parent themes should be considered in their declared order.

Conceptually:

```text
Current Theme
      │
      ├── ParentTheme1  ← highest parent priority
      │
      ├── ParentTheme2
      │
      ├── ParentTheme3
      │
      └── ...
```

The current theme itself takes precedence over its parents.

## Sequential Numbering

`ParentTheme<N>` entries form a sequential list.

Valid:

```ini
ParentTheme1=ThemeA
ParentTheme2=ThemeB
ParentTheme3=ThemeC
```

Valid:

```ini
ParentTheme1=ThemeA
```

Valid:

```ini
[Info]
Author=My Theme
```

Invalid:

```ini
ParentTheme1=ThemeA
ParentTheme3=ThemeC
```

because `ParentTheme2` is missing.

Do not skip numbers when declaring parent themes.

## Resource Resolution

A theme can be viewed as a layered resource set:

```text
                    Current Theme
                         │
                         ▼
                 ┌───────────────┐
                 │ Local Resource│
                 └───────┬───────┘
                         │
                    not found?
                         ▼
                 ┌───────────────┐
                 │ ParentTheme1  │
                 └───────┬───────┘
                         │
                    not found?
                         ▼
                 ┌───────────────┐
                 │ ParentTheme2  │
                 └───────┬───────┘
                         │
                    not found?
                         ▼
                       ...
```

This allows a theme to override only the resources it actually changes.

For example:

```text
ShizukuMiko/
├── SDdiskStatusBad-100.png
├── ...
├── SDdiskStatusUnknown-300.png
├── ShizukuBackground-300.png
└── theme.ini

ShizukuMikoNight/
├── ShizukuBackground-300.png
└── theme.ini
```

`ShizukuMikoNight/theme.ini` may contain:

```ini
[Info]
Author=...
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

The local `ShizukuBackground-300.png` overrides the parent's background, while the status images can be inherited from `ShizukuMiko`.

## AI Generation Rules

When generating `ParentTheme<N>` entries:

1. `ParentTheme<N>` is optional.
2. Parent themes must be numbered starting from `1`.
3. Parent numbers must be sequential.
4. Parent order is significant.
5. Do not reorder parents unless explicitly requested.
6. Do not create unnecessary parent relationships.
7. Prefer the most relevant parent as `ParentTheme1`.
8. Use additional parents only when they provide resources that are actually needed.
9. Do not copy inherited resources into the current theme unnecessarily.
10. A theme with no inheritance should omit all `ParentTheme<N>` entries.

The general rule is:

> **Local resources override inherited resources; inherited resources are resolved in `ParentTheme<N>` order.**
