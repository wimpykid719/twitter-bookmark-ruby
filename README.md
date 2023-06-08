## 最初に

ツイッターのバックアップではブックマークまで保存してくれないためAPIをたたくことにした。
結論からいうと今回作成したコードでは全てのブックマークを取得できなかった。
全部で122件あったのだが107件までしかとれなかった。
`$max_results` を調整することで107件までとれたがそうしないと95件までとかしかとれなかった。

ドキュメントには最新の800件まで取得出来ると書かれていたため本来であるなら取得できるはずだが、出来なかった。

## 環境構築

リポジトリを好きなフォルダにcloneする。
環境変数はあらかじめ取得して docker-compose に記載しておく。

### ブックマークを取得

バックエンドのコンテナをビルドして起動するには

```bash
# 初回起動時のコマンド
docker-compose up --build

# コンテナに入る際は
docker-compose exec backend bash

# ブックマークを取得してJsonに書き出す
ruby bookmarks_lloup.rb
```

## 最後に

基本的には公式[Twitter-API-v2-sample-code](https://github.com/twitterdev/Twitter-API-v2-sample-code/blob/main/Bookmarks-lookup/bookmarks_lookup.rb)のサンプルコードを参考に `next_token` という次のページトークンがあればデータを取得するを再帰的に行っている。