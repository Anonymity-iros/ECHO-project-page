# 双盲 Project Page 修改指南

## 页面结构（从上到下）

```
标题 → 摘要 → Teaser 图 → 视频展示（3行×3列）→ Footer
```

---

## 需要替换的内容

### 1. 页面标题（第 70 行）

```html
<h1 class="title is-1 publication-title">Your Paper Title Here</h1>
```

把 `Your Paper Title Here` 替换为你的论文标题。

---

### 2. 摘要文字（第 84~86 行）

```html
<p>
  Lorem ipsum dolor sit amet...
</p>
```

把 `Lorem ipsum...` 整段替换为你的论文摘要。

---

### 3. Teaser 图（第 99 行）

```html
<img src="./static/images/carousel1.jpg" alt="Teaser figure" />
```

- 把你的 teaser 图片放到 `static/images/` 目录下
- 将 `carousel1.jpg` 替换为你的文件名
- 同时修改第 101 行的图片描述文字

---

### 4. 视频文件（第 114~178 行）

每个视频的格式如下：

```html
<video controls muted loop autoplay playsinline width="100%" preload="metadata">
  <source src="./static/videos/carousel1.mp4" type="video/mp4">
</video>
<p class="has-text-centered">Video 1 description</p>
```

对每个视频你需要修改两处：
- `src="./static/videos/xxx.mp4"` → 替换为你的视频文件路径
- `Video X description` → 替换为对应的视频描述文字

当前共有 **9 个视频位**（3 行 × 3 列）：

| 位置 | 行号 | 当前文件 | 描述 |
|------|------|----------|------|
| Row1-1 | 118 | carousel1.mp4 | Video 1 description |
| Row1-2 | 124 | carousel2.mp4 | Video 2 description |
| Row1-3 | 130 | carousel3.mp4 | Video 3 description |
| Row2-1 | 140 | carousel1.mp4 | Video 4 description |
| Row2-2 | 146 | carousel2.mp4 | Video 5 description |
| Row2-3 | 152 | carousel3.mp4 | Video 6 description |
| Row3-1 | 162 | carousel1.mp4 | Video 7 description |
| Row3-2 | 168 | carousel2.mp4 | Video 8 description |
| Row3-3 | 174 | carousel3.mp4 | Video 9 description |

---

## 增减视频数量

### 增加一行视频

在 `<!-- Row 3 -->` 的 `</div>` 后面复制一整个 Row 块：

```html
<!-- Row 4 -->
<div class="columns is-centered is-multiline" style="margin-bottom: 1.5rem;">
  <div class="column is-one-third">
    <video controls muted loop autoplay playsinline width="100%" preload="metadata">
      <source src="./static/videos/your_video.mp4" type="video/mp4">
    </video>
    <p class="has-text-centered">描述</p>
  </div>
  <!-- 再复制 column 块可增加更多列 -->
</div>
```

### 每行只放 2 个视频

把 `is-one-third` 改为 `is-half`。

### 每行只放 1 个视频

把 `is-one-third` 改为 `is-full` 或 `is-two-thirds`。

### 删除视频

直接删掉对应的 `<div class="column is-one-third">...</div>` 块即可。
如果删掉整行，把整个 `<div class="columns ...">...</div>` 块删掉。

---

## 添加文件的步骤

1. 将你的**图片**放到 `static/images/` 目录
2. 将你的**视频**放到 `static/videos/` 目录
3. 在 `index.html` 中修改对应的 `src` 路径

路径统一用 `./static/...` 的格式（带 `./` 前缀），确保 GitHub Pages 能正确加载。

---

## 部署到 GitHub Pages

1. 创建一个 GitHub 仓库
2. 将所有文件 push 上去
3. 在仓库 Settings → Pages → Source 选择 `main` 分支
4. 等待部署完成后访问 `https://你的用户名.github.io/仓库名/`

确保仓库根目录有 `.nojekyll` 文件（已存在），否则 GitHub Pages 会用 Jekyll 处理导致问题。
