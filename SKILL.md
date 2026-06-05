---
name: personal-web-builder
description: 帮助用户从零搭建网站，包括个人网站、品牌官网、产品页等。触发场景：用户说"帮我做网站"、"做个官网"、"搭个落地页"、"做作品集"、"build my website/portfolio/landing page"。流程：深度需求沟通→内容规划→蓝图确认→网页搭建→AI视频提示词→本地预览。交付本地可运行的项目文件夹。
---

# Web Builder

帮用户从零搭建网站。适用范围：个人网站、作品集、品牌官网、产品落地页、活动页等。全程引导，深度定制，最终交付本地可运行的项目文件夹。

---

## 整体流程

```
Phase 1 深度需求沟通
→ Phase 2 内容清单确认
→ Phase 3 蓝图 + 风格确认
→ Phase 4 网页搭建（视频 scrub 结构已内置，CSS 动画为视频到位前的占位）
→ Phase 5 本地验收 + 一镜到底 AI 提示词（验收 OK 后输出，用户自行生成视频替换）
```

**铁律：蓝图没有用户确认，不写一行代码。**

**核心架构原则：视频滚动驱动（scroll scrub）是这个网站的骨架，不是可选装饰。每个网站都按「有视频」的结构生成。没有视频前，CSS 动态背景是占位；用户把 `hero.mp4` 放到同一文件夹，刷新即生效，零改代码。**

---

## Phase 1 — 深度需求沟通

**目标：搞清楚用户要做什么网站、给谁看、想放什么内容。**

不要预设模板，不要套职业类型。通过对话真正理解用户的需求，再据此设计结构和风格。

### 开场

> 你好！我来帮你从零搭建一个网站 🎬
>
> 先问几个问题，帮我了解你想做什么——
>
> **这个网站是给谁看的？用一两句话描述一下你的访客是谁、他们看完网站你希望他们做什么？**
>
>（比如："给招聘方看，让他们了解我的经历然后约面试" / "给潜在客户看，让他们了解我的服务然后联系我" / "给粉丝看，展示我的作品"）

### 追问逻辑

根据用户的回答，继续追问以下内容（每次一个问题，不一次全抛）：

**① 网站类型确认**
根据用户描述判断是哪类网站，如有歧义则直接问：
> 这个网站更偏向哪个方向？
> A · 个人网站 / 作品集（展示个人身份和经历）
> B · 品牌 / 公司官网（展示品牌和服务）
> C · 产品落地页（推广某个具体产品或功能）
> D · 活动 / 项目专题页（某次活动、发布会、特定项目）
> E · 其他（请描述）

**② 核心内容追问**
这是最重要的一步。逐一问清楚用户想放什么内容：

> **你希望网站里放哪些内容？** 比如：
> - 自我介绍 / 公司介绍
> - 作品 / 项目展示
> - 服务 / 产品列表
> - 数据成果 / 案例
> - 视频（宣传片 / 作品 reel / 产品演示）
> - 图片画廊
> - 博客 / 文章
> - 联系方式 / 预约表单
>
> 不用一一对应，随意说你想放什么，我来帮你整理。

**③ 内容形式追问**
针对用户提到的每一块内容，追问具体形式：

| 用户说 | 追问 |
|--------|------|
| 有视频 | 是嵌入 YouTube/Bilibili 链接，还是本地 mp4 文件？如果是 .mov 文件需要先转换（见下方命令） |
| 有作品 | 作品是图片、视频、还是链接跳转？大概几个？ |
| 有案例 | 案例要展示哪些信息？（图片 / 数据 / 文字描述 / 链接）|
| 有服务列表 | 有没有对应的图片或图标？ |
| 有联系方式 | 只显示邮箱/社媒，还是需要填写表单（静态展示即可）？|

> ⚠️ 如果用户提到 `.mov` 视频，提醒先转码：
> ```bash
> ffmpeg -i input.mov -c:v libx264 -crf 22 -movflags +faststart -pix_fmt yuv420p output.mp4
> ```

**④ 已有素材确认**
> 你现在手上有哪些现成素材？
> A · 有 Logo / 品牌色 / VI 规范
> B · 有图片（个人照 / 产品图 / 场景图）
> C · 有文案（自我介绍 / 产品描述）
> D · 基本没有，需要 AI 生成占位内容
>
> 多选，回复字母即可。

**⑤ 参考风格**
> 有没有你喜欢的网站截图或链接？（没有也完全没关系）
>
> 如果没有，用几个关键词描述你想要的感觉：
> 🎬 电影感 · ◻️ 极简 · 🎨 创意 · 💻 科技感 · 🌿 温暖 · 🖋 编辑杂志感 · 💎 奢华高端 · 🎮 游戏感


---

## Phase 2 — 内容清单确认

沟通完成后，整理一份「内容清单」给用户确认，格式如下：

```
网站类型：[个人作品集 / 品牌官网 / 产品落地页...]
目标访客：[描述]
访客期望行为：[描述]

内容模块：
1. [模块名] — [内容描述] — [形式：文字/图片/视频链接/嵌入...]
2. [模块名] — [内容描述] — [形式...]
...

现有素材：[列举]
参考风格：[关键词或参考链接]
```

**用户确认内容清单后，才进入 Phase 3。**

如果内容清单中有模糊项，先按合理假设填写，标注 [待定]，继续推进不卡住。

---

## Phase 3 — 蓝图 + 风格确认

根据内容清单，生成「网站蓝图」：

### 蓝图格式

```
页面结构（共 X 页）：
1. [页面名] — [功能] — [交互方式（如有）]
   文案草稿：[...]
2. ...

视觉风格方向：
- 配色：[主色 / 背景色 / 强调色]
- 字体：[标题字体 + 正文字体]
- 布局风格：[大字排版 / 卡片式 / 全屏分页 / 长页滚动...]
- 背景处理：[纯色 / 视频 / 图片 / 渐变]
- 特色交互：[视频滚动 / 动画 / 悬停效果...]
```

### Hero 文案：张力提取法

**个人网站的 Hero 文案不要写成简历句。** 从用户的自我介绍里找「对仗张力」：

- 白天 vs 黑夜：`By day, I run campaigns. / By night, I build worlds.`
- 理性 vs 感性：`Data is my language. / Story is my weapon.`
- 东方 vs 西方、技术 vs 艺术、本地 vs 全球……

用两行 punchy 对仗句强化这个张力，比「我是一名XX从业者」有力 10 倍。

### 字体 × 风格匹配

| 调性 | 标题字体 | 正文字体 |
|------|---------|---------|
| 电影 / 戏剧感 | Cormorant Garamond / Manrope | Inter |
| 极简现代 | Unbounded / Space Grotesk | Inter |
| 科技感 | JetBrains Mono / Syne | Inter |
| 温暖亲切 | Playfair Display / Lora | Source Sans Pro |
| 奢华高端 | Bodoni Moda | Garamond |
| 创意怪趣 | Syne / Cabinet Grotesk | DM Sans |
| 复古千禧 | Audiowide | Space Mono |
| 海洋 / 奇幻 | Instrument Serif | Inter |

### 风格差异化原则

**每个用户的网站都应该和其他人的不一样。** 风格由内容和品牌决定，不是套模板。

| 网站类型 | 推荐风格方向 |
|---------|-------------|
| 影视 / 创意人 | 沉浸式、暗色、有戏剧张力、大图/视频主导 |
| 科技产品落地页 | 深色科技感、大字标题、清晰 CTA、无装饰 |
| 设计师作品集 | 极简留白、作品主导、字体考究、不花哨 |
| 品牌官网 | 明亮干净、有序网格、品牌色主导、信任感 |
| 个人品牌 / 博主 | 温暖色系、有人像、亲近感、轻松不正式 |
| 活动专题页 | 大背景氛围感、强对比色、倒计时、时效感 |

**不要默认给所有人用暗色电影感。**

### 反模式禁令（所有风格通用）

以下是会让网站显得廉价或失去个性的设计，**必须避免**：

- ❌ 圆角卡片 + drop-shadow 组合（SaaS landing 专属，让个人网站显得没有品位）
- ❌ 居中堆叠的「标题 + 副标题 + 按钮」三件套（太模板化）
- ❌ 卡通插图 / emoji 装饰（除非品牌调性明确需要）
- ❌ 「友好」或「轻松」的语气（如"Hi there! 👋"——除非是个人博主）
- ❌ 所有 section 等间距、等字号、无节奏变化

**用户确认蓝图后，才进入 Phase 4。**

---

## Phase 4 — 网页搭建

### 技术栈（固定）

- **单文件 `index.html`**：UTF-8，所有 CSS / JS 内嵌，无构建工具，双击可预览（但需 `npx serve` 才能跑视频）
- **Tailwind v3 CDN**：`<script src="https://cdn.tailwindcss.com"></script>`
- **GSAP 3.14 + ScrollTrigger CDN**：
  ```html
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.14.2/gsap.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.14.2/ScrollTrigger.min.js"></script>
  ```
- **Google Fonts**：按风格选择，`<link rel="preconnect">` 优化加载
- **图标**：内联 SVG，不用 lucide 或其他图标库

### 层级规范（必须遵守）

```
z-0   固定视频背景
z-10  主内容（pointer-events-none；互动元素单独加 pointer-events: auto）
z-20  header（如有）
z-50  loading 屏（首屏覆盖，视频加载完后淡出）
```

### 视频结构（必须内置，照写）

**每个网站都内置视频背景结构。** 没有视频文件时，`<video>` 元素 `src` 为空，JS 的 `!video.duration` guard 使 scrub 静默，CSS 动态背景作为视觉占位。用户把 `hero.mp4` 放进来，刷新即生效。

> 视频文件命名统一为 `hero.mp4`，和 `index.html` 放在同一目录。用户如有 `.mov` 文件，提醒先转码：
> ```bash
> ffmpeg -i input.mov -c:v libx264 -crf 22 -movflags +faststart -pix_fmt yuv420p hero.mp4
> ```

### CSS 动态背景（视频到位前的占位）

**视频放好之前不裸奔纯色。** 根据风格选用对应动态背景，放在 `z-0` 与 `#video-bg` 同层（视频加载后，视频盖在上面，动态背景自然隐入背景）：

| 风格 | CSS 方案 | 效果描述 |
|------|---------|---------|
| 电影感 / Editorial | 颗粒噪点 + 暗色渐变 | 胶片质感底纹，静止但有呼吸感 |
| 海洋 / 奇幻 | `.caustics` 水波光动画 | 缓慢流动的水底光斑 |
| 科技感 | CSS 网格线 + 扫光动画 | 深色网格，光线缓慢扫过 |
| 温暖 / 自然 | 柔光 blob 渐变动画 | 粉/橙/黄色光晕缓慢漂移 |
| 极简 | 纯色 + 细微纸质纹理 | 无动画，但有触感 |
| 创意 / IP | 彩色 blob 漂移动画 | 品牌色光晕随机漂浮 |

**彩色 blob 漂移（适合创意/IP/温暖风格）：**
```css
.bg-blobs {
  position: fixed; inset: 0; z-index: 0; pointer-events: none; overflow: hidden;
}
.blob-item {
  position: absolute; border-radius: 50%; filter: blur(80px); opacity: 0.35;
  animation: blobdrift var(--duration, 12s) ease-in-out infinite alternate;
}
@keyframes blobdrift {
  0%   { transform: translate(0, 0) scale(1); }
  50%  { transform: translate(var(--tx, 40px), var(--ty, -30px)) scale(1.1); }
  100% { transform: translate(var(--tx2, -20px), var(--ty2, 50px)) scale(0.95); }
}
```
用法（颜色换成品牌色）：
```html
<div class="bg-blobs">
  <div class="blob-item" style="width:500px;height:500px;top:-100px;left:-100px;background:#FFE8EE;--duration:14s;--tx:60px;--ty:-40px;--tx2:-30px;--ty2:80px;"></div>
  <div class="blob-item" style="width:400px;height:400px;bottom:-80px;right:-80px;background:#FFB3C6;--duration:10s;--tx:-50px;--ty:30px;--tx2:40px;--ty2:-60px;"></div>
</div>
```

**科技感网格扫光：**
```css
.tech-grid {
  position: fixed; inset: 0; z-index: 0; pointer-events: none;
  background-image: linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
                    linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 40px 40px;
}
.tech-scan {
  position: fixed; top: 0; left: -100%; width: 60%; height: 100%;
  background: linear-gradient(90deg, transparent, rgba(99,179,255,0.04), transparent);
  animation: scan 8s linear infinite;
  z-index: 0; pointer-events: none;
}
@keyframes scan { to { left: 150%; } }
```

**颗粒噪点（电影感必备）：**
```css
.grain {
  position: fixed; inset: -50%; z-index: 0; pointer-events: none;
  width: 200%; height: 200%;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.4'/%3E%3C/svg%3E");
  opacity: 0.04;
  animation: grain 0.5s steps(2) infinite;
}
@keyframes grain {
  0%,100% { transform: translate(0,0); }
  25%      { transform: translate(-1%,1%); }
  50%      { transform: translate(1%,-1%); }
  75%      { transform: translate(-1%,-1%); }
}
```

### Signature CSS — 按风格启用

不要所有人都用同一套 CSS。根据用户选的风格，启用对应的 Signature CSS：

**电影感 / Editorial（暗色 + 玻璃感）**
```css
/* 玻璃卡片 */
.glass {
  backdrop-filter: blur(20px);
  background: rgba(255,255,255,0.05);
  border: 1px solid rgba(255,255,255,0.1);
}
/* 辅助色可选：冷金属 / 暖黄 / 莫兰迪绿 / 钴蓝 */
```

**海洋 / 奇幻（深海蓝 + 水波光）**
```css
/* 水底光波动画 */
.caustics {
  position: fixed; inset: 0; pointer-events: none; z-index: 1;
  background:
    radial-gradient(ellipse 60% 50% at 30% 20%, rgba(150,220,255,0.18), transparent 50%),
    radial-gradient(ellipse 50% 60% at 80% 60%, rgba(200,240,255,0.10), transparent 60%);
  animation: caustic 15s ease-in-out infinite alternate;
}
@keyframes caustic {
  0%   { transform: translate(0,0) scale(1); }
  50%  { transform: translate(-20px,15px) scale(1.05); }
  100% { transform: translate(15px,-10px) scale(0.98); }
}
/* 底色：linear-gradient(180deg, #0A1929 0%, #0F2F47 50%, #1A4565 100%) */
```

**复古千禧 Y2K（chrome 金属 + 镭射彩虹）**
```css
/* Chrome 金属字 */
.chrome {
  background: linear-gradient(180deg, #fff 0%, #C0E0FF 30%, #80B0FF 50%, #fff 60%, #C0C0E0 100%);
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
  filter: drop-shadow(0 0 12px rgba(180,200,255,0.4));
}
/* 镭射彩虹副标 */
.laser {
  background: linear-gradient(90deg, #FF80E0, #80E0FF, #80FFE0, #FFE080);
  -webkit-background-clip: text; background-clip: text;
  -webkit-text-fill-color: transparent;
}
/* 果冻按钮 */
.jelly {
  background: linear-gradient(180deg, rgba(255,255,255,0.25), rgba(180,200,255,0.15));
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255,255,255,0.3);
  box-shadow: inset 0 1px 0 rgba(255,255,255,0.5), 0 4px 30px rgba(100,200,255,0.2);
}
/* 底色：linear-gradient(135deg, #1A1F4E 0%, #2C1A4E 50%, #4E1A4E 100%) */
```

### 关键代码块 1：视频背景 + 加载 + Scroll Scrub

**照写，不要自己实现**（`video.seeking` guard 自己写极易出 bug）

**HTML：**
```html
<div id="video-bg" class="fixed inset-0 z-0 bg-black">
  <video id="hero-video" muted playsinline preload="auto">
    <source src="assets/video/bg.mp4" type="video/mp4" />
  </video>
</div>
<!-- loading 屏 -->
<div id="loading" class="fixed inset-0 z-50 bg-black flex items-center justify-center">
  <div class="text-white/40 text-sm tracking-widest uppercase">Loading</div>
</div>
```

**CSS：**
```css
#video-bg video {
  position: absolute; top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  min-width: 100%; min-height: 100%;
  object-fit: cover;
  /* 禁止给 video 加 mix-blend-mode 或 opacity < 1，否则视频会被淹没 */
  /* 需要染色请在视频上层加独立 <div> overlay */
}
/* loading 屏淡出（配合 JS 里 body.dataset.loaded = 'true'） */
body[data-loaded="true"] #loading {
  opacity: 0;
  visibility: hidden;
  pointer-events: none;
  transition: opacity 0.6s ease;
}
```

**JS（放在 `</body>` 前）：**
```js
const video = document.getElementById('hero-video');
let isLoaded = false;

// 多事件 + 3秒兜底（任一先触发就解锁）
const handleLoaded = () => {
  if (isLoaded) return;
  isLoaded = true;
  document.body.dataset.loaded = 'true';
};
if (video) {
  video.addEventListener('loadeddata', handleLoaded);
  video.addEventListener('canplay', handleLoaded);
  video.addEventListener('canplaythrough', handleLoaded);
  video.load();
}
setTimeout(handleLoaded, 3000);

// Scroll Scrub（含 video.seeking guard 防帧撕裂）
window.addEventListener('scroll', () => {
  if (!isLoaded || !video || !video.duration || video.seeking) return;
  const maxScroll = Math.max(1, document.documentElement.scrollHeight - window.innerHeight);
  const fraction = Math.max(0, Math.min(1, window.scrollY / maxScroll));
  video.currentTime = fraction * video.duration;
}, { passive: true });
```

### 关键代码块 2：GSAP 大字逐词浮现

**照写**（GSAP ScrollTrigger 时序 + scrub 同步容易写错）

**用法：**
```html
<h2 data-scroll-reveal data-text-class="font-medium tracking-tight text-white">
  你想逐词浮现的长句
</h2>
```

**CSS：**
```css
.scroll-reveal { margin: 0; }
.scroll-reveal-text { display: flex; flex-wrap: wrap; margin: 0; }
.word { display: inline-block; white-space: pre; }
```

**JS：**
```js
if (window.gsap && window.ScrollTrigger) {
  gsap.registerPlugin(ScrollTrigger);
  document.querySelectorAll('[data-scroll-reveal]').forEach((el) => {
    const text = el.textContent || '';
    el.textContent = '';
    el.classList.add('scroll-reveal');
    const p = document.createElement('p');
    p.className = 'scroll-reveal-text ' + (el.dataset.textClass || '');
    text.split(/(\s+)/).forEach((part) => {
      if (!part) return;
      const span = document.createElement('span');
      span.className = 'word';
      span.textContent = part;
      p.appendChild(span);
    });
    el.appendChild(p);
    // 容器旋转 3deg → 0
    gsap.fromTo(el, { rotate: 3, transformOrigin: '0% 50%' },
      { rotate: 0, ease: 'none', scrollTrigger: { trigger: el, start: 'top bottom', end: 'bottom bottom', scrub: true }});
    // 词不透明度 0.1 → 1
    gsap.fromTo(p.querySelectorAll('.word'), { opacity: 0.1 },
      { opacity: 1, stagger: 0.05, ease: 'none', scrollTrigger: { trigger: el, start: 'top bottom-=20%', end: 'bottom bottom', scrub: true }});
    // 词去模糊 4px → 0
    gsap.fromTo(p.querySelectorAll('.word'), { filter: 'blur(4px)' },
      { filter: 'blur(0px)', stagger: 0.05, ease: 'none', scrollTrigger: { trigger: el, start: 'top bottom-=20%', end: 'bottom bottom', scrub: true }});
  });
}
```

### 关键代码块 3：IntersectionObserver 元素淡入上浮

**用法：** `<div data-reveal style="--reveal-delay: 0.2">...</div>`

```css
[data-reveal] {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.8s cubic-bezier(0.16,1,0.3,1), transform 0.8s cubic-bezier(0.16,1,0.3,1);
  transition-delay: calc(var(--reveal-delay, 0) * 1s);
}
[data-reveal="visible"] { opacity: 1; transform: translateY(0); }
```

```js
const revealObserver = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      entry.target.dataset.reveal = 'visible';
      revealObserver.unobserve(entry.target);
    }
  });
}, { rootMargin: '-50px' });
document.querySelectorAll('[data-reveal]').forEach((el) => revealObserver.observe(el));
```

### 搭建原则

**截图先行：改完必截图 → 截图等确认 → 确认再改下一处。**

不等用户说"截图给我"，每次修改后主动截图。

**限制修改范围：** 每次明确告知只改哪个 section，不动其他部分。CSS 用具体父选择器（如 `#hero .phone`，不用 `.phone`）。

### 已知技术坑

| 坑 | 原因 | 解法 |
|----|------|------|
| 视频 scrub 无法 seek | moov atom 在文件末尾 | `ffmpeg -movflags +faststart` 重新编码 |
| 本地滚动无反应 | `file://` 协议不兼容 Lenis | 必须用 `npx serve`，不能双击打开 |
| 视频跳到最后一帧 | `autoplay` 属性 | 去掉 `autoplay`，完全由 scrub 控制 |
| Scroll 初始文字不显示 | Lenis 初始不触发 scroll 事件 | 初始化后手动调用一次 `updateScene()` |
| CSS snap 跳过高内容页 | `scroll-snap-type: mandatory` | 改用 JS snap，滚动停止后吸附 |
| AI 误改其他模块 | CSS 类名共用 | 每个 section 用独立父选择器 |
| 帧撕裂 / 视频跳帧 | 未加 `video.seeking` guard | 使用关键代码块 1 的 scrub 代码 |

---

## Phase 5 — 本地验收 + 一镜到底提示词

用户先把网页跑起来，确认一切 OK。

```bash
npx serve .
# 打开 http://localhost:3000
```

### 验收清单

- [ ] 页面正常加载，CSS 动态背景有动画效果
- [ ] 所有 section 内容显示正确，无空白
- [ ] Chrome DevTools 手机模拟（375px）布局正常
- [ ] 所有链接 / 按钮点击跳转正确

### 验收通过后：Step 1 — 确认首帧视觉风格

验收 OK 后，**不直接给提示词**，先引导用户确认视频的视觉方向：

> "网站跑起来了 🎬
>
> 在生成视频提示词之前，先帮你想清楚视频的第一帧——它决定了整段视频的气质。
>
> 根据你的网站风格，我给你 2-3 个方向，你选一个，或者告诉我你自己的想法："

然后根据用户网站的风格，给出 **2-3 个具体的首帧方向**，每个方向描述：
- 画面里有什么（场景、光线、氛围）
- 色调和质感
- 镜头位置（从哪里往哪里看）

**例：** 如果用户是影视创作者，可以给：
> A · 空置摄影棚，单束戏剧顶光从高处打下，暖金色光柱穿透烟雾，镜头位于观众席视角向舞台仰望
> B · 胶片洗印室，暗红安全灯，湿润的暗房气息，镜头从底片悬挂处缓慢推进
> C · 你有别的想法？（随意描述，或发一张参考图）

**用户确认首帧方向后**，再进入 Step 2。

---

### 验收通过后：Step 2 — 生成一镜到底提示词

用户确认了首帧视觉方向后，结合用户的选择 + 网站整体风格，输出完整提示词（见下方生成规则）。

---

### 一镜到底 AI 视频提示词生成规则

提示词由你根据用户的风格和内容**自由创作**，不套模板。以下是必须遵守的核心原则：

---

**原则一：时间戳分段**

不要用一段话描述整个视频。把 8 秒切成 2-3 个阶段，每段给 AI 明确的指令。AI 有了时间节奏，才不会自己加剪辑。

段落数量和内容完全由你决定——可以是场景变化、运动节奏变化、时间状态变化（如子弹时间），或者什么都不变只是节奏上从动到静。段落边界要自然衔接，不能有跳切感。

---

**原则二：运镜连续性**

必须在提示词里明确说：**一镜到底，不要切镜，不要转场，摄像机轨迹连续平滑**。不说清楚，AI 会自行加剪辑。

运镜方式根据用户网站风格自由选择——推进、后退、弧形环绕、升降、穿越、停留都可以。关键是整段视频的运镜逻辑要有叙事感，和用户的品牌气质匹配。

---

**原则三：留白和克制**

视频是背景，不是主角。场景里的元素要有足够留白，动作要克制，不要密集、不要杂乱。用户的文字内容要能压在上面。

---

**原则四：严格禁止清单（每次都要写）**

结尾必须加一段禁止项，根据用户风格排除最可能出现的垃圾元素，比如：
- 通用禁止：任何切镜、转场、闪白、黑屏、场景切换、人物、清晰文字、水印
- 按风格加：科技风用户 → 禁止赛博朋克/电路板/AI界面；个人品牌 → 禁止PPT感/商业卡片；自然风 → 禁止过曝/滤镜感

---

**提示词语言：中文**（Kling 中文效果更稳；Runway 用英文版，备注翻译即可）

---

**输出格式：**

```
🎬 一镜到底视频提示词

[完整提示词，含时间戳分段 + 运镜说明 + 视觉要求 + 严格禁止]

---
推荐工具：Kling（国内最稳）/ Runway Gen-3（英文）
生成参数：8 秒，1920×1080，横屏
转码（如果是 .mov）：ffmpeg -i input.mov -c:v libx264 -crf 22 -movflags +faststart -pix_fmt yuv420p hero.mp4
放入方式：命名 hero.mp4，和 index.html 同目录，刷新即生效

没有生成条件？Pexels 备选：搜索 "[场景关键词] cinematic slow motion"，筛选 10s+、1080p、横屏
```

---

## 设计原则

1. **先聊需求再做设计** — 内容决定结构，结构决定风格，不反过来
2. **每个网站都应该不一样** — 风格从用户的内容和品牌中生长出来，不套模板
3. **张力驱动文案** — Hero 文案找对仗张力，不写简历句
4. **内容形式要问清楚** — 作品是图片还是跳转？联系方式是邮箱还是表单？
5. **视频骨架始终内置** — 照写关键代码块 1，不自己实现 scrub / loading
6. **GSAP 动效照写** — ScrollTrigger 时序容易写错，不要自己实现
7. **截图先行** — 每次改完主动截图，不等用户要
8. **限制修改范围** — 每次明说只改哪个 section，CSS 用具体父选择器
9. **验收后必出提示词** — 验收 OK 就立刻给一镜到底提示词，不需要用户问

---

## 不在范围内（本版本）

- 上线部署（GitHub Pages / 域名绑定）→ Part 2
- React / Next.js 等框架 → 纯 HTML 足够
- 表单后端处理 → 静态展示
- SEO 优化 → Part 3
