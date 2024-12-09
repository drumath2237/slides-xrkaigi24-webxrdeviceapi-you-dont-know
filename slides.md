---
# You can also start simply with 'default'
theme: default
title: UnJSを使って軽率にCLIを作ってみたらめちゃくちゃ便利だった
info: v-tokyo 21でのLT登壇資料
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
exportFilename: create-cli-with-unjs
---

# UnJSを使って[軽率に]{style="color:#33CCFF"}
# CLIを作ってみたら
# めちゃくちゃ便利だった

### にー兄さん[@ninisan_drumath](https://twitter.com/ninisan_drumath)  
### v-tokyo #21

---
layout: two-cols
hideInToc: true
---

# にー兄さん

- ソフトウェアエンジニア@HoloLab inc.
- Babylon.js勉強会運営
- Iwaken Lab.

好きなもの

- Babylon.js / WebXR Device API / C#
- ねこ / コーヒー / ウィスキー / ギター

アカウント

- <uim-twitter-alt /> [@ninisan_drumath](https://x.com/ninisan_drumath)
- <uim-github-alt /> [@drumath2237](https:github.com/drumath2237)

::right::

<img src="https://pbs.twimg.com/profile_images/1113849253548269568/4uy_K_LA_400x400.png" class="rounded shadow m-30 h-60"/>

---
hideInToc: true
---

# 本日の話

- 個人開発しているCLIでUnJSを使ってみた
- どんなパッケージを使ったのか、用途別にご紹介
- UnJSのパッケージが気になっている方に刺さると嬉しいです

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
layout: two-cols
---

# create-babylon-app とは

- Babylon.jsのプロジェクトを簡単に作成するためのCLI
- コマンドラインから質問に答えるとプロジェクトができ、そのまま開発できる手軽さが売り

お手元のターミナルでぜひ試してみてください！<twemoji-backhand-index-pointing-down />

```txt
npm create babylon-app
```

GitHub: https://github.com/drumath2237/create-babylon-app

<style>
code.language-txt{
  font-size: 1.2rem
}
</style>

::right::

<img src="/run2.png" class="ml-10 mb-5" />
<img src="/run-web.png" class="ml-10" />

---
level: 2
---

# create-babylon-appの要件

1. 作成するプロジェクト名を指定
2. テンプレートを選択
3. 設定を反映したプロジェクトを作成

create-viteやNuxt CLIの動作に近いので参考にしている。

---
level: 2
layout: two-cols
---

# UnJSとは

> UnJSは、Nuxt 開発チームが中心となって開発・メンテナンスされている、あらゆるJavaScriptフレームワーク上で統一的に動作するユーティリティーツール・ライブラリ群です。[^*]

[^*]:『[UnJS にどんなツールがあるのか、上位30件すべて紹介してみた（前編）](https://zenn.dev/ytr0903/articles/c6c42147ed29be)』より

つまりUnJSはパッケージそのものではなく、パッケージ群のこと。

2024/07/26時点で63個ものパッケージが提供されていてすごい<twemoji-backhand-index-pointing-right/>

<style>
.footnote-item,.footnote-item p{
  font-size: 1rem
}
</style>


::right::

<img src="https://unjs.io/favicon.svg" class="mt-5 ml-10 w-[6rem]" />

<img src="/unjs.png" class="ml-10 mt-5" />

---
level: 2
layout: two-cols
---

# UnJSを使ってみたい
<br/>

便利なパッケージがたくさんあるんだなぁ

自分でメンテしているCLIに使えないかな......？

当初はcitty目当てで調べ始めた


::right::

<v-click>
GANGANさんのツイートを発見

<Tweet id="1744908147733692742" scale="0.7"/>
</v-click>


---
layout: section
---

# 使用したUnJSパッケージ

---
level: 2
---

# 使用したパッケージ一覧

- unbuild
- citty
- jiti
- consola
- giget
- pkg-types

---
level: 2
layout: two-cols
---

# <twemoji-cityscape-at-dusk /> citty

> Elegant CLI Builder

いわゆるCLIフレームワーク的なものだと思う

コマンドライン引数やサブコマンドなど、いい感じに設定できて良さげ

今回は`run`に処理を書いただけだけど、自動で`--help`などに対応してくれるのはうれしい

Nuxt CLIの中身を見ると使い方が分かりやすい

::right::

```ts
import { defineCommand, runMain } from "citty";

const main = defineCommand({
  meta: {
    name: "hello",
    version: "1.0.0",
    description: "My Awesome CLI App",
  },
  args: {
    name: {
      type: "positional",
      description: "Your name",
      required: true,
    },
  },
  run({ args }) {
    console.log(`Hi, ${args.name}!`);
  },
});

runMain(main);
```

---
level: 2
layout: two-cols
---

# <twemoji-koala /> consola

> Elegant Console Wrapper

コンソールログをきれいに修飾してくれる

CLI使うときにUIがきれいだとテンションが上がる

他にも`prompt`により対話型の入力を実装できるのがうれしい  
（inquireから移行した）

```ts
consola.info("info");
consola.start("start");
consola.warn("warn");
consola.success("success");
consola.error(new Error("This is an error"));
consola.box("simple box");
await consola.prompt("OK", {
  type: "confirm",
});
```

::right::

<Tweet id="1806034836374851651" scale="0.75"/>


---
level: 2
layout: two-cols
---

# <twemoji-sparkles/> giget

> Download templates and git repositories with pleasure!

GitHubなどからファイルをごそっとダウンロードしてローカルに展開できる

Scaffoldingツールにはもってこいのツール

内部でnypmも使っているので、ダウンロードした後にnpmやpnpmで依存解決も可能

::right::

使用例  
特定のディレクトリも指定できる

```ts {all|3-9}
const githubRepoUrlBase = "gh:drumath2237/create-babylon-app/templates";
const templateName = `${buildTool}-${language}`;
const { dir: appDir } = await downloadTemplate(
  `${githubRepoUrlBase}/${templateName}`,
  {
    dir: projectName,
    install: doInstall,
  },
);
```


<style>
code{
  font-size:0.9rem
}
</style>


---
level: 2
---

# <twemoji-beverage-box/> pkg-types

> Node.js utilities and TypeScript definitions for package.json and tsconfig.json

ディレクトリやファイルパスを指定して  
`package.json`や`tsconfig`をを読み書きできる

自前で書いてもいいけど、型がついたりするのでいい感じ



```ts
// パッケージ名を変更
const packageJson = await readPackageJSON(appDir);
if (packageJson.name) {
  packageJson.name = projectName;
  const jsonPath = path.resolve(appDir, "package.json");
  await writePackageJSON(jsonPath, packageJson);
}
```

<style>
  code{
    font-size: 1rem;
  }
</style>


---
level: 2
layout: two-cols
---

# <twemoji-french-fries /> jiti

> Runtime TypeScript and ESM support for Node.js

開発中にビルドせずに動作を確認するときに使用

もともとはvite-nodeを使っていたが  
なんとなく移行してみた

特殊な使い方はしておらず、シンプルにtsファイルを指定して実行するだけ

```sh
pnpm exec jiti src/run.ts
```

::right::


# <twemoji-package /> unbuild

> A unified javascript build system

ビルドツールの選択肢はいろいろある中で  
元々はtscでコンパイルした.cjsを`bin`に指定して動かしていた

バンドルなども考慮したいと思い移行

Zero Configでも普通に動くし、`build.config.ts`にビルド設定を記述可能

```ts
import { defineBuildConfig } from "unbuild";

export default defineBuildConfig({
	entries: ["./src/index.ts"],
});
```

<style>
code{
  font-size:0.75rem
}
</style>


---
layout: section
---

# おわりに

---
level: 2
layout: two-cols
---

# まとめ

- 自作CLIツールの技術スタックをごそっとUnJSに移行してみた
- するとほぼ全部UnJSで機能が補えてしまった（すごい）
- TypeScriptでCLIを作るときに使ってみてはいかがでしょうか？
  - みんなで<twemoji-backhand-index-pointing-right/>のようになりましょう

::right::

<Tweet id="1814587731051487443" scale="0.8"　class="ml-5"/>

---
level: 2
---

# 参考文献

- UnJS  
https://unjs.io/
- create-babylon-app　v1.0に向けたアプデ作業  
https://zenn.dev/drumath2237/scraps/b085d5f90b65f3
- drumath2237/create-babylon-app  
https://github.com/drumath2237/create-babylon-app
