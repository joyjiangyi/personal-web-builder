---
name: personal-web-builder
description: 帮助用户从零搭建电影质感个人网站（作品集/求职/个人品牌）。触发场景：用户说"帮我做个人网站"、"做个作品集"、"搭个个人主页"、"build my portfolio/personal website"。流程：信息采集→蓝图确认→网页搭建→AI视频提示词→本地预览。交付本地可运行的项目文件夹。
---

# Personal Web Builder

帮用户从零搭建一个电影质感的个人网站。全程引导，逐步确认，最终交付本地可运行的项目文件夹。

**灵感来源：** jiojiojoy.com 的完整搭建过程。

---

## 整体流程

```
Phase 1 信息采集 → Phase 2 蓝图确认 → Phase 3 网页搭建 → Phase 4 AI视频 → Phase 5 本地收尾
```

**铁律：蓝图没有用户确认，不写一行代码。**

---

## Phase 1 — 信息采集

**逐一提问，不一次全抛。等用户回答后再问下一个。**

按顺序问：

1. 你的姓名 / 英文名 / 职业头衔是什么？
2. 这个网站的目的：求职中 / 展示作品 / 个人品牌？
3. 网站主要给谁看？（HR / 客户 / 合作方 / 粉丝 / 综合）
4. 风格偏好：有没有喜欢的参考网站？或者用关键词描述调性（极简 / 电影感 / 创意 / 科技感 / 温暖）？
5. 颜色倾向：深色系 / 浅色系 / 不确定？

---

## Phase 2 — 页面蓝图确认

收集完信息后，输出「网站蓝图」供用户确认，包含：

### 标准模块（所有人）
- **Hero** — 姓名 + 一句话宣言 + 背景视频
- **关于我** — 简短介绍（2-3 句）
- **经历** — 教育 / 工作亮点
- **联系方式** — Email / 社交媒体

### 根据职业身份智能追加推荐

| 职业类型 | 追加推荐模块 |
|---------|------------|
| 影视 / 创意人 | 作品展示（横向滚动海报 / 视频 reel）|
| 程序员 / 产品人 | 产品 / 开源项目展示 |
| 市场 / 运营 | 数据成果 / Campaign 案例展示 |
| 设计师 | 视觉作品集（大图展示）|
| 自媒体博主 | 内容展示 / 账号数据 |
| 其他职业 | 根据用户描述判断最合适的展示模块 |

### 蓝图格式

每个确认的页面输出：
- 页面名称 + 功能描述
- 文案草稿（英文为主，可切换中文）
- 交互说明（如有）

**用户回复确认后，才进入 Phase 3。**

---

## Phase 3 — 网页搭建

### 技术规范

- **单文件 HTML**：所有 CSS / JS 内嵌，无构建工具，直接打开可用
- **Scroll Scrubbing**：GSAP ScrollTrigger，滚动控制视频时间轴
- **Scroll Snap**：JS 实现（不用 CSS mandatory，避免跳过高内容 section）
- **字体**：Cormorant Garamond（衬线标题）+ Inter（正文）
- **默认配色**：深色系（`#0f0e0d` 背景 + `#c9a84c` 暖金强调色 + `#f0e8d8` 奶油白文字）
- **默认视频**：Grand Budapest Hotel 帷幕视频（内嵌占位，用户可替换）

### 搭建原则

**截图先行：改完必截图 → 截图等确认 → 确认再改下一处。**

不等用户说"截图给我"，每次修改后主动截图。

**限制修改范围：** 每次明确告知只改哪个 section，不动其他部分。CSS 用具体父选择器（如 `#hero .phone`，不用 `.phone`）。

### 已知技术坑（必须规避）

| 坑 | 原因 | 解法 |
|----|------|------|
| 视频 scrub 无法 seek | moov atom 在文件末尾 | `ffmpeg -movflags +faststart` 重新编码 |
| 本地滚动无反应 | `file://` 协议不兼容 Lenis | 必须用 `npx serve`，不能双击打开 |
| 视频跳到最后一帧 | `autoplay` 属性 | 去掉 `autoplay`，完全由 scrub 控制 |
| Scroll 初始文字不显示 | Lenis 初始不触发 scroll 事件 | 初始化后手动调用一次 `updateScene()` |
| CSS snap 跳过高内容页 | `scroll-snap-type: mandatory` | 改用 JS snap，滚动停止后吸附 |
| AI 误改其他模块 | CSS 类名共用 | 每个 section 用独立父选择器 |

---

## Phase 4 — AI 视频提示词包

根据用户风格偏好，提供三套方案，用户三选一：

### 方案 A — AI 生成视频

**通用提示词结构：**
```
[场景描述], [灯光风格], [摄影机运动], [色调], cinematic, 4K, slow motion, no text, no people
```

**推荐工具：** Runway Gen-3 / Kling / Pika Labs

**预设主题提示词：**

| 主题 | 适合风格 | 提示词 |
|------|---------|--------|
| 电影帷幕 | 戏剧感、创意 | `A grand theater with deep red velvet curtains slowly parting, warm golden spotlights, cinematic, dramatic, 4K, slow motion, no text` |
| 子弹时间片场 | 影视从业者 | `A film set frozen in time, camera slowly orbiting around a director's chair and vintage camera, warm golden hour light, cinematic, 4K` |
| 极简空间 | 极简、设计师 | `Minimal white studio space, soft diffused light, subtle dust particles floating, slow push-in camera, 4K, no people` |
| 城市夜景 | 科技感、商务 | `Aerial timelapse of city lights at night, slow smooth motion, dark background, neon reflections, cinematic, 4K` |
| 自然空镜 | 温暖、生活感 | `Ocean waves in slow motion, golden sunset, wide angle, cinematic, no people, 4K` |

### 方案 B — Pexels 免费素材（推荐保底）

搜索关键词：`cinematic slow motion` / `atmospheric dark` / `minimal abstract`

筛选标准：
- 时长 10-30 秒（循环用）
- 分辨率 1080p 以上
- 无人物特写（减少版权风险）
- 横屏（16:9）

### 方案 C — 保留默认视频

跳过此步，继续使用 Grand Budapest 帷幕视频。

### 视频处理（无论哪个方案都需要）

```bash
# Step 1：faststart 编码（必须，否则 scrub 失效）
ffmpeg -i input.mp4 -movflags +faststart -c copy output.mp4

# Step 2：替换项目里的视频文件
# 把 output.mp4 放入 assets/video/，更新 HTML 里的路径

# Step 3：本地预览
npx serve .
# 浏览器打开 http://localhost:3000
```

---

## Phase 5 — 本地预览收尾

### 本地验收清单

- [ ] `npx serve .` 启动后，浏览器可以访问 `http://localhost:3000`
- [ ] 滚动页面，视频随滚动进度播放（不卡帧，不跳帧）
- [ ] 所有 section 内容正常显示，无空白区域
- [ ] Chrome DevTools 手机模拟（375px 宽度）布局正常
- [ ] 联系方式点击跳转正确

### 收尾提示

收尾时说：
> "本地版本完成 🎬 你的网站已经可以在本地运行了。下一步是把它发布到网上（GitHub Pages + 自定义域名），那是 Part 2 的内容。"

---

## 设计原则

1. **先确认再动手** — 蓝图没有用户确认，不写一行代码
2. **文案先于设计** — 每页文案草稿确认后再排版
3. **截图先行** — 每次改完主动截图，不等用户要
4. **参考图优于文字描述** — 引导用户发图，比纯文字描述准确 10 倍
5. **限制修改范围** — 每次明说只改哪个 section，防止误改

---

## 不在范围内（本版本）

- 上线部署（GitHub Pages / 域名绑定）→ Part 2
- React / Next.js 等框架 → 纯 HTML 足够
- 表单后端处理 → 静态展示
- SEO 优化 → Part 3
