# STEWP
STEWPはWP REST APIを利用して、現在運営しているWEBサイトにWordPressの記事を表示させます。
設定から、デザインや表示する項目の有無などを切り替えることができます。
また、カテゴリー、タグ、キーワード検索、関連記事表示にも対応しています。

## 使い方
ダウンロードした後、stewpフォルダごと運営中のサイトにアップロードしてください。

### 設定
1. `config.sample.json`を参考に`config.json`をstewpフォルダ内に作成します。
2. `wpUrl`に取得したいWordPressサイトのURLを入力します。
3. `post.articlePagePath`に記事を表示したいページの相対パスを入力します。

### 記事一覧の表示
記事一覧を表示したいページで`index.bundle.js`を読み込みます。読み込む際はdefer属性をつけてください。

例:
```
  <head>
    <script src="stewp/index.bundle.js" defer></script>
  </head>
```

その後、記事一覧を表示したい場所に以下を追加してください。

```
  <div id="stewpList">
    <stewp-list v-if="isStewpList" :app-config-object="appConfig"/></stewp-list>
  </div>
```

### 記事詳細の表示

記事一覧を表示したいページで`article.bundle.js`を読み込みます。読み込む際はdefer属性をつけてください。

例:
```
  <head>
    <script src="stewp/article.bundle.js" defer></script>
  </head>
```

その後、記事一覧を表示したい場所に以下を追加してください。

```
  <div id="stewpArticle">
    <stewp-article v-if="isStewpArticle" :app-config-object="appConfig"/></stewp-article>
  </div>
```
## 設定

| Property | Type | Description |
----|----|---- 
| wpUrl | String | 記事を取得するWordPressサイトのURLです。 |

### color
STEWPで使われる色の設定です。

| Property | Type | Description |
----|----|---- 
| mainColor | String | 装飾のメインで使われるカラーです。 |
| subColor | String | 装飾のサブで使われるカラーです。 |
| baseColor | String | 背景色で使われるカラーです。一部スタイルでは対応していません。 |
| accentColor | String | ボタンやリンクで使われるカラーです。 |
| fontColor | String | フォントのカラーです。 |

### list
記事一覧の設定です。

| Property | Type | Description |
----|----|---- 
| style | Number | 記事一覧のデザインを変更します。現在は0〜4までの5種類に対応しています。 |
| pickUp | Boolean | 一つ目の記事を大きく表示するかどうか。 |
| totalArticles | Boolean | 総記事数の表示するかどうか。 |
| perPage | Array | 選択式の表示記事数の数値を設定します。空にすると、表示しません。 |
| filter.category | Boolean | カテゴリー検索を使用するかどうか。 |
| filter.tag | Boolean | タグ検索を使用するかどうか。 |
| filter.keyword | Boolean | キーワード検索を使用するかどうか。 |
| pagination | Boolean | ページネーションを表示するかどうか。 |

### post
記事一覧の記事表示設定です。

| Property | Type | Description |
----|----|---- 
| articlePagePath | String | 表示するページへのパスです。 |
| paramsName | String | 記事を特定するためのURLパラメータのkey名です。 |
| author | Boolean | 投稿者を表示するかどうか。 |
| categories | Array | カテゴリーを表示するかどうか。 |
| tags | Boolean | タグを表示するかどうか。 |
| modified | Boolean | 更新日を表示するかどうか。 |

### article
記事詳細の設定です。

| Property | Type | Description |
----|----|---- 
| customField.use | Boolean | カスタムフィールドからの記事取得を有効にするかどうかです。記事一覧以外から記事詳細ページにリンクするために使用します。 |
| customField.originalParamsName | String | 記事一覧以外でページを表示するために使用している固有URLパラメータのkey名です。 |
| customField.settinglParamsName | String | カスタムフィールドで設定した記事の固有URLパラメータのkey名です。 |
| style | Boolean | 現在未使用です。 |
| author | Boolean | 投稿者を表示するかどうか。 |
| style | Boolean | 投稿者を表示するかどうか。 |
| categories | Array | カテゴリーを表示するかどうか。 |
| tags | Boolean | タグを表示するかどうか。 |
| modified | Boolean | 更新日を表示するかどうか。 |
| share.link | Boolean | リンクのコピーボタンを使用するかどうか。 |
| share.facebook | Boolean | facebookシェアボタンを使用するかどうか。 |
| share.twitter | Boolean | twitterシェアボタンを使用するかどうか。 |
| pocket.twitter | Boolean | pocketボタンを使用するかどうか。 |
| relatedList.display | Boolean | 関連記事を表示するかどうか。 |

### ライセンス

Created by Mirek Geckou CCL. Released under the MIT License.
