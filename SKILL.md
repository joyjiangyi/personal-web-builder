---
name: personal-web-builder
description: 帮助用户从零搭建网站，包括个人网站、品牌官网、产品页等。触发场景：用户说"帮我做网站"、"做个官网"、"搭个落地页"、"做作品集"、"build my website/portfolio/landing page"。流程：深度需求沟通→内容规划→蓝图确认→网页搭建→AI视频提示词→本地预览。交付本地可运行的项目文件夹。
---

# Web Builder

帮用户从零搭建网站。适用范围：个人网站、作品集、品牌官网、产品落地页、活动页等。全程引导，深度定制，最终交付本地可运行的项目文件夹。

---

## 整体流程

```
Phase 1 深度需求沟通 → Phase 2 内容清单确认 → Phase 3 蓝图+风格确认 → Phase 4 网页搭建 → Phase 5 AI视频 → Phase 6 本地收尾
```

**铁律：蓝图没有用户确认，不写一行代码。**

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

**⑥ 视频背景**
> **你希望网站有一个会随滚动动起来的视频背景吗？**（首屏背景会随鼠标滚动播放，有很强的沉浸感）
> A · 要——我来提供视频，或者用 AI 生成
> B · 不要——纯色 / 渐变背景就好
> C · 不确定，你来推荐

**处理规则：**
- 用户选 A：记录下来，Phase 5 给出 AI 视频提示词 + 替换流程
- 用户选 B：跳过 Phase 5，直接用纯色或渐变背景
- 用户选 C：根据网站类型判断——氛围感强的（电影感 / 活动页 / 创意人）推荐加，内容密度高的（品牌官网 / 产品落地页）推荐不加

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

## Phase 5 — AI 视频提示词包

**只在用户需要视频背景时进入此阶段。** 不需要视频则直接跳 Phase 6。

根据用户风格偏好，提供三套方案：

### 方案 A — AI 生成视频

**推荐工具：** Runway Gen-3 / Kling / Pika Labs

**通用结构：**
```
[场景描述], [灯光风格], [摄影机运动], [色调], cinematic, 4K, slow motion, no text, no people
```

| 风格 | 提示词 |
|------|--------|
| 电影 / 戏剧感 | `Empty film set with dramatic spotlight, camera slowly pushing in, dark atmospheric, cinematic, 4K` |
| 科技感 | `Abstract glowing data streams flowing in dark space, blue and purple light, slow motion, 4K` |
| 极简 | `Minimal white studio, soft light shifting slowly, subtle shadows, clean, 4K, no people` |
| 海洋 / 奇幻 | `Underwater light caustics, deep ocean blue, slow weightless drift, cinematic, 4K` |
| 温暖 / 自然 | `Golden hour sunlight filtering through leaves, gentle breeze, warm tones, slow motion, 4K` |
| 城市 / 商务 | `Modern city skyline at dusk, slow aerial push-in, warm ambient light, cinematic, 4K` |
| 复古千禧 | `Retro CRT screen glow, vintage electronics, soft light, Y2K aesthetic, slow motion, 4K` |

### 方案 B — Pexels 免费素材（推荐保底）

搜索关键词：`cinematic slow motion` / `atmospheric dark` / `minimal abstract`

筛选标准：时长 10-30 秒、1080p 以上、无人物特写、横屏 16:9

### 方案 C — 跳过视频

暂时跳过，保留纯色或渐变背景。

### 视频处理命令（有视频必须执行）

```bash
# .mov 转 .mp4
ffmpeg -i input.mov -c:v libx264 -crf 22 -movflags +faststart -pix_fmt yuv420p output.mp4

# 已有 .mp4 直接加 faststart（否则 scrub 失效）
ffmpeg -i input.mp4 -movflags +faststart -c copy output.mp4
```

---

## Phase 6 — 本地预览收尾

### 本地验收清单

- [ ] `npx serve .` 启动后，浏览器可以访问 `http://localhost:3000`
- [ ] loading 屏正常淡出，不卡死
- [ ] 有视频：滚动时视频随进度播放，不卡帧，不跳帧
- [ ] 所有 section 内容正常显示，无空白区域
- [ ] Chrome DevTools 手机模拟（375px 宽度）布局正常
- [ ] 所有链接 / 按钮点击跳转正确

### 收尾提示

> "本地版本完成 🎬 你的网站已经可以在本地运行了。下一步是把它发布到网上（GitHub Pages + 自定义域名），那是 Part 2 的内容。"

---

## 设计原则

1. **先聊需求再做设计** — 内容决定结构，结构决定风格，不反过来
2. **每个网站都应该不一样** — 风格从用户的内容和品牌中生长出来，不套模板
3. **张力驱动文案** — Hero 文案找对仗张力，不写简历句
4. **内容形式要问清楚** — 视频是链接还是文件？作品是图片还是跳转？
5. **照写关键代码块** — 视频加载/scrub/GSAP reveal 不要自己实现
6. **截图先行** — 每次改完主动截图，不等用户要
7. **限制修改范围** — 每次明说只改哪个 section，防止误改

---

## 不在范围内（本版本）

- 上线部署（GitHub Pages / 域名绑定）→ Part 2
- React / Next.js 等框架 → 纯 HTML 足够
- 表单后端处理 → 静态展示
- SEO 优化 → Part 3
