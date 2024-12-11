---
layout: section
---

# Apple Vision Pro

---
level: 2
---

# Safari on visionOS
<br />

Vision Proに搭載されているブラウザはSafari

Safari on visionOSではWebXR Device APIが使える

visionOS 2.0からフラグの有効化不要で  
WebXRアプリの実行が可能に

WWDC 2024でもWebXRに関係するセッションが２つ

- [Build immersive web experiences with WebXR](https://developer.apple.com/videos/play/wwdc2024/10066)
- [Optimize for the spatial web](https://developer.apple.com/videos/play/wwdc2024/10065)

---
level: 2
layout: two-cols
---

# Safari on visionOSで使える機能

- VRモードは使用可能
- ARモードは使用不可能
  - プライバシーの観点からカメラのアクセスができない状況
- Hand Input（ハンドトラッキング）が使用可能
- Immersive Webの[サポートテーブル](https://immersiveweb.dev/#supporttable)でも同様の記述

::right::

<img src="/visionchess.png" class="ml-10 mt-30"/>

[『News from WWDC24:WebKit in Safari 18 beta』より引用]{font-size=15px}
[https://webkit.org/blog/15443/news-from-wwdc24-webkit-in-safari-18-beta/]{font-size=15px}

---
layout: section
---

# Meta Quest

---
level: 2
---

# Meta QuestとDevice APIの概要
<br/>

Meta Quest3をはじめとするデバイスではQuestブラウザを搭載

もちろんQuestブラウザはWebXR Device API対応

WebXR Incubation Flagの有効化は必要なものの、  
Questブラウザは多くのWebXR Moduleを実装している

モバイルでは動かないような機能もいくつかあり、触っていて楽しい

---
level: 2
layout: two-cols
---

# Mesh Detection
<br/>

WebXR Mesh Detection Module　　
https://immersive-web.github.io/real-world-meshing/

空間の形状を取得できる機能

事前にスキャンしてあるメッシュを取得できる形なため  
メッシュは動的に変わらない

WebXR SamplesのProposal欄にサンプルがあるので、気軽に試すには良い

::right::

<img src="/meshh.jpg" class="ml-10"/>

[WebXR SampleのAR Mesh Detectionが動作している様子]{font-size=15px}

---
level: 2
layout: two-cols
---

# Body Tracking
<br/>

WebXR Body Tracking Module  
https://cabanier.github.io/webxr-body-tracking/

Quest3の場合、  
手と頭から全身骨格の姿勢を推定する  
ユニークな機能

WebXR Samplesにはサンプルがないが、  
個人的に試せるものを公開しています  
https://drumath2237.github.io/babylon-body-tracking-testbed/

::right::

<Youtube id="EF8-pKhncAE" width="450" height="450" />

---
level: 2
layout: two-cols
---

# Depth Sensing
<br/>

WebXR Depth Sensing Module  
https://www.w3.org/TR/webxr-depth-sensing-1/

Depth画像を取得できる機能  
オクルージョンや衝突判定などに活用できる

XR体験のプレゼンスがぐっと上がる仕組みなので注目している

Chrome for Andoroidにも実装されているが、
画像フォーマット定義に齟齬があるようでそのままでは動かない可能性もある

::right::

<Youtube id="TORgatMXFRg" width="450" height="450" />


---
layout: section
---

# Wolvic

---
level: 2
layout: two-cols
---

# Wolvicブラウザ
<br />

XRデバイス向けブラウザ

Igalia主導のもとオープンソースで開発されている  
https://github.com/Igalia/wolvic

Firefox Realityというブラウザの後継

Immersive Webのサポートテーブルにも記載

::right::

<img src="/wolvic.png" class="ml-10 mt-20"/>

---
level: 2
---

# Wolvicに期待する部分

- Androidベース・SnapdragonSpaces系端末に広く対応
  - Quest系, Vive Focus, PICO系
  - ThinkReality A3 / Lynx R1
- 新しいXRデバイスが出てきている
  - PICO 4 Ultra
  - QONOQ Devices MiRZA
  - Quest 3S
  - Meta Orion
  
---
level: 2
# layout: two-cols
---

# Chromium版アップデート
<br/>

WolvicはGecko版とChromium版が走っており、  
とうとうChromium版でAR Moduleが利用可能に！

<img src="/chromium.png" class="scale-80"/>

