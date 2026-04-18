# Claude Code Skills 技能集合

这是一个扩展 Claude Code 能力的专用技能集合，涵盖全栈开发、前端设计、音乐生成、浏览器自动化和视频创作等领域。

## 项目结构

```
my-skills/
├── minimax-skill/          # MiniMax AI 相关技能
│   ├── fullstack-dev/      # 全栈开发指南
│   ├── frontend-dev/       # 高品质前端与 UI 设计
│   └── minimax-music-gen/  # 音乐生成
├── usefull/                # 实用工具技能
│   ├── find-skills/        # 从生态中搜索技能
│   ├── skill-creator/      # 创建和改进技能
│   ├── playwright-cli/     # 浏览器自动化
│   └── remotion-best-practices/ # Remotion 视频创作
└── 滚动驱动逐帧播放/        # 滚动驱动逐帧动画
```

---

## 技能概览

### minimax-skill/fullstack-dev

**全栈开发实践**

全面的全栈应用构建指南，涵盖后端架构、前后端集成、数据库模式、认证授权、缓存策略、实时功能和生产环境加固。

**适用场景：**
- 构建全栈应用（Express + React、Django + Vue、Go + HTMX 等）
- 创建 REST API 并配套前端
- 搭建后端服务
- 设计服务层和模块边界
- 实现认证授权、文件上传、实时功能（SSE/WebSocket）
- 生产环境安全加固

**核心主题：**
- 特性优先的项目结构（对比层级优先）
- 类型化错误层级与全局错误处理器
- 数据库访问模式（迁移、N+1 防护、事务）
- API 客户端模式（ typed fetch、React Query、tRPC、OpenAPI codegen）
- 认证中间件（JWT、Session、OAuth、RBAC）
- 实时通信模式（SSE、WebSocket、轮询）
- 后台任务、缓存、文件上传（预签名 URL）

---

### minimax-skill/frontend-dev

**前端工作室**

通过协调五大专业能力构建完整的生产级前端页面：设计工程、动效系统、AI 素材生成、说服力文案和生成式艺术。

**适用场景：**
- 构建落地页、营销站点、产品页、数据仪表盘
- 生成图片/视频/音频/音乐素材
- 创建电影级滚动动画
- 实现生成式艺术

**核心能力：**

1. **设计工程** — Tailwind CSS、Bento 网格布局、创意组件（ Dock 放大、磁性按钮、渐变网格等）

2. **动效引擎** — 动画工具选择矩阵：
   - Framer Motion：UI 入出场/布局动画
   - GSAP + ScrollTrigger：滚动故事化（固定/延迟同步）
   - Three.js/R3F：3D/WebGL 内容
   - Lottie：循环图标动画
   - CSS：悬停/焦点状态、滚动驱动动画

3. **素材生成** — 通过 MiniMax API 生成 AI 素材：
   - 图片、视频、TTS 语音、音乐
   - 所有素材本地保存（无占位图 URL）

4. **文案创作** — 框架：AIDA、PAS、FAB 打造说服力文案

5. **视觉艺术** — p5.js 生成艺术（静态 PDF/PNG 或交互式 HTML）

---

### minimax-skill/minimax-music-gen

**MiniMax 音乐生成**

使用 MiniMax Music API 生成歌曲（人声或器乐）。支持多语言交互和两种创建模式。

**适用场景：**
- 音乐/歌曲创作、音轨生成
- 歌词生成与歌曲创作
- 音频制作或翻唱
- 背景音乐（氛围/场景）

**模式：**

1. **基础模式** — 一句话描述 → 自动生成歌曲
2. **高级模式** — 完全控制歌词、提示词、结构、BPM、风格
3. **翻唱模式** — 基于参考音频生成翻唱版本

**依赖项：**
- `mmx` CLI：`npm install -g mmx-cli`
- 认证：`mmx auth login --api-key <key>`
- 音频播放器（mpv、ffplay 或 macOS afplay）

---

### usefull/find-skills

**查找技能**

从 [skills.sh](https://skills.sh) 开放技能生态中搜索和安装技能。

**适用场景：**
- "怎么实现 X？" 其中 X 可能已有现成技能
- "找个 X 的技能" 或 "有没有 X 的技能？"
- 想扩展 Claude Code 能力
- 搜索工具、模板或工作流

**命令：**
```bash
npx skills find [query]     # 搜索技能
npx skills add <package>    # 安装技能
npx skills check            # 检查更新
npx skills update           # 更新所有技能
```

---

### usefull/skill-creator

**技能创建器**

用于创建、改进和基准测试其他技能的元技能。指导技能开发的完整生命周期。

**适用场景：**
- 从零创建新技能
- 改进现有技能
- 运行评估测试技能效果
- 优化技能描述以提高触发准确性

**流程：**
1. 明确意图 — 技能要实现什么？
2. 编写 SKILL.md 草稿
3. 创建测试提示（评估用例）
4. 运行「有技能」vs「无技能」对比
5. 用基准测试查看器评估结果
6. 根据反馈改进
7. 重复直至满意
8. 优化触发描述

---

### usefull/playwright-cli

**Playwright 浏览器自动化**

通过 CLI 接口自动化浏览器交互、测试网页、处理 Playwright 测试用例。

**适用场景：**
- 浏览器自动化任务
- 网页测试和爬取
- 截图/PDF 导出
- 会话和 Cookie 管理
- 网络请求拦截

**核心命令：**
```bash
playwright-cli open                    # 打开浏览器
playwright-cli goto <url>             # 导航到页面
playwright-cli click <element>        # 点击元素
playwright-cli snapshot                # 获取页面快照（含元素引用）
playwright-cli screenshot              # 截图
playwright-cli cookie-list             # 管理 Cookie
playwright-cli tab-new                # 新建标签页
playwright-cli tracing-start          # 开始录制追踪
```

---

### usefull/remotion-best-practices

**Remotion 最佳实践**

Remotion（React 中的视频创作）最佳实践。涵盖项目初始化、动画模式、字幕、FFmpeg 集成和音频可视化。

**适用场景：**
- 用 React 程序化创建视频
- 使用 Remotion Studio 预览/编辑视频
- 添加字幕/特效声、语音旁白
- 复杂时间轴动画

**核心规则：**
- Three.js 和 React Three Fiber 的 3D 内容
- 动画基础、序列编排、转场效果
- 素材处理（图片、视频、音频、字体）
- 字幕/唱词模式
- 音频可视化（频谱柱、波形）
- Tailwind CSS 集成
- 动态构图元数据
- DOM 节点和文字尺寸测量

---

## 技能格式

每个技能遵循以下结构：

```
skill-name/
├── SKILL.md                      # 必需：name、description、使用说明
├── scripts/                      # 可执行脚本（可选）
├── references/                  # 深度文档（可选）
├── agents/                       # 子代理指令（可选）
└── assets/                       # 静态资源（可选）
```

**SKILL.md 前置元数据：**
```yaml
---
name: skill-name
description: 何时触发以及功能描述
---
```

技能采用渐进式加载：
- 元数据始终加载（约 100 词）
- 正文在技能触发时加载（最好控制在 500 行以内）
- 捆绑资源按需加载

## 安装方式

兼容 Claude Code 技能系统的技能可通过以下方式安装：

```bash
npx skills add <owner/repo@skill>
```

开发阶段也可直接将技能放置在本仓库中，通过路径引用。

## 许可证

MIT 许可证 — 各技能目录中可能有单独的许可证说明。
