# 算盘 · Abacus

珠算练习与小工具，纯前端、可离线安装。

Abacus practice and tools. Pure front end, installable and offline-ready.

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

### Phone still shows the old version?

After editing any page, **bump `VERSION` in `sw.js`** (e.g. `1.0.0` → `1.0.1`). Otherwise the browser keeps serving the cached files.

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
