==============================================================================
Disnana Projects — DictSQLite and CARVS | Disnana プロジェクト — DictSQLite および CARVS
==============================================================================

.. contents:: Contents | 目次
   :local:
   :depth: 2

.. image:: https://img.shields.io/badge/Organization-Disnana-blue.svg
   :target: https://github.com/disnana
   :alt: Disnana Organization

-----

📦 **DictSQLite**
=================

.. image:: https://img.shields.io/pypi/v/dictsqlite.svg
   :target: https://pypi.org/project/dictsqlite/
   :alt: PyPI Version

.. image:: https://img.shields.io/pypi/pyversions/dictsqlite.svg
   :target: https://pypi.org/project/dictsqlite/
   :alt: Python Versions

.. image:: https://static.pepy.tech/badge/dictsqlite
   :target: https://pepy.tech/project/dictsqlite
   :alt: Downloads

.. image:: https://img.shields.io/badge/License-MIT%20%28Custom%29-blue.svg
   :target: https://github.com/disnana/DictSQLite/blob/main/LICENSE
   :alt: MIT License

Overview | 概要
----------------

**Dictionary-like simplicity for SQLite databases**

DictSQLite provides a Pythonic, dictionary-like interface for SQLite databases, making database operations intuitive and straightforward. Designed for developers who want to perform basic CRUD (Create, Read, Update, Delete) operations without writing complex SQL queries.

**辞書のような簡単さでSQLiteデータベースを扱う**

DictSQLiteは、SQLiteデータベースに対してPythonicで辞書のようなインターフェースを提供し、データベース操作を直感的で分かりやすくします。複雑なSQLクエリを書くことなく、基本的なCRUD（Create、Read、Update、Delete）操作を行いたい開発者向けに設計されています。

Features | 特長
----------------

✨ **Dictionary-like Interface | 辞書のようなインターフェース**
   Access SQLite tables with familiar dictionary syntax (``db['key'] = 'value'``)
   
   SQLiteテーブルを馴染みのある辞書構文で操作（``db['key'] = 'value'``）

🔧 **Automatic Schema Management | 自動スキーマ管理**
   Tables and columns are created automatically as needed
   
   テーブルとカラムが必要に応じて自動作成

🔒 **Transaction Control | トランザクション制御**
   Simple context manager for handling database transactions
   
   データベーストランザクションを処理するシンプルなコンテキストマネージャー

🛡️ **Built-in Encryption | 内蔵暗号化**
   Optional AES encryption to protect your data
   
   オプションのAES暗号化でデータを保護

⚡ **Cross-process & Thread-safe | クロスプロセス・スレッドセーフ**
   Uses ``portalocker`` to ensure data integrity
   
   ``portalocker`` を使用してデータ整合性を保証

🪶 **Lightweight & Minimal Dependencies | 軽量・依存関係なし**
   Pure Python except for ``portalocker`` and ``cryptography``
   
   ``portalocker`` と ``cryptography`` 以外は純粋なPython

Installation | インストール
----------------------------

Install using pip:

.. code-block:: bash

   pip install dictsqlite

pipを使用してインストール：

.. code-block:: bash

   pip install dictsqlite

Quick Start | クイックスタート
------------------------------

.. code-block:: python

   from dictsqlite import DictSQLite
   import os

   # Database initialization
   db = DictSQLite('sample.db')

   # --- Basic operations ---
   # Create/Update
   db['name'] = 'Alice'
   db['age'] = 30
   db.update({'city': 'New York', 'country': 'USA'})

   # Read
   print(f"Name: {db['name']}")  # Output: Name: Alice
   print(f"City: {db.get('city')}")  # Output: City: New York

   # Delete
   del db['country']

   # Check existence
   print('country' in db)  # Output: False

   # --- Table usage ---
   users = db.table('users')
   users['user1'] = {'name': 'Bob', 'age': 25}
   users['user2'] = {'name': 'Charlie', 'age': 35}

   print(users['user1'])  # Output: {'name': 'Bob', 'age': 25}

   # --- Transactions ---
   try:
       with db.transaction() as t:
           t['status'] = 'pending'
           # This change will be rolled back
           raise ValueError("Something went wrong")
   except ValueError as e:
       print(e)

   print(db.get('status'))  # Output: None (transaction was rolled back)

   # Close connection
   db.close()

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

Documentation | ドキュメント
-----------------------------

For detailed usage, API reference, and advanced topics, please refer to the official documentation:

* `English Documentation <https://github.com/disnana/DictSQLite/blob/main/documents/english.md>`_

詳細な使用法、API リファレンス、高度なトピックについては、公式ドキュメントをご覧ください：

* `日本語ドキュメント <https://github.com/disnana/DictSQLite/blob/main/documents/japanese.md>`_

License | ライセンス
---------------------

This project is licensed under a Custom MIT License. Usage and modification are free, but proper credit to the original author is required.

See the `License File <https://github.com/disnana/DictSQLite/blob/main/LICENSE>`_ for details.

このプロジェクトはカスタムMITライセンスの下でライセンスされています。コードの使用と修正は自由ですが、元の作成者への適切なクレジットが必要です。

詳細は `ライセンスファイル <https://github.com/disnana/DictSQLite/blob/main/LICENSE>`_ をご覧ください。

Links | 公式リンク
-------------------

* `GitHub Repository <https://github.com/disnana/DictSQLite>`_ | `GitHubリポジトリ <https://github.com/disnana/DictSQLite>`_
* `PyPI Package <https://pypi.org/project/dictsqlite/>`_ | `PyPIパッケージ <https://pypi.org/project/dictsqlite/>`_

-----

🔐 **CARVS**
============

Overview | 概要
----------------

**Convert Windows user passwords to OTP (One-Time Password)**

CARVS is a security tool that changes Windows user account passwords to OTP generated by Google Authenticator app on your smartphone.

**WindowsユーザーのパスワードをOTP（ワンタイムパスワード）に変換**

CARVSは、Windowsユーザーアカウントのパスワードを、スマートフォンのGoogle Authenticatorアプリで生成されるOTPに変更するセキュリティツールです。セキュリティ層の追加としての利用を想定しています。

Warning | 注意
---------------

.. warning::
   **Important Security Notice**
   
   At least up to v0.0.0.6, this tool is vulnerable to certain attacks. We strongly recommend using additional protection such as BitLocker.
   
   It is recommended to set up password recovery options in case of login issues.

.. warning::
   **重要な注意事項**
   
   少なくともv0.0.0.6までは一部の攻撃に弱いため、BitLocker等による追加保護を強く推奨します。
   
   万が一不具合等でログインできなくなると困るので、パスワードをリセットできるようにしておくことをお勧めしております。

.. important::
   **Requirements | 必要要件**
   
   * Smartphone | スマートフォン
   * Google Authenticator app | Google Authenticatorアプリ
   * If using third-party security software, add ``c:\passchange.exe`` to exclusion list | サードパーティ製セキュリティソフト使用時は ``c:\passchange.exe`` を除外リストに追加

Setup | セットアップ
--------------------

**If the application won't start:**

1. **Visual Studio C Runtime is required**
   
   The most likely cause is missing Visual Studio C Runtime.

2. **Runtime installation steps**

   .. code-block:: text

      1. Download the latest version from the link below
      2. Run install_all.bat from the ZIP file with administrator privileges
      3. Automatic setup will complete

   `Visual C++ Redistributable Runtime Package <https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/>`_

**起動できない場合の対処法：**

1. **Visual StudioのCランタイムが必要**
   
   起動できない可能性が高い原因は、Visual Studio C Runtimeの不足です。

2. **ランタイムのインストール手順**

   .. code-block:: text

      1. 以下のサイトから最新版をダウンロード
      2. ZIPファイル内の install_all.bat を管理者権限で実行
      3. 自動セットアップが完了

   `Visual C++ Redistributable Runtime Package <https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/>`_

License | ライセンス
---------------------

See the `License File <https://github.com/disnana/CARVS/blob/main/LICENSE>`_ for details.

詳細は `ライセンスファイル <https://github.com/disnana/CARVS/blob/main/LICENSE>`_ をご覧ください。

Links | 公式リンク
-------------------

* `GitHub Repository <https://github.com/disnana/CARVS>`_ | `GitHubリポジトリ <https://github.com/disnana/CARVS>`_

===================
📞 Support | サポート
===================

If you have questions or need support, please feel free to contact us through the following methods:

ご質問やサポートが必要な場合は、以下の方法でお気軽にお問い合わせください：

📧 **Email Support | メールサポート**
   support@disnana.com

🐛 **Issues (Bug Reports & Feature Requests) | Issues（問題報告・機能要求）**
   Please use the GitHub Issues page for each project:
   
   各プロジェクトのGitHub Issuesページをご利用ください：
   
   * `DictSQLite Issues <https://github.com/disnana/DictSQLite/issues>`_
   * `CARVS Issues <https://github.com/disnana/CARVS/issues>`_

💬 **Discord (DictSQLite Official) | Discord（DictSQLite公式）**
   Real-time support and community: https://discord.gg/KzeHDrgwAz
   
   リアルタイムサポートとコミュニティ: https://discord.gg/KzeHDrgwAz

.. note::
   If the project has been helpful to you, please give us a ⭐ on GitHub!
   Your support encourages our development.
   
   プロジェクトが役に立った場合は、GitHubで ⭐ をお願いします！
   あなたのサポートが開発の励みになります。

-----

.. raw:: html

   <div align="center">
   <p><strong>© 2024 Disnana Organization. All rights reserved.</strong></p>
   </div>