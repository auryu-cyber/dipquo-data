# dipquo-data

`auryu-cyber/dipquo`(DIP見積Webアプリ)のデータストア。**Private** リポジトリ。

このリポジトリはアプリからのみ書き込まれる想定です。スキーマの詳細は `dipquo` リポジトリの `docs/architecture.md` を参照してください。

## ディレクトリ構成

```
masters/            原価マスター(材料・人件費・梱包・輸送)。品目ごとにディレクトリを切り、
                     ファイル名 = 有効日(YYYY-MM-DD.json)。レコードは追加のみ、上書きしない。
quotes/              見積データ。1見積1JSON(quotes/{product}/{variant}.json)。
logs/                ログイン・操作ログ。月次JSON Lines(logs/{login|activity}/YYYY-MM.jsonl)。
config/              管理者ロールなどのアプリ設定。
```

## 注意

- `masters/**` のファイルはイミュータブル(作成後は編集しない)。価格改定は新しい有効日のファイルを追加する。
- 現時点の `masters/` と `quotes/F4P0010/` の中身は、アプリ実装前の**スキーマ検証用サンプルデータ**です。実際の価格・原価として使う前に、必ず実データで置き換えてください。
