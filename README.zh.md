# CrystalDiskInfo Theme Prompt

[English](./README.md) | [简体中文](./README.zh.md)

> 让 AI 帮你制作 CrystalDiskInfo 主题。

一套用于教会 AI Agent 制作自定义
[CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo/) 主题的规范。

你只需要描述你想要的主题。

**剩下的交给 AI。**

---

## 🤖 怎么用？

把 **[`AGENT.md`](./AGENT.md)** 直接交给你的 AI Agent。

然后告诉它你想要什么主题。

例如：

```text
帮我做一个可爱的小狐狸主题的 CrystalDiskInfo。

要求：
- 整个主题使用同一个角色
- Good / Caution / Bad / Unknown 使用不同的表情和动作
- 有一个匹配的背景
- 整体风格统一、可爱
````

Agent 会读取 `AGENT.md` 和对应的主题规范，
然后生成所需的主题资源。

你也可以让 AI 基于现有主题进行修改：

```text
帮我做一个 ShizukuMiko 的深色版本。

只修改背景和颜色。
能够继承的资源不要复制。
```

---

## 📚 规范

| 文件                                       | 用途                    |
| ---------------------------------------- | --------------------- |
| [`AGENT.md`](./AGENT.md)                 | AI Agent 的总规则与工作流程    |
| [`basic_theme.md`](./basic_theme.md)     | 角色型主题                 |
| [`minimal_theme.md`](./minimal_theme.md) | 基于已有主题修改              |
| [`full_theme.md`](./full_theme.md)       | 完整独立主题                |
| [`theme_ini.md`](./theme_ini.md)         | `theme.ini`、颜色、透明度与继承 |

---

## 🎨 主题类型

### Basic Theme

以角色为核心的主题，包括：

* 角色立绘
* 不同磁盘状态对应的表情 / 动作
* 匹配的背景
* `theme.ini`

角色图片首先生成最高规格的 Master Artwork，
再通过程序生成其他尺寸。

### Minimal Theme

基于已有主题，只修改需要修改的部分。

```text
父主题
  +
修改的资源
  =
Minimal Theme
```

适合：

* 换色
* 更换背景
* 夜间版本
* 季节版本
* 其他小规模修改

### Full Theme

完全独立的主题。

主题本身包含所需的全部资源，不依赖其他主题提供资源。

---

## 📂 安装

将主题放置到：

```text
<software>\CdiResource\themes\<theme name>\
```

例如：

```text
CrystalDiskInfo\
└── CdiResource\
    └── themes\
        └── ShizukuMyTheme\
            ├── theme.ini
            ├── ...
            └── ShizukuBackground-300.png
```

### ⚠️ 主题名称要求

**主题目录名必须以 `Shizuku` 开头。**

CrystalDiskInfo 的主题扫描器只会识别目录名以：

```text
Shizuku
```

开头的主题。

因此应该使用：

```text
ShizukuFox
ShizukuFoxNight
ShizukuMikoNight
ShizukuMyTheme
```

而不是：

```text
FoxTheme
MyTheme
NightTheme
```

如果主题目录名不是以 `Shizuku` 开头，
CrystalDiskInfo 将不会扫描到它。

---

## 🔄 修改后需要重启

CrystalDiskInfo **不支持主题热更新**。

安装主题或者修改主题文件后，需要重新启动 CrystalDiskInfo
才能看到变化。

如果新主题没有出现：

1. 确认主题位于 `CdiResource\themes\` 下。
2. 确认主题目录名以 `Shizuku` 开头。
3. 重启 CrystalDiskInfo。

---

## 🧠 给 AI Agent

这个仓库是一个 **AI-first** 项目。

人类不需要记住 CrystalDiskInfo 的各种资源名称、
尺寸和继承规则。

只需要把：

```text
AGENT.md
```

交给你的 Agent。

Agent 就可以把其他 `.md` 文件作为主题制作规范使用。

完整流程：

```text
人类描述主题
      ↓
AI 读取 AGENT.md
      ↓
AI 读取对应的主题规范
      ↓
生成 Master Artwork
      ↓
生成派生尺寸
      ↓
创建 theme.ini
      ↓
验证
      ↓
安装到 CdiResource\themes\Shizuku*
      ↓
重启 CrystalDiskInfo
```

---

## ✨ 核心理念

不要手动绘制每一个尺寸。

不要为了修改一张图片就复制整个主题。

不要让 AI 独立生成同一个角色的六个尺寸。

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
* 文档修正
* 新的主题规范
* 图片生成 / 处理工具

欢迎提交 Pull Request！

---

## 📄 License

详见仓库 License。

CrystalDiskInfo 由 **hiyohiyo** 开发。
