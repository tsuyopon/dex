# 概要
dexのカスタムサンプルです。
修正内容はv2.28.1を基にしています。

変更点詳細
- https://github.com/tsuyopon/dex/compare/v2.28.1...v2.28.1_custom

# 変更点
- テスト用のdb(sqlite3)の追加。テスト用ClientID, Secretの設定
- コメントの追加
- 設定ファイルの一部修正
- ログの埋め込み
- Connecterは以下のケースにだけログを埋め込みしている。後は必要に応じて追加する
  - authproxy/mock
  - authproxy/oidc
  - authproxy/authproxy

