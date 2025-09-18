=======================================================
Disnana組織 - オープンソースプロジェクトへようこそ
=======================================================

.. contents:: 目次
   :depth: 2
   :local:

.. image:: https://img.shields.io/badge/Organization-Disnana-blue.svg
   :target: https://github.com/disnana
   :alt: Disnana Organization

-----

📦 **DictSQLite**
=================

.. image:: https://img.shields.io/pypi/v/dictsqlite.svg
   :target: https://pypi.org/project/dictsqlite/
   :alt: PyPI version

.. image:: https://img.shields.io/badge/License-MIT%20%28Custom%29-blue.svg
   :target: https://github.com/disnana/DictSQLite/blob/main/LICENSE
   :alt: MIT License

.. image:: https://static.pepy.tech/badge/dictsqlite
   :target: https://pepy.tech/project/dictsqlite
   :alt: Downloads

概要
----

**辞書のような簡単さでSQLiteデータベースを扱う**

DictSQLiteは、SQLiteデータベースに対してPythonicで辞書のようなインターフェースを提供し、データベース操作を直感的で分かりやすくします。複雑なSQLクエリを書くことなく、基本的なCRUD（Create、Read、Update、Delete）操作を行いたい開発者向けに設計されています。

主要特徴
--------

✨ **辞書のようなインターフェース**
   SQLiteテーブルを馴染みのある辞書構文で操作（``db['key'] = 'value'``）

🔧 **自動スキーマ管理**
   テーブルとカラムが必要に応じて自動作成

🔒 **トランザクション制御**
   データベーストランザクションを処理するシンプルなコンテキストマネージャー

🛡️ **内蔵暗号化**
   オプションのAES暗号化でデータを保護

⚡ **クロスプロセス・スレッドセーフ**
   ``portalocker`` を使用してデータ整合性を保証

🪶 **軽量・依存関係なし**
   ``portalocker`` と ``cryptography`` 以外は純粋なPython

インストール
------------

pipを使用してインストール：

.. code-block:: bash

   pip install dictsqlite

クイックスタート
----------------

.. code-block:: python

   from dictsqlite import DictSQLite
   import os

   # データベースの初期化
   db = DictSQLite('sample.db')

   # --- 基本操作 ---
   # 作成・更新
   db['name'] = 'Alice'
   db['age'] = 30
   db.update({'city': 'New York', 'country': 'USA'})

   # 読み取り
   print(f"名前: {db['name']}")  # 出力: 名前: Alice
   print(f"都市: {db.get('city')}")  # 出力: 都市: New York

   # 削除
   del db['country']

   # 存在確認
   print('country' in db)  # 出力: False

   # --- テーブルの使用 ---
   users = db.table('users')
   users['user1'] = {'name': 'Bob', 'age': 25}
   users['user2'] = {'name': 'Charlie', 'age': 35}

   print(users['user1'])  # 出力: {'name': 'Bob', 'age': 25}

   # --- トランザクション ---
   try:
       with db.transaction() as t:
           t['status'] = 'pending'
           # この変更はロールバックされます
           raise ValueError("何かがうまくいきませんでした")
   except ValueError as e:
       print(e)

   print(db.get('status'))  # 出力: None（トランザクションがロールバックされました）

   # 接続を閉じる
   db.close()

ドキュメント
------------

詳細な使用法、API リファレンス、高度なトピックについては、公式ドキュメントをご覧ください：

* `英語ドキュメント <https://github.com/disnana/DictSQLite/blob/main/documents/english.md>`_
* `日本語ドキュメント <https://github.com/disnana/DictSQLite/blob/main/documents/japanese.md>`_

ライセンス
----------

このプロジェクトはカスタムMITライセンスの下でライセンスされています。コードの使用と修正は自由ですが、元の作成者への適切なクレジットが必要です。

詳細は `ライセンスファイル <https://github.com/disnana/DictSQLite/blob/main/LICENSE>`_ をご覧ください。

公式リンク
----------

* `GitHubリポジトリ <https://github.com/disnana/DictSQLite>`_
* `PyPIパッケージ <https://pypi.org/project/dictsqlite/>`_

-----

🔐 **CARVS**
============

概要
----

**WindowsユーザーのパスワードをOTP（ワンタイムパスワード）に変換**

CARVSは、Windowsユーザーアカウントのパスワードを、スマートフォンのGoogle Authenticatorアプリで生成されるOTPに変更するセキュリティツールです。

.. warning::
   **重要な注意事項**
   
   少なくともv0.0.0.6までは一部の攻撃に弱いため、Bitlockerを用いた追加の保護を強く推奨いたします。
   
   万が一不具合等でログインできなくなると困るので、パスワードをリセットできるようにしておくことをお勧めしております。

必要要件
--------

.. note::
   * スマートフォン
   * Google Authenticatorアプリ
   * Windows Defender以外のセキュリティソフトをご使用の場合、 ``c:\passchange.exe`` を検知除外リストに追加することを推奨

セットアップメモ
----------------

起動できない場合の対処法：

1. **Visual StudioのCランタイムが必要**
   
   起動できない可能性が高い原因は、Visual Studio C Runtimeの不足です。

2. **ランタイムのインストール手順**

   .. code-block:: text

      1. 以下のサイトから最新版をダウンロード
      2. ZIPファイル内の install_all.bat を管理者権限で実行
      3. 自動セットアップが完了

   `Visual C++ Redistributable Runtime Package <https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/>`_

お知らせ
--------

* 📹 使い方や説明動画は近日中に投稿予定です
* 💾 ソースコードの一部も近日中に公開します
* 🔒 セキュリティ関連の強化、および解析対策の強化等を行っております

ライセンス
----------

詳細は `ライセンスファイル <https://github.com/disnana/CARVS/blob/main/LICENSE>`_ をご覧ください。

公式リンク
----------

* `GitHubリポジトリ <https://github.com/disnana/CARVS>`_

===================
📞 サポート・連絡先
===================

ご質問やサポートが必要な場合は、以下の方法でお気軽にお問い合わせください：

📧 **メールサポート**
   support@disnana.com

🐛 **Issues（問題報告・機能要求）**
   各プロジェクトのGitHub Issuesページをご利用ください：
   
   * `DictSQLite Issues <https://github.com/disnana/DictSQLite/issues>`_
   * `CARVS Issues <https://github.com/disnana/CARVS/issues>`_

💬 **Discord（DictSQLite公式）**
   リアルタイムサポートとコミュニティ

.. note::
   プロジェクトが役に立った場合は、GitHubで ⭐ をお願いします！
   あなたのサポートが開発の励みになります。

-----

.. raw:: html

   <div align="center">
   <p><strong>© 2024 Disnana Organization. All rights reserved.</strong></p>
   </div>