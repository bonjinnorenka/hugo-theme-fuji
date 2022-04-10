# 🍥 Fuji 🍥

*注意　この翻訳はforkした作者が勝手につけた日本語訳的なものです。日本語訳は一部にしかつけていません。 

富士は最低限の完全ダークモードをサポートしgithubのマークダウン方式に対応したHugoのテーマです。  
Hugo extended 版が必須です。

![GitHub release](https://img.shields.io/github/v/release/dsrkafuu/hugo-theme-fuji)
![GitHub build status](https://img.shields.io/github/workflow/status/dsrkafuu/hugo-theme-fuji/build-test)
![GitHub license](https://img.shields.io/github/license/dsrkafuu/hugo-theme-fuji)

[English](https://github.com/dsrkafuu/hugo-theme-fuji#readme) | [简体中文](https://github.com/dsrkafuu/hugo-theme-fuji/blob/master/README_CN.md)


対応言語: `cs`, `de`, `en`, `eo`, `fr`, `ja`, `nl`, `pl`, `pt-pt`, `zh-hans`, `zh-hant`. Check the i18n folder to add more languages.

## 📑 目次

- [🍥 Fuji 🍥](#-fuji-)
  - [📑 目次](#-目次)
  - [💻 デモサイト](#-デモサイト)
  - [❗ 注意](#-注意)
  - [🐣 始め方](#-始め方)
  - [🆕 テーマのアップデート](#-テーマのアップデート)
  - [⚙️ 設定](#️-設定)
    - [🎨 Faviconの設定](#-faviconの設定)
    - [❌ ライセンス, 目次とコメント](#-ライセンス-目次とコメント)
    - [🎵 APlayerを使用する](#-aplayerを使用する)
    - [📐 LaTeX や KaTexを表示する](#-latex-や-katexを表示する)
    - [📷 画像の設定](#-画像の設定)
    - [⚓ Markdown render hook](#-markdown-render-hook)
    - [📨 Comments area](#-comments-area)
    - [🔧 CSSを変更する](#-cssを変更する)
  - [✏️ 問題とそれに関する貢献](#️-問題とそれに関する貢献)
  - [📝 License](#-license)
  - [🤝 Annotations](#-annotations)

## 💻 デモサイト

[**デモサイト (fork作者のブログ)**](https://www-ryokuryu-com.pages.dev/)

![Fujiのスクリーンショット](https://raw.githubusercontent.com/dsrkafuu/hugo-theme-fuji/master/images/screenshot.png)

## ❗ 注意

トップページに文章の一部を表示するようになっています。そのため文章の一部をカットしてほしい場所に`<!--more-->`をマークダウンファイルに入れるようにしてください。
[summary divider](https://gohugo.io/content-management/summaries/#manual-summary-splitting)

## 🐣 始め方

まずHugoでサイトを作成します。(hugo new site sitename)
そしたらそこのフォルダ内で以下のコマンドを実行します。(gitのインストールが必要)

```bash
git submodule add https://github.com/bonjinnorenka/hugo-theme-fuji.git themes/fuji
```
もっと詳しく知りたければ[hugoの公式設定ガイド](https://gohugo.io/overview/installing/)を見てください
検索やその他テーマの機能を利用するためにexamplesiteフォルダ内にあるconfig.tomlを親ディレクトリのconfig.tomlにコピーしてください。
(検索やその他独自機能が追加されない場合はcontentのところにexamplesiteのマークダウンを参考にして追加する必要があるかもしれません。)

## 🆕 テーマのアップデート

親フォルダで以下のコマンドを実行してください(gitが必要)

```bash
git submodule update --remote --merge
```

## ⚙️ 設定

### 🎨 Faviconの設定

`[SITEROOT]/layouts/partials/favicon.html` でfaviconを設定できます。
例
```html
<link rel="shortcut icon" href="faviconpass" />
```

### ❌ ライセンス, 目次とコメント

設定は`config.toml`で行います。

すべてに共通する設定
```toml
showLicense = true # Enable or disable ライセンスを表示するかどうか
showToc = true # Enable or disable 目次を表示するかどうか(右側に出ます)
```

投稿ごとに設定する場合
投稿のmetaタグを記述するところに

```yaml
showLicense = true # Enable or disable license 設定した投稿でライセンスを表示するかどうか
showToc = true # Enable or disable 設定した投稿で目次を表示するかどうか
```

特定の投稿ごとにコメントの有効無効を切り替える

```toml
showComments = false # Do not show comments in this post
```
詳しくはこちらで[📨 Comments area](#-comments-area)

### 🎵 APlayerを使用する

投稿内でAPlayerを使用する場合は`aplayer`ショートコードを使用します。

```txt
{{< aplayer urls="/aplayer/fluid.mp3" names="Fluid" artists="Crowander" covers="/aplayer/crowander.jpg" >}}
```

`exampleSite/content/post/aplayer-test.md` に複数のファイルを再生している場合のデモがあります。

### 📐 LaTeX や KaTexを表示する

You can write LaTeX directly in markdown with escape characters:

<!-- prettier-ignore -->
```txt
$$
\begin{matrix}
  a & b \\\\ c & d
\end{matrix}
$$
```

Or use the short code, display style:

<!-- prettier-ignore -->
```txt
{{< math >}}
\begin{matrix}
  a & b \\
  c & d
\end{matrix}
{{< /math >}}
```

Inline style:

<!-- prettier-ignore -->
```txt
{{< math "inline" >}}
\begin{matrix}
  a & b \\
  c & d
\end{matrix}
{{< /math >}}
```

これらの機能を利用するためには`config.toml`で`math = true`にするのを忘れないでください

### 📷 画像の設定

普通の画像の書き方(拡大,遅延読み込み**なし**)

```markdown
![Alt text](test/example.png)
```

ライトボックス対応型(ライトボックス,遅延読み込み**あり**)

<!-- prettier-ignore -->
```html
{{< img-lazy-lbox "Alt text here" "test/example.png" "test/exampleBig.png(option)" >}}
```

ライトボックス対応型(ライトボックス,遅延読み込み**なし**)

<!-- prettier-ignore -->
```html
{{< img-lbox "Alt text here" "test/example.png" "test/exampleBig.png(option)" >}}
```

遅延読み込みのみ

<!-- prettier-ignore -->
```html
{{< img-lazy "Alt text here" "test/example.png" >}}
```

元のhujiテーマにあった画像ショートコードの利用(非推奨)

```html
{{< img-nz-lazy "aspect(ignore)" "Alt text here" "test/example.png" >}}
```

### ⚓ Markdown render hook

You can create the files below in your site to adjust the markdown render hook, see [Hugo's Official Docs](https://gohugo.io/getting-started/configuration-markup#markdown-render-hooks).

You can use `[SITEROOT]/layouts/_default/_markup/render-link.html` to decide whether or not links in the markdown content will open in new tab:

<!-- prettier-ignore -->
```html
<a href="{{ .Destination | safeURL }}"{{ with .Title }} title="{{ . }}"{{ end }}{{ if strings.HasPrefix .Destination "http" }} target="_blank"{{ end }}>{{ .Text | safeHTML }}</a>
```

### 📨 Comments area

広告表示あり　Disqusというサービスを通じて実装

Theme supports Disqus, utterances and DisqusJS (for Mainland China user)。

by default, disqus uses `{{ .Permalink }}` as `url`, `{{ .File.ContentBaseName }}` as `identifier`.

Use the `[SITEROOT]/layouts/partials/comment-*.html` to cover `themes/fuji/layouts/partials/comment-*.html`. Then you can customize the url and identifier, or set multiple api key, add more settings for using DisqusJS. If you want to use DisqusJS, please remember to set `disqusJSApi` to anything in your `config.toml` to load CSS.

### 🔧 CSSを変更する

> Hugo extended 版が必須です

`[SITEROOT]/assets/scss/_custom_var.scss`　を作成することでテーマのフォントや配色の変数を編集することを通してを簡単に変更することができます。

利用できる変数一覧

```scss
$body-font:　sans-serif; //通常時のフォント
$mono-font: 'Cascadia Code', 'SF Mono', 'Fira Code', 'Consolas', $body-font; //主にコードを表示するときに使われるフォント
$title-font: 'Product Sans', $body-font; //タイトルに使うフォント
$body-font-size: 16px; //ほぼすべてのフォントの大きさ

//ライトモード

$light-color-primary: #8aa2d3; // https://irocore.com/aofuji/ リンクとかの色
$light-color-secondary: #8f82bc; // https://irocore.com/fujimurasaki/ カーソルを重ねた時の色
$light-color-focus: #3b469b; // https://irocore.com/aomurasaki/
$light-color-mute: #9ea1a3; // https://irocore.com/suzu-iro/
$light-color-font: #3f4551; // https://irocore.com/konnezu/ フォントの色
$light-color-divider: #e5e2e4; // https://irocore.com/komachinezu/
$light-color-bg: #fffffd; // https://irocore.com/shiro/ 背景の色
$light-color-codebg: #f6f8fa; // GitHub　コードを表示するときのその背景

//ダークモード

$dark-color-primary: #8aa2d3; // https://irocore.com/aofuji/ リンクとかの色
$dark-color-secondary: #bab1df; // https://irocore.com/fujimurasaki/ カーソルを重ねた時の色
$dark-color-focus: #e6e6e6; // https://irocore.com/shironezumi/
$dark-color-mute: #9ea1a3; // https://irocore.com/suzu-iro/
$dark-color-font: #c0c0c0; // https://irocore.com/gin-iro/ フォントの色
$dark-color-divider: #4d5158; // Discord
$dark-color-bg: #2f3136; // Discord　背景の色
$dark-color-codebg: #414449; // GitHub コードを表示するときのその背景
```
`[SITEROOT]/assets/scss/_custom_rules.scss`を使用することでカスタムCSSを追加できます。
*注意 最優先で適用されますが変数が使用されているものには効かないっぽいです。

## ✏️ 問題とそれに関する貢献

[issue tracker](https://github.com/dsrkafuu/hugo-theme-fuji/issues)テーマのバグはこちらのissueを使用してください。 
このテーマはfirefoxでしか完全な動作確認はしてません。なのでほかのブラウザで問題があった場合も頬国していただけると助かります。
## 📝 License

The theme is released under the `Apache License 2.0`, for more information read the [License](https://github.com/dsrkafuu/hugo-theme-fuji/blob/master/LICENSE).

- [Primer CSS - MIT](https://github.com/primer/css/blob/master/LICENSE)
- [APlayer - MIT](https://github.com/MoePlayer/APlayer/blob/master/LICENSE)
- [lazysizes - MIT](https://github.com/aFarkas/lazysizes/blob/gh-pages/LICENSE)
- [DisqusJS - MIT](https://github.com/SukkaW/DisqusJS/blob/master/LICENSE)
- [ionicons - MIT](https://github.com/ionic-team/ionicons/blob/master/LICENSE)
- [Fuse.js - Apache-2.0](https://github.com/krisk/Fuse/blob/master/LICENSE)
- [cloudflare-workers-async-google-analytics - MIT](https://github.com/SukkaW/cloudflare-workers-async-google-analytics/blob/master/LICENSE)
- [art-template - MIT](https://github.com/aui/art-template/blob/master/LICENSE)

**Copyright © 2019-present DSRKafuU <https://dsrkafuu.net/>**

## 🤝 Annotations

Thanks to [community contributors](https://github.com/dsrkafuu/hugo-theme-fuji/graphs/contributors) for great help.

Learned a lot in [Sukka's Blog](https://blog.skk.moe/).
