# 李上 Locrian · 个人作品集

线上地址：https://locrian-site.pages.dev

纯静态单页网站：所有内容、样式和脚本都在 `index.html` 里，图片在 `assets/img/`。
音频和视频放在 Cloudflare R2 存储桶 `locrian-media`（见 `index.html` 里的 `MEDIA` 常量），不在这个仓库里：音频在 `audio/` 下，视频在根目录。
（Pages 不支持音频分段读取，进度条会拖不动，所以音频也放 R2。）

## 修改作品

作品数据在 `index.html` 底部的 `const Wk=[...]` 数组里，每条一个作品：
`k` 板块（sound / music / aigc）、`t` 标题、`e` 英文名、`d` 简介、`img` 封面、`au` R2 音频路径（如 `audio/winter.mp3`）、`v` R2 视频文件名、`ld` 外链按钮。

## 本地预览

```bash
python3 -m http.server 8765
```

## 发布

```bash
wrangler pages deploy . --project-name=locrian-site --branch=main
```

上传新音频到 R2：

```bash
wrangler r2 object put locrian-media/audio/新歌.mp3 --file 新歌.mp3 --content-type audio/mpeg --remote
```
