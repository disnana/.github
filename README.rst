################################################################################
Disnana Projects - DictSQLite & CARVS
################################################################################

.. contents:: 目次 / Table of Contents
   :depth: 3
   :local:
   :backlinks: top

================================================================================
DictSQLite
================================================================================

|pypi-version| |python-versions| |license-dictsqlite| |downloads|

.. |pypi-version| image:: https://img.shields.io/pypi/v/dictsqlite.svg
   :target: https://pypi.org/project/dictsqlite/
   :alt: PyPI version

.. |python-versions| image:: https://img.shields.io/pypi/pyversions/dictsqlite.svg
   :target: https://pypi.org/project/dictsqlite/
   :alt: Python versions

.. |license-dictsqlite| image:: https://img.shields.io/badge/License-MIT%20%28Custom%29-blue.svg
   :target: https://github.com/disnana/DictSQLite/blob/main/LICENSE
   :alt: License

.. |downloads| image:: https://static.pepy.tech/badge/dictsqlite
   :target: https://pepy.tech/project/dictsqlite
   :alt: Downloads

概要 / Overview
--------------------------------------------------------------------------------

**日本語:**

DictSQLiteは、Pythonの辞書のようなシンプルなインターフェースでSQLiteデータベースを操作できるライブラリです。
複雑なSQL文を書くことなく、基本的なCRUD（作成、読み取り、更新、削除）操作を直感的に行うことができます。

**English:**

DictSQLite provides a Pythonic, dictionary-like interface for SQLite databases, making database operations intuitive and straightforward. 
It's designed for developers who want to manage SQLite data without writing complex SQL queries for basic CRUD (Create, Read, Update, Delete) operations.

特長 / Features
--------------------------------------------------------------------------------

**日本語:**

✨ **辞書ライクなインターフェース**: ``db['key'] = 'value'`` のような馴染みのある辞書構文でデータベーステーブルを操作
🔧 **自動スキーマ管理**: テーブルとカラムが自動で作成される
🔒 **トランザクション制御**: データベーストランザクションを処理するシンプルなコンテキストマネージャー
🛡️ **組み込み暗号化**: オプションのAES暗号化でデータを保護
🔄 **クロスプロセス/スレッドセーフ**: ``portalocker`` を使用してデータの整合性を保証
⚡ **軽量でゼロ依存**: ``portalocker`` と ``cryptography`` 以外は純粋なPython

**English:**

✨ **Dictionary-like Interface**: Interact with your database tables using familiar dictionary syntax (``db['key'] = 'value'``)
🔧 **Automatic Schema Management**: Tables and columns are created on-the-fly
🔒 **Transaction Control**: Simple context manager for handling database transactions
🛡️ **Built-in Encryption**: Secure your data with optional AES encryption
🔄 **Cross-process/thread Safety**: Uses ``portalocker`` to ensure data integrity
⚡ **Lightweight & Zero-dependency**: Besides ``portalocker`` and ``cryptography``, it's pure Python

インストール / Installation
--------------------------------------------------------------------------------

**日本語:**

pipを使用してインストール:

.. code-block:: bash

   pip install dictsqlite

**English:**

Install via pip:

.. code-block:: bash

   pip install dictsqlite

クイックスタート / Quick Start
--------------------------------------------------------------------------------

**日本語:**

基本的な使用例:

.. code-block:: python

   from dictsqlite import DictSQLite
   import os

   db_file = 'sample.db'
   if os.path.exists(db_file):
       os.remove(db_file)

   # データベースの初期化
   db = DictSQLite(db_file)

   # --- 基本操作 ---
   # 作成/更新
   db['name'] = 'Alice'
   db['age'] = 30
   db.update({'city': 'New York', 'country': 'USA'})

   # 読み取り
   print(f"Name: {db['name']}")  # 出力: Name: Alice
   print(f"City: {db.get('city')}") # 出力: City: New York

   # 削除
   del db['country']

   # 存在確認
   print('country' in db)  # 出力: False

   # イテレーション
   for key, value in db.items():
       print(f"{key}: {value}")

   # --- テーブルの使用 ---
   users = db.table('users')
   users['user1'] = {'name': 'Bob', 'age': 25}
   users['user2'] = {'name': 'Charlie', 'age': 35}

   print(users['user1']) # 出力: {'name': 'Bob', 'age': 25}

   # 接続を閉じる
   db.close()

**English:**

Basic usage example:

.. code-block:: python

   from dictsqlite import DictSQLite
   import os

   db_file = 'sample.db'
   if os.path.exists(db_file):
       os.remove(db_file)

   # Initialize the database
   db = DictSQLite(db_file)

   # --- Basic Operations ---
   # Create/Update
   db['name'] = 'Alice'
   db['age'] = 30
   db.update({'city': 'New York', 'country': 'USA'})

   # Read
   print(f"Name: {db['name']}")  # Output: Name: Alice
   print(f"City: {db.get('city')}") # Output: City: New York

   # Delete
   del db['country']

   # Check existence
   print('country' in db)  # Output: False

   # Iterate
   for key, value in db.items():
       print(f"{key}: {value}")

   # --- Using Tables ---
   users = db.table('users')
   users['user1'] = {'name': 'Bob', 'age': 25}
   users['user2'] = {'name': 'Charlie', 'age': 35}

   print(users['user1']) # Output: {'name': 'Bob', 'age': 25}

   # Close the connection
   db.close()

ドキュメント / Documentation
--------------------------------------------------------------------------------

**日本語:**

詳細な使用方法、API リファレンス、高度なトピックについては、公式ドキュメントをご参照ください:

- `English Documentation <https://github.com/disnana/DictSQLite/blob/main/documents/english.md>`_
- `Japanese Documentation <https://github.com/disnana/DictSQLite/blob/main/documents/japanese.md>`_

**English:**

For detailed usage, API reference, and advanced topics, please refer to our official documentation:

- `English Documentation <https://github.com/disnana/DictSQLite/blob/main/documents/english.md>`_
- `Japanese Documentation <https://github.com/disnana/DictSQLite/blob/main/documents/japanese.md>`_

ライセンス / License
--------------------------------------------------------------------------------

**日本語:**

このプロジェクトはカスタムMITライセンスの下でライセンスされています。コードの使用と修正は自由ですが、元の作成者への適切なクレジットを表示する必要があります。

詳細については `LICENSE <https://github.com/disnana/DictSQLite/blob/main/LICENSE>`_ ファイルをご覧ください。

**English:**

This project is licensed under a custom MIT License. While you are free to use and modify the code, you must give appropriate credit to the original creator.

See the `LICENSE <https://github.com/disnana/DictSQLite/blob/main/LICENSE>`_ file for more details.

リンク / Links
--------------------------------------------------------------------------------

**日本語:**

- `GitHub リポジトリ <https://github.com/disnana/DictSQLite>`_
- `PyPI パッケージ <https://pypi.org/project/dictsqlite/>`_
- `Issue 報告 <https://github.com/disnana/DictSQLite/issues>`_

**English:**

- `GitHub Repository <https://github.com/disnana/DictSQLite>`_
- `PyPI Package <https://pypi.org/project/dictsqlite/>`_
- `Issue Reports <https://github.com/disnana/DictSQLite/issues>`_

================================================================================
CARVS
================================================================================

|security-warning| |platform-windows|

.. |security-warning| image:: https://img.shields.io/badge/Security-Warning-red.svg
   :alt: Security Warning

.. |platform-windows| image:: https://img.shields.io/badge/Platform-Windows-blue.svg
   :alt: Windows Platform

概要 / Overview
--------------------------------------------------------------------------------

**日本語:**

CARVSは、WindowsユーザーのパスワードをOTP（ワンタイムパスワード）に変更するセキュリティツールです。
Google Authenticatorと連携してセキュリティを強化します。

**English:**

CARVS is a security tool that converts Windows user passwords to OTP (One-Time Password) authentication.
It enhances security by integrating with Google Authenticator for two-factor authentication.

.. warning::
   **重要な注意事項 / Important Notice**
   
   **日本語:** 少なくともv0.0.0.6までは一部の攻撃に弱いため、Bitlockerを用いた追加の保護を推奨いたします。
   万が一不具合等でログインできなくなると困るので、パスワードをリセットできるようにしておくことをお勧めしております。
   
   **English:** Until at least v0.0.0.6, this software is vulnerable to certain attacks. We recommend using Bitlocker for additional protection.
   We recommend setting up password reset capabilities in case of login issues due to malfunctions.

特長 / Features
--------------------------------------------------------------------------------

**日本語:**

🔐 **OTP認証**: Windowsログインにワンタイムパスワードによるセキュリティ層を追加
📱 **Google Authenticator連携**: スマートフォンアプリとの seamless な統合
🛡️ **セキュリティ強化**: 従来のパスワード認証よりも安全
⚙️ **Windows統合**: Windows認証システムと直接統合

**English:**

🔐 **OTP Authentication**: Adds a one-time password security layer to Windows login
📱 **Google Authenticator Integration**: Seamless integration with smartphone app
🛡️ **Enhanced Security**: More secure than traditional password authentication
⚙️ **Windows Integration**: Direct integration with Windows authentication system

インストール / Installation
--------------------------------------------------------------------------------

**日本語:**

.. tip::
   **必要な環境:**
   
   - Windows OS
   - スマートフォン
   - Google Authenticator アプリ
   - Visual Studio C Runtime

**セットアップ手順:**

1. **Visual Studio C Runtime のインストール**
   
   起動できない場合、Visual StudioのCランタイムがないから起動できない可能性が高いです。
   
   `必要なランタイムのダウンロード <https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/>`_ から
   できるだけ日付が新しいものをダウンロードし、そのZIPファイルに入っている ``install_all.bat`` を管理者権限で実行してください。

2. **セキュリティソフトの設定**
   
   Windows Defender以外のセキュリティソフトをご使用の際は、``c:\passchange.exe`` を検知除外リストに追加することをお勧めいたします。

**English:**

.. tip::
   **System Requirements:**
   
   - Windows OS
   - Smartphone
   - Google Authenticator app
   - Visual Studio C Runtime

**Setup Instructions:**

1. **Install Visual Studio C Runtime**
   
   If the application fails to start, it's likely due to missing Visual Studio C Runtime.
   
   Download the latest version from `Visual C++ Redistributable Runtime Package <https://www.techpowerup.com/download/visual-c-redistributable-runtime-package-all-in-one/>`_ 
   and run ``install_all.bat`` from the ZIP file with administrator privileges.

2. **Security Software Configuration**
   
   When using security software other than Windows Defender, we recommend adding ``c:\passchange.exe`` to the detection exclusion list.

クイックスタート / Quick Start
--------------------------------------------------------------------------------

**日本語:**

.. code-block:: text

   1. 必要なランタイムをインストール
   2. Google Authenticator をスマートフォンにインストール
   3. CARVS を管理者権限で実行
   4. 画面の指示に従ってセットアップ
   5. QRコードをGoogle Authenticator でスキャン
   6. OTP認証でログインテスト

**English:**

.. code-block:: text

   1. Install required runtime
   2. Install Google Authenticator on smartphone
   3. Run CARVS with administrator privileges
   4. Follow on-screen setup instructions
   5. Scan QR code with Google Authenticator
   6. Test login with OTP authentication

ドキュメント / Documentation
--------------------------------------------------------------------------------

**日本語:**

- 使い方や説明動画は近日中に投稿予定です
- ソースコードの一部も近日中に公開します
- セキュリティ関連の強化、および解析対策の強化等を行っております

**English:**

- Usage and tutorial videos will be published soon
- Partial source code will be released soon
- Security enhancements and anti-analysis measures are being implemented

ライセンス / License
--------------------------------------------------------------------------------

**日本語:**

このプロジェクトはBSD 3-Clause ライセンスの下でライセンスされています。

詳細については `LICENSE <https://github.com/disnana/CARVS/blob/main/LICENSE>`_ ファイルをご覧ください。

**English:**

This project is licensed under the BSD 3-Clause License.

See the `LICENSE <https://github.com/disnana/CARVS/blob/main/LICENSE>`_ file for more details.

リンク / Links
--------------------------------------------------------------------------------

**日本語:**

- `GitHub リポジトリ <https://github.com/disnana/CARVS>`_
- `Issue 報告 <https://github.com/disnana/CARVS/issues>`_

**English:**

- `GitHub Repository <https://github.com/disnana/CARVS>`_
- `Issue Reports <https://github.com/disnana/CARVS/issues>`_

================================================================================
サポート / Support
================================================================================

**日本語:**

このプロジェクトが役に立ったら、GitHubで ⭐ をつけてください！

質問やサポートについては、以下にお問い合わせください:

- **Email**: support@disnana.com
- **GitHub Issues**: 各プロジェクトのIssueページをご利用ください
- **Pull Requests**: コントリビューション、Issue、機能リクエストを歓迎します！

**English:**

If you find these projects useful, please give them a ⭐ on GitHub!

For questions or support, please contact us:

- **Email**: support@disnana.com
- **GitHub Issues**: Please use the Issues page for each project
- **Pull Requests**: Contributions, issues, and feature requests are welcome!

.. note::
   **お知らせ / Notice**
   
   **日本語:** セキュリティに関する問題を発見した場合は、公開のIssueではなく、直接メールでご連絡ください。
   
   **English:** If you discover security-related issues, please contact us directly via email rather than public Issues.

================================================================================
Copyright © 2024 Disnana. All rights reserved.
================================================================================