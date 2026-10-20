# Milcal

**Milcal** 是一个基于Mlithm网页查分器开发的原生 Android **Milthm 查分器**。它可以从设备上的 Milthm 存档中读取成绩，
也可以通过 Milkloud 账号联网查询，并按官方公式计算单曲 Reality 与总 Reality（Best 20）。

> 使用 Java + 原生 Android View 编写，无第三方 UI 框架，包体轻量、启动快速。

[![Platform](https://img.shields.io/badge/platform-Android-3DDC84.svg)](#)
[![minSdk](https://img.shields.io/badge/Android-10%2B%20(API%2029)-3DDC84.svg)](#)
[![Version](https://img.shields.io/badge/version-0.3.2-orange.svg)](CHANGELOG.md)

## 功能

| 功能 | 说明 |
| --- | --- |
| 手动读取存档 | 通过系统文件选择器导入 `saves.db` / `data.db` / `PlayerFile` / XML / `.reg` / 文本 / PNG |
| Root 读取 | 通过 `su` 读取官方包与 TapTap 包（`com.morizero.milthm` / `game.taptap.morizero.milthm`）的内部与外置存档目录 |
| ADB（Shizuku）读取 | 通过 Shizuku 以 adb 权限读取，**无需 root** |
| Milkloud 联网查分 | 使用 Milkloud 令牌查询触摸端 / 键盘端 / 混合 / 自动成绩 |
| 数据持久化 | 每次导入 / 查分后都会记住成绩，下次启动自动恢复，无需重新读取 |
| 成绩页 | 顶部头图（名字 + `Reality` 数值 + 星标 + 查询时间）+ 成绩卡片网格（手机 2 列 / 平板 4-5 列），评级使用 Milthm 评级素材，支持「看 Best 20」与「生成查分图」 |
| 查分图 | 生成 PNG 保存到相册并可分享，横向 4 列版式，头图按比例顶部裁剪不拉伸 |
| 外观 | 深色模式、8 种主题色、相册自定义背景（PNG / JPG / **GIF 动图**）、胶囊开关 |
| 侧边栏 Dock | 全高导航栏，背景随导入图片呈现磨砂玻璃效果并跟随深浅色，手机 / 平板自适应 |
| 关于 | 展示版本与数据来源，附作者社交链接 |

> 完整功能说明见 [`docs/README.md`](docs/README.md)。

## 截图

> 占位：欢迎 PR 补充截图，建议放入 `docs/screenshots/` 并在下方引用。
>
> ```markdown
> | 首页 | 成绩页 | 查分图 | 深色模式 |
> | --- | --- | --- | --- |
> | ![](docs/screenshots/home.png) | ![](docs/screenshots/score.png) | ![](docs/screenshots/share.png) | ![](docs/screenshots/dark.png) |
> ```

## 环境要求

- **JDK** 17+（已在 JDK 22 上验证）
- **Android SDK**：`compileSdk 34`、`build-tools 34.0.0`
- **Gradle** 8.9（可直接使用仓库内的 `gradlew`）
- 运行环境：**Android 10（API 29）** 及以上


## 目录结构（未完善）

```
app/src/main/java/com/milcal/app/
├── core/     # 解析、Reality 计算、曲库、评级素材等业务核心
├── image/    # 查分图渲染（ScoreImageRenderer）与高斯模糊（BlurUtil）
├── model/    # 数据模型（成绩、谱面信息、用户数据）
├── net/      # Milkloud 客户端与令牌管理
├── source/   # 存档读取来源：手动 / Root / Shizuku(ADB)
└── ui/       # Activity、主题、页面与对话框
```

## 文档

- [`docs/architecture.md`](docs/architecture.md) — 代码结构与数据流
- [`docs/reality-formula.md`](docs/reality-formula.md) — Reality 评分公式
- [`docs/save-formats.md`](docs/save-formats.md) — 支持的存档格式
- [`docs/milkloud-api.md`](docs/milkloud-api.md) — Milkloud 接口
- [`docs/assets.md`](docs/assets.md) — 资源生成（`tools/gen_assets.py`）


## 免责声明

- 本项目为个人非官方工具，与 Milthm 官方及 Milkloud 团队**无任何关联**。
- 游戏名称、曲绘、评级素材等一切与 Milthm 相关的资源，其版权归**原权利方**所有，本项目仅用于
  学习交流与数据展示，请勿用于商业用途。
- Root / Shizuku 读取会以更高权限访问设备上的存档文件，请自行评估风险。

## 作者

**纸喵橘柚**（Lazy-nya）

- GitHub：<https://github.com/Lazy-nya>
- 哔哩哔哩：<https://space.bilibili.com/626182490>
  
## 相关连接
- MilthmCalc：<https://mhtlim.top/>
