# 算盘 · Abacus

珠算练习与小工具，纯前端、可离线安装。

Abacus practice and tools. Pure front end, installable and offline-ready.

[中文](#中文) · [English](#english)

线上地址 / Live: `https://<你的用户名>.github.io/abacus/`

---

## 中文

### 是什么

一个只在浏览器里跑的小工具集，围绕算盘（上一下四）和珠心算练习。没有后端、没有外部依赖，每个工具都是单文件 HTML，断网照样用。

### 包含

| 工具 | 路径 | 说明 |
|---|---|---|
| 珠心算 · 听算 | [`zhuxinsuan/`](./zhuxinsuan/) | 听数字，在算盘上累加。4–8 列、3–15 个加数，四档速度；可遮盘盲算，可自己拨珠作答；带「打百子」演示、加法/乘法口诀、练习日历与计时 |

首页 `index.html` 是入口，中英文可切换（右上角「中 / EN」）。

### 手机上安装（PWA）

必须用 `https://` 地址打开，直接用文件双击打开（`file://`）装不了。

- **iPhone / iPad**：Safari 打开 → 分享按钮 → 「添加到主屏幕」
- **Android**：Chrome 打开 → 右上角菜单 → 「安装应用」或「添加到主屏幕」

装好后从主屏幕图标进入，是独立窗口，没有地址栏；断网也能用。

### 目录结构

```
abacus/
├── index.html            入口页（中英双语）
├── manifest.json         PWA 清单
├── sw.js                 离线缓存
├── icons/
│   ├── favicon.svg       站点图标（矢量）
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── icon-maskable-512.png
│   └── apple-touch-icon.png
├── zhuxinsuan/
│   └── index.html        珠心算 · 听算
├── .nojekyll             关闭 GitHub Pages 的 Jekyll 处理
└── .gitignore
```

### 部署到 GitHub Pages

1. 在 GitHub 新建仓库，名字叫 `abacus`
2. 把本文件夹里的内容推到仓库根目录（不是再套一层文件夹）
3. 仓库 Settings → Pages → Source 选 `Deploy from a branch`，分支 `main`、目录 `/ (root)`
4. 等一两分钟，访问 `https://<你的用户名>.github.io/abacus/`

命令行推送：

```bash
cd ~/Desktop/abacus
git init
git add -A
git commit -m "算盘 · 初版"
git branch -M main
git remote add origin https://github.com/<你的用户名>/abacus.git
git push -u origin main
```

### 更新后手机上还是旧版？

改完页面内容，**一定要把 `sw.js` 里的 `VERSION` 加一**（比如 `1.0.0` → `1.0.1`）。否则浏览器会继续用缓存里的旧文件。

### 新增一个工具

1. 建文件夹，名字用英文小写（如 `abacus-basics/`），里面放 `index.html`
2. 在首页 `<main>` 里复制一张 `.card`，改 `href`、标题、描述、标签
3. 卡片里的中英文都要加：中文写在 HTML 里，英文写进页面底部脚本的 `TEXT.en`
4. 把新页面加进 `sw.js` 的 `ASSETS`，并把 `VERSION` 加一
5. 推送

### 数据与隐私

不联网、不上传。以下内容只存在你这台设备的浏览器里：

| 键 | 内容 |
|---|---|
| `zhuxin.practice.v1` | 每日练习组数 |
| `zhuxin.timer.v1` | 练习计时 |
| `abacus.lang` | 中英文选择 |

清空浏览器数据会一起清掉。换设备不会同步。

### 已知限制

- 语音播报用的是系统自带的中文语音；设备上没有中文语音包时，只能用上方式子代替
- 拨珠声、语音都需要先点一下页面才会出声（浏览器的自动播放限制）

---

## English

### What it is

A small set of browser-only tools for practising on the suanpan (1 upper bead + 4 lower beads) and mental abacus. No backend, no external dependencies. Every tool is a single HTML file and works offline.

### What's inside

| Tool | Path | About |
|---|---|---|
| Mental Abacus · Listening | [`zhuxinsuan/`](./zhuxinsuan/) | Hear a number, add it on the abacus. 4–8 columns, 3–15 addends, four speeds. Practise with the frame covered, enter beads yourself, or watch the 1-to-100 demo. Includes addition/multiplication tables, a practice calendar and a timer |

`index.html` is the entry page. Switch between Chinese and English with the 「中 / EN」 toggle in the top-right corner.

### Install on a phone (PWA)

It must be served over `https://`. Opening the file directly from disk (`file://`) cannot be installed.

- **iPhone / iPad**: open in Safari → Share → *Add to Home Screen*
- **Android**: open in Chrome → menu → *Install app* / *Add to Home screen*

Once installed it opens in its own window without an address bar, and works offline.

### Project layout

```
abacus/
├── index.html            entry page (Chinese / English)
├── manifest.json         web app manifest
├── sw.js                 offline cache
├── icons/
│   ├── favicon.svg       site icon (vector)
│   ├── icon-192.png
│   ├── icon-512.png
│   ├── icon-maskable-512.png
│   └── apple-touch-icon.png
├── zhuxinsuan/
│   └── index.html        mental abacus · listening
├── .nojekyll             disable Jekyll on GitHub Pages
└── .gitignore
```

### Deploy to GitHub Pages

1. Create a GitHub repository named `abacus`
2. Push the contents of this folder to the repository root (do not nest it in another folder)
3. Repository Settings → Pages → Source: `Deploy from a branch`, branch `main`, folder `/ (root)`
4. Wait a minute or two, then open `https://<your-username>.github.io/abacus/`

```bash
cd ~/Desktop/abacus
git init
git add -A
git commit -m "Abacus · first release"
git branch -M main
git remote add origin https://github.com/<your-username>/abacus.git
git push -u origin main
```

### Phone still shows the old version?

After editing any page, **bump `VERSION` in `sw.js`** (e.g. `1.0.0` → `1.0.1`). Otherwise the browser keeps serving the cached files.

### Adding a new tool

1. Create a folder with a lowercase English name (e.g. `abacus-basics/`) and put an `index.html` inside
2. Copy a `.card` in the entry page's `<main>` and change the `href`, title, description and tags
3. Provide both languages: Chinese lives in the HTML, English goes into `TEXT.en` in the script at the bottom of the page
4. Add the new page to `ASSETS` in `sw.js` and bump `VERSION`
5. Push

### Data and privacy

Nothing is uploaded. The following stay in this device's browser only:

| Key | Contents |
|---|---|
| `zhuxin.practice.v1` | Rounds practised per day |
| `zhuxin.timer.v1` | Practice timer |
| `abacus.lang` | Language choice |

Clearing browser data clears these too. They do not sync across devices.

### Known limitations

- Speech uses the system's built-in Chinese voice. Without a Chinese voice pack, the on-screen expression is the fallback
- Audio only starts after you tap the page once (browser autoplay policy)
