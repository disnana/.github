# Disnana

Disnanaチームが開発しているツールやライブラリの置き場所です。

主にPythonでデータベース周りのライブラリを作っています。

## 🔗 リンク

- **ホームページ**: https://disnana.com/
- **Disnanaボット**: https://disnana.com/bot
- **GitHub Organization**: https://github.com/disnana

## 📦 主なプロジェクト

### データベース関連

#### NanaSQLite

Dictみたいに使えるSQLiteラッパーライブラリです。

```python
from nanasqlite import NanaSQLite

db = NanaSQLite("mydata.db")
db["user"] = {"name": "Nana", "age": 20}
print(db["user"])
```

- **リポジトリ**: https://github.com/disnana/NanaSQLite
- **PyPI**: https://pypi.org/project/nanasqlite/
- **ドキュメント**: https://nanasqlite.disnana.com/
- **ライセンス**: MIT License

**主な機能:**
- 辞書型の操作感でSQLiteを扱える
- 書き込みは自動で保存される
- ネストした構造もそのまま保存可能
- 暗号化やトランザクションにも対応

#### DictSQLite

NanaSQLiteの前身となるライブラリです。

- **リポジトリ**: https://github.com/disnana/DictSQLite
- **リリースノート**: https://disnana.github.io/DictSQLite-Release-Note/
- **ライセンス**: MIT License

> [!NOTE]
> 新しいプロジェクトではNanaSQLiteの使用を推奨します。

#### NanaSQLite-Server

NanaSQLiteをサーバーとして動かすやつです。

- **リポジトリ**: https://github.com/disnana/NanaSQLite-Server
- **ライセンス**: MIT License

### ツール系

#### ValidKit

バリデーション用のツールキットです。

- **リポジトリ**: https://github.com/disnana/ValidKit
- **ライセンス**: MIT License

#### CalcX

`(10^100)+1-(10^100)` を正確に計算できる電卓です。

Androidの電卓みたいに浮動小数点の誤差を回避します。

- **リポジトリ**: https://github.com/disnana/CalcX
- **ライセンス**: MIT License

### ゲーム

#### neuro-reversi

TypeScriptで作ったリバーシゲームです。

- **リポジトリ**: https://github.com/disnana/neuro-reversi
- **ビルド済み**: https://github.com/disnana/neuro-reversi-pages

### Webページ

#### Disnana-Official-HomePage

公式サイトのソースコードです。

- **リポジトリ**: https://github.com/disnana/Disnana-Official-HomePage
- **公開URL**: https://disnana.com/home

#### DictSQLite-Release-Note

DictSQLiteのリリースノート用サイトです。

- **リポジトリ**: https://github.com/disnana/DictSQLite-Release-Note
- **公開URL**: https://disnana.github.io/DictSQLite-Release-Note/

## 📜 ライセンスと著作権

特に記載がない限り、すべての著作権はDisnanaが保有しており、許可を得ない限り利用することはできません。

公開されているプロジェクトの多くはMIT Licenseで提供されていますが、各リポジトリのLICENSEファイルを必ず確認してください。

### MIT License

MIT Licenseで公開されているプロジェクトはこちらです。

- NanaSQLite
- DictSQLite
- NanaSQLite-Server
- ValidKit
- CalcX

詳細は各リポジトリのLICENSEファイルをご確認ください。

## 📝 備考

> [!WARNING]
> このREADMEは公開リポジトリの情報のみ記載しています。
> 各プロジェクトの利用にあたっては、必ずライセンスを確認してください。
> このREADMEは更新が不定期なので必ず最新の情報をご確認ください。

> [!TIP]
> バグ報告や機能要望は各リポジトリのIssueからどうぞ。

---

Copyright (c) 2024-2026 Disnana. All rights reserved.
