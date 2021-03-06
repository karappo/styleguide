# HTML/CSS コーディング・ガイドライン

## はじめに

本文書は、株式会社Karappoでの HTML/CSS コードのスタイル規準を定めるものである。
受注案件でクライアント側に別のガイドラインがある場合は、そちらを優先的に準拠する。


## 目次

- [文字エンコーディング](#encoding)
- [インデント](#indent)
- [body要素のclassおよびid属性](#body_class_id)
- [classやidの命名規則](#class-id)
- [ディレクトリ構成](#directory)
- [画像ファイル名](#image_name)
- [構文チェック](#validate)
- [メールアドレスの書き方](#email)


<a name="encoding"></a>
## 文字エンコーディング

- **[MUST]** 特別な理由がない場合はスクリプトのエンコーディングは UTF-8 にすること

<a name="indent"></a>
## インデント

- **[MUST]** 1レベルのインデントに2つの空白（スペース）を使用する。水平タブを使用しない
理由：Githubなどブラウザ上でソースを表示する際にインデントが揃わないなどの問題が起こりやすい


<a name="body_class_id"></a>
## body要素のclassおよびid属性

- **[MUST]** idではなく、classのみを付加する
理由：idだと強制力が強すぎて、あとで調整しにくくなることが多い

```html
// GOOD
<body class="top ja">
</body>

// BAD
<body id="top" class="ja">
</body>
```

ただし、IE6対応が必要な場合は、CSSで`body.top.ja`のような複数のクラスを指定することができないので、この限りではない。


<a name="classid"></a>
## classやidの命名規則

- **[MUST]** ハイフンはダブルクリックで一括選択できないエディタが多いため、単語の区切りにはアンダーバーを使用する

```html
// GOOD
<div class="profile_area">
</div>

// BAD
<div class="profile-area">
</div>
```

<a name="directory"></a>
## ディレクトリ構成

- **[SHOULD]** 以下の構成に従う

```
.
├─ _assets
│   ├── database
│   │　　├── create_backup.sh
│   │　　└── backup.sql
│   └── design.psd
├─ img
│   └── logo.png
├─ lib
│   ├── blueimp
│   │　　├── blueimp-gallery.css
│   │　　└── blueimp-gallery.js
│   ├── jquery.min.js
│   └── PIE.htc
├─ script
│   └── common.js
├─ style
│   └── common.css
└─ index.html
```

| directory  | contents          |
|:---------- |:----------------- |
| _assets    | サイト上では直接参照しないが、バージョン管理に含めたいファイルなどを格納。         |
| img        | 画像ファイル         |
| lib        | ライブラリファイル。複数のファイルを含むライブラリの場合は、ディレクトリにまとめる。 ※1 |
| script     | Javascriptファイル  |
| style      | CSSファイル         |


***※1 ライブラリディレクトリのバリエーション***

自作ライブラリとそれ以外のライブラリを区別したい場合は、下記のようにしても良い。

| directory  | contents               |
|:---------- |:---------------------- |
| lib        | 自作ライブラリ            |
| vendor     | サードパーティ製のライブラリ |


<a name="image_name"></a>
## 画像ファイル名

- **[MUST]** 長すぎない範囲で内容が分かる名前にする。扱う量が多いときはその限りではないが、なるべく分かりやすく

連番は、並びが綺麗なのは良いが、ファイルを探すときに分かりにくくなったり、画像や見出しの順番が変わった際に連番が崩れたりするため、極力避ける。
（例：スライドショーの順番変更）

- **[SHOULD]** 以下の基準にそって表記を揃える

ファイル名はURLにも現れるため、見た目が綺麗になるように、アンダーバーではなくハイフンを使う。
（例：`fig-1-2.png`）

| 種類                    | ◎ 推奨           | ◯ 可        |
|:---------------------- |:---------------- |:---------- |
| **省略語**              |                  |            |
| ボタン（リンク、その他UI）  | btn              | button     |
| 図                     | fig              | figure, img |
| ナビゲーション            | nav              | menu       |
| **テキスト関係**          |                  |            |
| h1,h2などの見出しで使う画像 | title            |            |
| サブタイトル、リード文      | lead             |            |
| 本文                    | text             |            |
| **その他**              |                   |            |
| スライドショーの画像       | slide-1, slide-2   |            |
| 矢印アイコン系            | arrow-l, arrow-r   |            |
| サムネール画像            | thumb-1, thumb-2   |            |


<a name="validate"></a>
## 構文チェック

- **[MUST]** [Markup Validation Service](http://validator.w3.org/)などを使って、構文チェックをすること

<a name="email"></a>
## メールアドレスの書き方

- **[MUST]** スパムメール対策として、直接メールアドレスを記述することは避ける。ただし、閲覧者が簡単にコピペできることを考慮して下記のように記述する。

```
info@<span style="display: none;">Anti-Spam</span>example.com
```
