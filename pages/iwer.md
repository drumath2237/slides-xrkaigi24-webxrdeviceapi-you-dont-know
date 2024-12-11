---
layout: section
---

# Meta Immersive Web Emulator Runtime
# (IWER)

---
level: 2
---

# WebXR開発のデバッグは大変
<br />

うまく環境を作れればホットリロードやデバッガなどの恩恵を受けられる  
→ ネイティブアプリよりもイテレーションを回しやすい

しかし実機デバッグのためには...

- HTTP通信のセットアップ
- コンソール確認用の工夫

などが必要になってくる

---
level: 2
layout: two-cols
---

# Immersive Web Emulator
<br/>

Meta社が提供するImmersive Web Emulator拡張機能

開発者ツールに新しくタブが追加される

PCブラウザでもWebXRモードへ移行することが可能になる

ヘッドセットやコントローラの位置  
トリガー入力などをGUIで操作可能

::right::

<img src="/emulator.png" class="ml-10"/>

---
level: 2
---

# Immersive Web Emulator Runtime(以下IWER)
<br/>

Immersive Web Emulatorでやっていた  
WebXRサポートのエミュレーションをアプリに組み込めるようになった

![demo](https://scontent-nrt1-1.xx.fbcdn.net/v/t39.2365-6/449689975_1051614846296718_599362266642986737_n.gif?_nc_cat=108&ccb=1-7&_nc_sid=e280be&_nc_ohc=2BUmPqNjMF8Q7kNvgGmm4H1&_nc_zt=14&_nc_ht=scontent-nrt1-1.xx&_nc_gid=A5LclQWk4GIKUhbVhKCy7QT&oh=00_AYBiCVHm5Rp2EepzKdEqU2YkUPIzRO475YYB1WxgUT1OrQ&oe=67745CA7){width=400px}

---
level: 2
---

# ツールの導入
<br/>

npmからインストール  
CDN経由で使うことも可能

```sh
npm i iwer
```

Three.jsやBabylon.jsのコードで  
`XRDevice`のセットアップ・インストール

```ts
import { XRDevice, metaQuest3 } from 'iwer';

const xrDevice = new XRDevice(metaQuest3);
xrDevice.installRuntime();
```

これだけでPCからWebXRモードへ移行可能になる

---
level: 2
---

# IWERの面白い部分
<br/>

IWERのAPIは3Dライブラリ非依存

シミュレーションするデバイスの設定や  
操作を`XRDevice`クラスに集約している

```js
xrDevice.ipd = 0.063;
xrDevice.fovy = Math.PI / 2;

const leftController = xrDevice.hands.left; // nullチェック略
leftController.position.set(0, 0, 0);
```

出来合いのデバイス設定が提供されていて  
カスタマイズも可能

```js
import { metaQuest3, metaQuest2, metaQuestPro } from "iwer";
```

---
level: 2
---

# 実際にBabylon.jsで触ってみる

<Youtube id="0wgZj2RnaPg" width="750" height="422"/>

---
level: 2
---

# Action Recording & Playback(beta)
<br/>

XRSessionやXRFrameの情報を記録・再生できる機能も  
記録データはJSONとして保存されるらしいが、  
log出力する関数がある（文字列として受け取れない？）

```js
const recorder = new ActionRecorder(xrSession, refSpace);
// ...
onFrame(xrFrame) {
    if (recording) {
        recorder.recordFrame(xrFrame);
    }
}
recorder.log();
```

キャプチャしたデータをなんらかして取り出し、Playerで再生

```js
player = xrDevice.createActionPlayer(refSpace, capture);
player.play();
```
