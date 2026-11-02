# 忆潮空间 · 曜康个人站

一个纯静态的个人 OC 网站：首页四平台扩列按钮 + 世界观 + 角色档案 + 主线剧情 + 画廊。
桌面端、手机端各自排版，不依赖任何外部库、外部字体或后端服务。

## 怎么看

直接双击 `index.html` 用浏览器打开就能看，不需要装任何东西。

## 文件结构

```
yichao-space/
├─ index.html          整站（HTML + CSS + JS 都在里面）
├─ assets/             图片
│  ├─ yourkon-night.jpg        曜康 · 星夜回眸（首页主视觉）
│  ├─ yourkon-moon.jpg         曜康 · 月光之下
│  ├─ yourkon-sticker.jpg      曜康 · 贴纸立绘
│  ├─ yourkon-paw.jpg          曜康 · 爪
│  ├─ unya-city.jpg            乌奈雅 · 夜城（原图，灯箱用）
│  ├─ unya-city-portrait.jpg   乌奈雅 · 夜城（4:5 裁切，档案卡用）
│  ├─ unya-chibi.jpg           乌奈雅 · 立绘
│  └─ unya-sheet.jpg           乌奈雅 · 设定参考
└─ README.md
```

## 怎么发布

这是纯静态站点，**把 `index.html` 和 `assets` 文件夹一起上传**到任意静态托管即可。

- **GitHub Pages**：新建仓库 → 上传这些文件到根目录 → Settings → Pages → 选 `main` 分支根目录。
- **Cloudflare Pages / Vercel / Netlify**：直接拖拽这个文件夹上传，不用填构建命令。
- **国内服务器 / 阿里云 OSS / 腾讯云 COS**：把文件传到站点根目录，绑定域名即可。
- 也可以压缩成 zip 发给别人，解压双击就能看。

## 怎么改内容

全部在 `index.html` 里，按注释搜关键词最快：

| 想改什么 | 搜什么 |
| --- | --- |
| 首页四个社交按钮的链接 | `class="port"`，改 `href` |
| 底部那排小链接 | `class="contact-links"` |
| 名字、标语 | `class="hero"` 区块里的 `曜康` / `yourkon` |
| 世界观文案 | `id="world"` 区块 |
| 角色档案（身份、状态等） | `id="characters"`，每张卡的 `<dl class="dl">` |
| 剧情正文 | `id="story"`，每段 `<p>` 和 `<blockquote>` |
| 画廊图片与说明 | `id="gallery"`，`data-cap` 是说明，`data-src` 是大图 |
| 配色 | 顶部 `:root` 里的 `--gold`、`--jade`、`--ink` 等 |

### 加一张新图

1. 图片丢进 `assets/`，宽度建议 ≤ 1200px、体积 ≤ 300KB（JPEG）。
2. 画廊里复制一段 `<figure class="gitem" ...>`，改 `data-src`、`data-cap` 和 `alt` 即可。

### 三个角色的图

- 曜康、乌奈雅的图可以直接换同名的文件，页面不用改。
- 蒙卡纳暂时没有立绘，用的是「档案占位卡」。以后有图了，把
  `<div class="placeholder">…</div>` 整段换成
  `<div class="frame"><img src="assets/monkana.jpg" alt="蒙卡纳"></div>` 就行。

## 一点说明

- **字体**：故意没用 Google Fonts。标题走系统宋体 / 苹方，正文走微软雅黑 / 苹方，
  国内网络和断网情况下都能立刻显示，不会出现字体加载卡顿。
- **手机端**：首页把名字和四个按钮排在前面，保证一进站就能看到四个扩列入口；
  角色立绘、剧情、画廊依次往下。
- **动效**：背景的「记忆精华」光点用 canvas 绘制，系统开了「减少动态效果」时会自动静止。
- 剧情部分只写到第一章，没有剧透结局；主线脉络最后一环停在「抉择」，标注了「故事还在写」。