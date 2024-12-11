---
layout: section
---

# WebXR/WebXR Device API
# について整理

---
level: 2
---

# WebXRとは

- Webブラウザ上で動作するXR体験
- いいところ👍
  - ユーザ：アプリのインストール不要でXRコンテンツを楽しめる
  - 開発者：ストアを介さずにXRアプリをリリース・アプデできる
  - クロスデバイス性

![space ar](/spacear.png){width=400px}

---
level: 2
layout: two-cols
---

# WebXRの実現手段

<br />

WebXRを実現する手段はいくつか<br />存在する（→）

中には包含関係にあるものもある

「これを使っておけばよし」  
という選択肢はなく  
それぞれメリットデメリットがある

特に商用利用の場合は  
要件に応じて適切な技術選定が必要


::right::

<br/>

- 8thwall / Niantic Studio
- Three.js
- Babylon.js
- PlayCanvas
- palanAR
- Zapworks
- MyWebAR
- A-Frame
- AR.js
- Unity WebXR Export

---
level: 2
layout: two-cols
---

# WebXR Device APIとは
<br/>

WebXRのAPIにおける”標準仕様”

W3CのImmersive Web WGが策定  
https://immersiveweb.dev/

ブラウザの標準機能として実装されているため、
サードパーティを必要としない

::right::

<img src="https://immersiveweb.dev/webxr-logo.svg" class="ml-5 mt-30"/>

---
level: 2
---

# モバイルWebARにおけるARエンジン事情
<br />

Device APIはiOSではほぼ動かない[^1]という厳しい問題がある

WebARの実現のためにDevice APIを使い、iOSサポートをしないか  
もしくは別の選択肢をとる必要が出てくる

→World Tracking(= 6DoF)が可能な手段であれば、  
8thwallやZapworksなどが選択肢になる

[^1]:正確にはiOSのバージョンによってはWebXR機能を有効化できたり、Safariではない専用アプリを使うことも可能

<style>
  .footnote-item, .footnote-item p{
    font-size:13px
  }
</style>

---
level: 2
---

## Babylon.jsと8thwallの比較

![alt text](/bab8th.png)

---
level: 2
---

# HMDとDevice API
<br/>

HMDの場合はiOSほど制限のある環境は今のところない

主要なHMD環境は少なくともWebXRモードへ移行できるようなブラウザを搭載  
(e.g. Quest, VisionPro, PICO, HoloLens...)

WebXR Device APIを気兼ねなく使える  
→スマホでつくっていたWebXRアプリをそのまま動かせるかも

8thwallのMetaversal Deploymentのような  
モバイルでは非DeviceAPIだったツールも  
独自エンジンとDeviceAPIを切り替えられるようにしている（すごい）

非モバイルデバイスの状況はDeviceAPIが目指す理想状態に近い