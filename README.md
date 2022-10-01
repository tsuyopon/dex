# 概要
dexのカスタムサンプルです。
修正内容はv2.28.1を基にしています。

変更点詳細
- https://github.com/tsuyopon/dex/compare/v2.28.1...v2.28.1_custom

# セットアップ

レポジトリをcloneしたらdex直下に移動して、下記の証明書を発行します。
```
$ export SAN=IP.1:127.0.0.1
$ ./examples/grpc-client/cert-gen
```

サーバを起動します。
以下の設定ファイルに記述されたclient_id=test1が登録されていることを確認してください
```
$ ./bin/dex serve examples/grpc-client/config.yaml
```

クライアントを起動します。
アプリケーション内部でclient_idとしてtest1が指定され、そのパスワードもプログラム上で指定されていることに注意します。
```
$ ./bin/example-app
```

起動したら以下にアクセスします。
- http://localhost:5556/

画面が表示されたら何も入力せずにそのまま「LOGIN」ボタンを押下して、
Emailを選択して以下の値を入力します(これはconfig.yamlに記載されています)
- admin@example.com
- password

あとは「Grant Access」をクリックして、アクセスの承認を行います。

なお、今回はconfig.ymlに静的に設定を記載した例ですが、
動的にClientIDを発行したい場合にはGRPC API経由で発行することができます

# 変更点
- テスト用のdb(sqlite3)の追加。テスト用ClientID, Secretの設定
- コメントの追加
- 設定ファイルの一部修正
- ログの埋め込み
- Connecterは以下のケースにだけログを埋め込みしている。後は必要に応じて追加する
  - authproxy/mock
  - authproxy/oidc
  - authproxy/authproxy

