---
# You can also start simply with 'default'
theme: default
title: あなたの知らないWebXR Device APIの話を軽率にご紹介
info: XR Kaigi 2024登壇資料
author: にー兄さん
class: text-left
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
# transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
colorSchema: dark
mdc: true
fonts:
  sans: M PLUS 2
  mono: JetBrains Mono
layout: intro
hideInToc: true
download: true
export:
  dark: true
exportFilename: xrkaigi24-webxr-device-api
---

# あなたの知らない
# WebXR Device APIの話を
# [軽率に]{style="color:#33CCFF"}ご紹介

### にー兄さん[@ninisan_drumath](https://twitter.com/ninisan_drumath)  
### XR Kaigi 2024

---
layout: two-cols
hideInToc: true
---

# にー兄さん

- Babylon.jsとWebXR Device API<br />の宣教師
- ソフトウェアエンジニア
- 株式会社ホロラボ
- Microsoft MVP (Web)
- Babylon.js勉強会運営
- Iwaken Lab.

SNS

- <uim-twitter-alt /> [@ninisan_drumath](https://x.com/ninisan_drumath)
- <uim-github-alt /> [@drumath2237](https:github.com/drumath2237)

::right::

<img src="https://pbs.twimg.com/profile_images/1113849253548269568/4uy_K_LA_400x400.png" class="rounded shadow ml-30 mb-5 h-55"/>
<img src="/realavator.png" class="rounded shadow ml-30 h-55"/>

---
hideInToc: true
---

# アジェンダ

<Toc maxDepth="1"/>

---
layout: section
---

# はじめに

---
level: 2
---

# 本日の話

- 昨年に引き続きWebXR Device APIの話です
- XR Kaigi 2024のテーマは「More Immersive, More Spatial」
- WebXRの話でも、特に非モバイル向けにフォーカス
- 個人的に面白いなと思ってるけどあまり知られていなさそうな話題をピックアップ

## 本日のゴール：

**「WebXR Device APIってこんなことできるんだ！」と感じてもらう**

---
src: "./pages/about-webxr.md"
---

---
layout: section
---

# 個人的面白いWebXR Device APIトピックス

---
level: 2
---

# ここからはDevice APIのトピックのご紹介

- Apple Vision Pro
- Meta Quest3
- Wolvic
- Meta IWERについて

---
src: "./pages/hmd.md"
---

---
src: "./pages/iwer.md"
---

---
layout: section
---

# おわりに

---
level: 2
---

# まとめ

---
level: 2
---

# WebXR Device APIへの期待

---
level: 2
---

# 参考文献

- Apple Vision Pro (visionOS 2.0) における WebXR Device API とその周辺の現状確認  
  https://zenn.dev/ikkou/articles/337f584f7581da
- News from WWDC24:WebKit in Safari 18 beta  
  https://webkit.org/blog/15443/news-from-wwdc24-webkit-in-safari-18-beta/
- Introducing Immersive Web Emulation Runtime (IWER) for Faster WebXR Iteration  
  https://developers.meta.com/horizon/blog/immersive-web-emulation-runtime-iwer-webxr-meta-quest-developer/