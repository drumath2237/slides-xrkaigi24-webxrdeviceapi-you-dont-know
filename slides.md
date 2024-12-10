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
