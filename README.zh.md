# CrystalDiskInfo Theme Prompt

[English](./README.md) | [简体中文](./README.zh.md)

> 让 AI 帮你做 CrystalDiskInfo 主题。

一套用于教会 AI Agent 如何制作
[CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo/) 主题的规范。

你只需要描述：

**“我想要什么主题。”**

剩下的交给 AI。

---

## 🤖 怎么用？

把 **[`AGENT.md`](./AGENT.md)** 直接丢给你的 AI Agent。

然后告诉它你想要什么。

例如：

```text
帮我做一个可爱的小狐狸主题的 CrystalDiskInfo。

要求：
- 同一个角色
- Good / Caution / Bad / Unknown 有不同的表情
- 一个匹配的背景
- 整体风格可爱
````

就这样。

Agent 会读取 `AGENT.md`，并根据需要使用对应的主题规范，
然后生成主题。

也可以让 AI 基于现有主题修改：

```text
帮我做一个 ShizukuMiko 的深色版本。

只修改背景和颜色。
能够继承的资源不要复制。
```

---

## 📚 规范

| 文件                                       | 用途                |
| ---------------------------------------- | ----------------- |
| [`AGENT.md`](./AGENT.md)                 | AI Agent 的入口      |
| [`basic_theme.md`](./basic_theme.md)     | 角色型主题             |
| [`minimal_theme.md`](./minimal_theme.md) | 基于现有主题修改          |
| [`full_theme.md`](./full_theme.md)       | 完整独立主题            |
| [`theme_ini.md`](./theme_ini.md)         | `theme.ini` 与主题继承 |

### Basic Theme

以角色 / Mascot 为核心的主题。

包含状态角色立绘、背景等资源。

### Minimal Theme

基于已有主题，只修改需要修改的部分。

```text
父主题
  +
修改的资源
  =
Minimal Theme
```

### Full Theme

完整、自包含的主题。

不依赖其他主题提供资源。

---

## 📂 安装主题

将生成好的主题放到：

```text
<software>\CdiResource\themes\<theme name>\
```

例如：

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

然后在 CrystalDiskInfo 中选择对应主题即可。

---

## 🧠 给 AI 用

这个仓库是一个 **AI-first** 项目。

人类不需要记住 CrystalDiskInfo 的各种资源名称、
尺寸变体和继承规则。

只需要把：

```text
AGENT.md
```

交给你的 Agent。

Agent 会把其他 `.md` 规范作为自己的主题制作知识库。

---

## ✨ 核心理念

不要为了改一个背景就复制整个主题。

不要让五张状态立绘看起来像五个完全不同的作品。

不要手动记住一大堆 CrystalDiskInfo 文件名。

而是：

> **描述你想要的主题，让 Agent 处理剩下的一切。**

一个角色。

一个世界。

一套统一的视觉语言。

---

## ⭐ 参与贡献

欢迎贡献：

* 更完善的资源说明
* 新的主题示例
* 更好的 AI 生成规则
* 对现有规范的修正
* 新的主题类型

欢迎提交 Pull Request！

---

## 📄 License

详见仓库 License。

CrystalDiskInfo 由 **hiyohiyo** 开发。
