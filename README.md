# 李上 Locrian · 个人作品集

线上地址：https://locrian-site.pages.dev

纯静态单页网站：所有内容、样式和脚本都在 `index.html` 里，图片和音频在 `assets/`。
视频放在 Cloudflare R2（见 `index.html` 里的 `MEDIA` 常量），不在这个仓库里。

## 修改作品

作品数据在 `index.html` 底部的 `const Wk=[...]` 数组里，每条一个作品：
`k` 板块（sound / music / aigc）、`t` 标题、`e` 英文名、`d` 简介、`img` 封面、`au` 音频、`v` R2 视频文件名、`ld` 外链按钮。

## 本地预览

```bash
python3 -m http.server 8765
```

## 发布

```bash
wrangler pages deploy . --project-name=locrian-site --branch=main
```
