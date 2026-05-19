# Reveal.js 演示文稿模板

基于 [Reveal.js](https://revealjs.com/) 的本地离线演示模板，使用暖米色主题，内置多种常用布局组件。

## 快速开始

用任意支持本地文件的浏览器直接打开 `template.html` 即可预览。若需完整的代码高亮和 MathJax 渲染，请通过本地 HTTP 服务器访问：

```bash
# Python 3
python -m http.server 8080
# 然后访问 http://localhost:8080/template.html
```

## 文件结构

```
presentation_template/
├── template.html          # 主模板文件（从这里开始）
├── ta-transformer.html    # 完整示例演示（TA-Transformer 项目汇报）
├── dist/
│   ├── reveal.js          # Reveal.js 核心
│   ├── reveal.css
│   ├── reset.css
│   ├── theme/             # 内置主题（模板使用 white.css 作为基础）
│   └── plugin/            # 插件：highlight、math、markdown、notes 等
├── font/
│   ├── inter/             # 西文正文
│   ├── comic-neue/        # 西文展示体
│   ├── jetbrains-mono/    # 代码等宽字体
│   ├── noto-sans-sc/      # 中文正文
│   └── alibaba-puhuiti/   # 中文备用
└── lib/
    └── mathjax/           # MathJax 本地离线包
```

## 键盘快捷键

| 按键 | 功能 |
|------|------|
| `→` / `Space` | 下一张 |
| `←` | 上一张 |
| `F` | 全屏 |
| `O` | 扇形幻灯片地图（自定义） |
| `Esc` | 退出扇形地图 |
| `S` | 演讲者备注（需 notes 插件） |

## 配色变量

模板使用暖米色系，所有颜色可在 `<style>` 注释块中找到：

| 变量用途 | 颜色值 | 说明 |
|---------|--------|------|
| 主背景 | `#FAF8F4` | 暖米白 |
| 卡片底色 | `#F5EFE6` | 暖奶油 |
| 铜橙强调 | `#C8956C` / `#8B5E3C` | 主要强调色 |
| 赤陶辅色 | `#B85450` | 警示 / 重要 |
| 鼠尾草辅色 | `#4F8B68` | 正向 / 成功 |
| 边框 | `#E0D5C5` | 暖米边框 |
| 灰文字 | `#9A8878` | 次要说明文字 |

## 内置布局组件

### 左色条卡片

```html
<div style="background:#F5EFE6;border-left:4px solid #C8956C;border-radius:0 8px 8px 0;padding:10px 14px;">
  <div style="font-size:0.58em;font-weight:bold;color:#8B5E3C;">标题</div>
  <div style="font-size:0.46em;color:#5A4030;line-height:1.6;margin-top:4px;">内容文字</div>
</div>
```

边框颜色可替换为 `#B85450`（赤陶）或 `#4F8B68`（鼠尾草）。

---

### 管线流程图 `.pipeline`

```html
<div class="pipeline">
  <div class="pipe-step">
    <div class="ps-num">1</div>
    <div class="ps-title">步骤标题</div>
    <div class="ps-sub">步骤说明</div>
  </div>
  <div class="pipe-arrow">→</div>
  <!-- 重复以上结构 -->
</div>
```

---

### 公式步骤行 `.eq-row`

```html
<div class="eq-row">
  <span class="label">名称</span>
  <span>$公式占位 = f(x)$</span>
  <span class="c-dim">说明</span>
</div>
```

支持 MathJax 行内公式（`$...$`）和块级公式（`$$...$$`）。

---

### 终端风格代码框 `.code-theater`

```html
<div class="code-theater">
  <div class="theater-bar">
    <span class="dot d-r"></span>
    <span class="dot d-y"></span>
    <span class="dot d-g"></span>
    <span class="theater-fname">filename.py</span>
  </div>
  <pre><code class="language-python">
# 代码内容
  </code></pre>
</div>
```

---

### 代码 + 侧注布局 `.code-split`

```html
<div class="code-split">
  <div class="code-split-left">
    <!-- .code-theater 放这里 -->
  </div>
  <div class="code-split-right">
    <div class="ann-card">普通注释</div>
    <div class="ann-card r">警示注释</div>
    <div class="ann-card g">正向注释</div>
  </div>
</div>
```

---

### 注释气泡 `.ann`

```html
<span class="ann">默认</span>
<span class="ann r">警示</span>
<span class="ann g">正向</span>
```

---

### 架构框 `.arch-box`

```html
<div class="arch-box">模块名称</div>
<div class="arch-arrow">↓</div>
```

---

### 指标徽章 `.stat-badge`

```html
<span class="stat-badge">指标名: 数值</span>
```

## 新建演示文稿

1. 复制 `template.html`，重命名为你的项目名
2. 修改 `<title>` 标签
3. 替换封面的标题、副标题、作者和日期
4. 按需增删 `<section>` 块
5. 同步更新浮动导航的 `href`、`data-from`、`data-to` 页码

## 浮动导航配置

```html
<div class="floating-nav" id="floatingNav">
  <a href="#/0" data-from="0" data-to="0">封面</a>
  <span class="nav-sep">·</span>
  <a href="#/1" data-from="1" data-to="3">节名 <em>2–4</em></a>
  <!-- data-from/data-to 为该节覆盖的幻灯片索引（从 0 开始） -->
</div>
```

## 依赖说明

全部依赖均本地离线，无需网络：

- **Reveal.js** — 演示框架
- **MathJax 3** — 数学公式渲染
- **highlight.js** — 代码语法高亮（Monokai 主题）
- **字体** — Inter、Comic Neue、JetBrains Mono、Noto Sans SC（均为 woff2 本地文件）
