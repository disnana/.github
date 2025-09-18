==============================================================================
Disnana Projects — DictSQLite and CARVS
==============================================================================

.. contents::
   :local:
   :depth: 2

概要
====

Disnana の公開プロジェクトのうち、次の2件を紹介します。

- DictSQLite — Python から SQLite を辞書のように扱える軽量ライブラリ
- CARVS — Windows ユーザーのパスワードを OTP 化するツール

DictSQLite
==========

.. image:: https://img.shields.io/pypi/v/dictsqlite.svg
   :target: https://pypi.org/project/dictsqlite/
   :alt: PyPI Version
.. image:: https://img.shields.io/pypi/pyversions/dictsqlite.svg
   :target: https://pypi.org/project/dictsqlite/
   :alt: Python Versions
.. image:: https://static.pepy.tech/badge/dictsqlite
   :target: https://pepy.tech/project/dictsqlite
   :alt: Downloads
.. image:: https://img.shields.io/badge/License-MIT%20(Custom)-blue.svg
   :target: https://github.com/disnana/DictSQLite/blob/main/LICENSE
   :alt: License

「辞書のように」直感的な API で SQLite を操作できる Python ライブラリです。テーブルやカラムの自動生成、トランザクション、暗号化など、実用的な機能を小さなフットプリントで提供します。

特長
----

- 辞書ライクなインターフェース: ``db['key'] = 'value'``
- スキーマ自動管理: テーブル/カラムを必要に応じて作成
- トランザクション: ``with db.transaction():`` の簡潔な構文
- オプションの AES 暗号化
- マルチプロセス/スレッド安全性（``portalocker`` によるロック）
- 依存最小（実質 Python 標準 + 一部軽量依存）

インストール
------------

.. code-block:: bash

   pip install dictsqlite

クイックスタート
----------------

.. code-block:: python

   from dictsqlite import DictSQLite
   import os

   db_file = 'sample.db'
   if os.path.exists(db_file):
       os.remove(db_file)

   db = DictSQLite(db_file)

   # 基本操作
   db['name'] = 'Alice'
   db['age'] = 30
   db.update({'city': 'New York', 'country': 'USA'})

   print(db['name'])        # -> Alice
   print(db.get('city'))    # -> New York
   del db['country']
   print('country' in db)   # -> False

   # テーブル機能
   users = db.table('users')
   users['user1'] = {'name': 'Bob', 'age': 25}
   users['user2'] = {'name': 'Charlie', 'age': 35}

   # トランザクション
   try:
       with db.transaction() as t:
           t['status'] = 'pending'
           raise ValueError("Something went wrong")
   except ValueError:
       pass

   print(db.get('status'))  # -> None（ロールバック済み）

   db.close()

ドキュメント
------------

- 日本語: https://github.com/disnana/DictSQLite/blob/main/documents/japanese.md
- English: https://github.com/disnana/DictSQLite/blob/main/documents/english.md

ライセンス
----------

Custom MIT License（クレジット表記のお願いを含みます）

リンク
------

- リポジトリ: https://github.com/disnana/DictSQLite
- PyPI: https://pypi.org/project/dictsqlite/


CARVS
=====

Windows ユーザーのパスワードを OTP（ワンタイムパスワード）化するユーティリティです。セキュリティ層の追加としての利用を想定しています。

.. warning::

   少なくとも v0.0.0.6 までは一部攻撃に弱い旨が案内されています。
   BitLocker 等による追加保護の併用を強く推奨します。

.. important::

   利用にはスマートフォンおよび Google Authenticator が必須です。

.. note::

   一部サードパーティ製セキュリティソフトをご利用の場合、
   ``c:\passchange.exe`` を検知除外（許可リスト）へ登録することが推奨されています。

セットアップのヒント
--------------------

起動しない場合は Visual Studio の C ランタイムが不足している可能性があります。以下から最新を入手し、ZIP 内の ``install_all.bat`` を管理者権限で実行してください。

- Visual C++ Runtime All-in-One: https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/

開発状況・予定
--------------

- 使い方/解説動画の公開予定
- ソースコードの一部公開予定
- セキュリティ強化および解析対策の強化を継続

ライセンス
----------

BSD 3-Clause

リンク
------

- リポジトリ: https://github.com/disnana/CARVS


サポート・連絡先
================

- 各リポジトリの Issues をご利用ください
- メール: support@disnana.com
- DictSQLite Discord: https://discord.gg/KzeHDrgwAz