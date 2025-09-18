================================================================
Disnana Projects - DictSQLite & CARVS
================================================================

.. contents:: Table of Contents / 目次
   :depth: 2
   :local:

.. image:: https://img.shields.io/pypi/v/dictsqlite.svg
   :target: https://pypi.org/project/dictsqlite/
   :alt: PyPI Version

.. image:: https://img.shields.io/pypi/l/dictsqlite.svg
   :target: https://github.com/disnana/dictsqlite/blob/main/LICENSE
   :alt: License

.. image:: https://img.shields.io/pypi/dm/dictsqlite.svg
   :target: https://pypi.org/project/dictsqlite/
   :alt: Downloads

.. image:: https://img.shields.io/badge/python-3.7+-blue.svg
   :target: https://www.python.org/downloads/
   :alt: Python Version

========================================
DictSQLite
========================================

概要 / Overview
========================================

**日本語:**

DictSQLiteは、Pythonの辞書型データをSQLiteデータベースに簡単に保存・操作できる軽量ライブラリです。複雑なSQLクエリを書くことなく、直感的なPythonコードでデータベース操作を実現します。

**English:**

DictSQLite is a lightweight Python library that allows easy storage and manipulation of dictionary-type data in SQLite databases. It enables intuitive database operations with Python code without writing complex SQL queries.

特長 / Features
========================================

**日本語:**

* 🔥 **シンプルAPI**: 辞書型データを直接SQLiteに保存
* 🚀 **高速**: 最適化されたSQLiteクエリ生成
* 🛡️ **型安全**: Pythonの型ヒント完全対応
* 📊 **柔軟な検索**: 複数条件での高速検索機能
* 🔧 **軽量**: 外部依存関係なし、標準ライブラリのみ使用
* 📝 **完全ドキュメント**: 日本語・英語の詳細ドキュメント

**English:**

* 🔥 **Simple API**: Direct storage of dictionary data to SQLite
* 🚀 **Fast**: Optimized SQLite query generation
* 🛡️ **Type Safe**: Full Python type hints support
* 📊 **Flexible Search**: High-speed search with multiple conditions
* 🔧 **Lightweight**: No external dependencies, uses only standard library
* 📝 **Full Documentation**: Detailed documentation in Japanese and English

インストール / Installation
========================================

**日本語:**

.. code-block:: bash

   # PyPIからインストール
   pip install dictsqlite

   # 開発版をインストール
   pip install git+https://github.com/disnana/dictsqlite.git

**English:**

.. code-block:: bash

   # Install from PyPI
   pip install dictsqlite

   # Install development version
   pip install git+https://github.com/disnana/dictsqlite.git

クイックスタート / Quick Start
========================================

**日本語:**

.. code-block:: python

   from dictsqlite import DictSQLite

   # データベース接続を作成
   db = DictSQLite("example.db")

   # テーブルを作成（自動的にスキーマを推論）
   users_table = db.create_table("users")

   # データを挿入
   user_data = {
       "name": "田中太郎",
       "age": 30,
       "email": "tanaka@example.com",
       "is_active": True
   }
   users_table.insert(user_data)

   # データを検索
   results = users_table.find({"age": 30})
   print(f"検索結果: {results}")

   # 複数条件での検索
   active_users = users_table.find({
       "is_active": True,
       "age": {"$gte": 25}  # 25歳以上
   })

   # データを更新
   users_table.update(
       {"name": "田中太郎"}, 
       {"age": 31}
   )

   # データを削除
   users_table.delete({"is_active": False})

**English:**

.. code-block:: python

   from dictsqlite import DictSQLite

   # Create database connection
   db = DictSQLite("example.db")

   # Create table (automatically infers schema)
   users_table = db.create_table("users")

   # Insert data
   user_data = {
       "name": "John Doe",
       "age": 30,
       "email": "john@example.com",
       "is_active": True
   }
   users_table.insert(user_data)

   # Search data
   results = users_table.find({"age": 30})
   print(f"Search results: {results}")

   # Search with multiple conditions
   active_users = users_table.find({
       "is_active": True,
       "age": {"$gte": 25}  # Age 25 or above
   })

   # Update data
   users_table.update(
       {"name": "John Doe"}, 
       {"age": 31}
   )

   # Delete data
   users_table.delete({"is_active": False})

.. warning::
   **注意 / Warning**
   
   **日本語:** 大容量データを扱う場合は、適切なインデックスの設定を推奨します。
   
   **English:** For large datasets, it is recommended to set appropriate indexes.

ドキュメント / Documentation
========================================

**日本語:**

* `📚 完全ドキュメント <https://dictsqlite.readthedocs.io/ja/>`_
* `🎯 APIリファレンス <https://dictsqlite.readthedocs.io/ja/api/>`_
* `💡 チュートリアル <https://dictsqlite.readthedocs.io/ja/tutorials/>`_
* `❓ FAQ <https://dictsqlite.readthedocs.io/ja/faq/>`_

**English:**

* `📚 Full Documentation <https://dictsqlite.readthedocs.io/en/>`_
* `🎯 API Reference <https://dictsqlite.readthedocs.io/en/api/>`_
* `💡 Tutorials <https://dictsqlite.readthedocs.io/en/tutorials/>`_
* `❓ FAQ <https://dictsqlite.readthedocs.io/en/faq/>`_

ライセンス / License
========================================

**日本語:**

DictSQLiteはMITライセンスの下で公開されています。商用・非商用を問わず自由にご利用いただけます。

**English:**

DictSQLite is released under the MIT License. You are free to use it for both commercial and non-commercial purposes.

公式リンク / Links
========================================

**日本語:**

* `🏠 公式ホームページ <https://dictsqlite.disnana.com/>`_
* `📦 PyPIパッケージ <https://pypi.org/project/dictsqlite/>`_
* `🐙 GitHubリポジトリ <https://github.com/disnana/dictsqlite>`_
* `💬 Discord公式サーバー <https://discord.gg/dictsqlite>`_

**English:**

* `🏠 Official Homepage <https://dictsqlite.disnana.com/en/>`_
* `📦 PyPI Package <https://pypi.org/project/dictsqlite/>`_
* `🐙 GitHub Repository <https://github.com/disnana/dictsqlite>`_
* `💬 Official Discord Server <https://discord.gg/dictsqlite>`_

========================================
CARVS
========================================

概要 / Overview
========================================

**日本語:**

CARVS（Computer-Assisted Research and Visualization System）は、研究データの自動収集・分析・可視化を支援する高度なシステムです。機械学習とデータサイエンス技術を組み合わせ、研究者の作業効率を大幅に向上させます。

**English:**

CARVS (Computer-Assisted Research and Visualization System) is an advanced system that supports automatic collection, analysis, and visualization of research data. It combines machine learning and data science technologies to significantly improve researchers' work efficiency.

.. warning::
   **重要 / Important**
   
   **日本語:** CARVSは現在アルファ版です。本番環境での使用前に十分なテストを行ってください。
   
   **English:** CARVS is currently in alpha version. Please conduct thorough testing before using in production environments.

特長 / Features
========================================

**日本語:**

* 🤖 **AI駆動分析**: 機械学習による自動データ分析
* 📈 **リアルタイム可視化**: インタラクティブなダッシュボード
* 🔗 **多データソース対応**: API、CSV、データベース、Webスクレイピング
* 🎯 **カスタマイズ可能**: プラグインアーキテクチャ
* 🛡️ **セキュア**: エンタープライズレベルのセキュリティ
* 🌐 **クラウド対応**: AWS、Azure、GCP対応

**English:**

* 🤖 **AI-Driven Analysis**: Automatic data analysis with machine learning
* 📈 **Real-time Visualization**: Interactive dashboards
* 🔗 **Multi-Data Source Support**: APIs, CSV, databases, web scraping
* 🎯 **Customizable**: Plugin architecture
* 🛡️ **Secure**: Enterprise-level security
* 🌐 **Cloud Ready**: Support for AWS, Azure, GCP

インストール / Installation
========================================

**日本語:**

.. code-block:: bash

   # 基本インストール
   pip install carvs

   # 全機能版（推奨）
   pip install carvs[full]

   # 開発者向け
   git clone https://github.com/disnana/carvs.git
   cd carvs
   pip install -e .[dev]

**English:**

.. code-block:: bash

   # Basic installation
   pip install carvs

   # Full features (recommended)
   pip install carvs[full]

   # For developers
   git clone https://github.com/disnana/carvs.git
   cd carvs
   pip install -e .[dev]

クイックスタート / Quick Start
========================================

**日本語:**

.. code-block:: python

   from carvs import ResearchPipeline, DataCollector, Analyzer

   # 研究パイプラインを初期化
   pipeline = ResearchPipeline("my_research_project")

   # データ収集器を設定
   collector = DataCollector()
   collector.add_source("api", url="https://api.example.com/data")
   collector.add_source("csv", path="./research_data.csv")

   # データを収集
   raw_data = collector.collect_all()

   # 分析器を初期化
   analyzer = Analyzer(pipeline="auto_ml")

   # 自動分析を実行
   results = analyzer.analyze(raw_data, target="research_outcome")

   # 結果を可視化
   pipeline.visualize(results, output="dashboard.html")

   # レポートを生成
   pipeline.generate_report(
       template="academic",
       output="research_report.pdf",
       language="ja"  # 日本語レポート
   )

**English:**

.. code-block:: python

   from carvs import ResearchPipeline, DataCollector, Analyzer

   # Initialize research pipeline
   pipeline = ResearchPipeline("my_research_project")

   # Set up data collector
   collector = DataCollector()
   collector.add_source("api", url="https://api.example.com/data")
   collector.add_source("csv", path="./research_data.csv")

   # Collect data
   raw_data = collector.collect_all()

   # Initialize analyzer
   analyzer = Analyzer(pipeline="auto_ml")

   # Run automatic analysis
   results = analyzer.analyze(raw_data, target="research_outcome")

   # Visualize results
   pipeline.visualize(results, output="dashboard.html")

   # Generate report
   pipeline.generate_report(
       template="academic",
       output="research_report.pdf",
       language="en"  # English report
   )

ドキュメント / Documentation
========================================

**日本語:**

* `📖 ユーザーガイド <https://carvs.disnana.com/docs/ja/>`_
* `🔧 セットアップガイド <https://carvs.disnana.com/setup/ja/>`_
* `📊 分析手法リファレンス <https://carvs.disnana.com/analysis/ja/>`_
* `🎨 可視化ギャラリー <https://carvs.disnana.com/gallery/ja/>`_

**English:**

* `📖 User Guide <https://carvs.disnana.com/docs/en/>`_
* `🔧 Setup Guide <https://carvs.disnana.com/setup/en/>`_
* `📊 Analysis Methods Reference <https://carvs.disnana.com/analysis/en/>`_
* `🎨 Visualization Gallery <https://carvs.disnana.com/gallery/en/>`_

ライセンス / License
========================================

**日本語:**

CARVSは独自ライセンスの下で提供されています。アカデミック利用は無料、商用利用にはライセンスが必要です。

**English:**

CARVS is provided under a proprietary license. Academic use is free, commercial use requires a license.

公式リンク / Links
========================================

**日本語:**

* `🏛️ 公式サイト <https://carvs.disnana.com/>`_
* `📂 GitHubリポジトリ <https://github.com/disnana/carvs>`_
* `📧 商用ライセンス問い合わせ <mailto:license@disnana.com>`_
* `🎓 アカデミックプログラム <https://carvs.disnana.com/academic/>`_

**English:**

* `🏛️ Official Website <https://carvs.disnana.com/en/>`_
* `📂 GitHub Repository <https://github.com/disnana/carvs>`_
* `📧 Commercial License Inquiry <mailto:license@disnana.com>`_
* `🎓 Academic Program <https://carvs.disnana.com/academic/en/>`_

========================================
サポート / Support
========================================

**日本語:**

ご質問やサポートが必要な場合は、以下の方法でお気軽にお問い合わせください：

* `🐛 Issues (GitHub) <https://github.com/disnana/.github/issues>`_
* `📧 メール <mailto:support@disnana.com>`_
* `💬 Discord (DictSQLite公式サーバー) <https://discord.gg/dictsqlite>`_

**技術的な質問・バグレポート**
  GitHubのIssuesをご利用ください。日本語・英語どちらでも対応いたします。

**商用利用・ライセンスに関するお問い合わせ**
  support@disnana.com までメールでご連絡ください。

**コミュニティ交流**
  DictSQLite Discord公式サーバーにぜひご参加ください！

**English:**

For questions or support, please feel free to contact us through the following methods:

* `🐛 Issues (GitHub) <https://github.com/disnana/.github/issues>`_
* `📧 Email <mailto:support@disnana.com>`_
* `💬 Discord (DictSQLite Official Server) <https://discord.gg/dictsqlite>`_

**Technical Questions & Bug Reports**
  Please use GitHub Issues. We support both Japanese and English.

**Commercial Use & License Inquiries**
  Please contact us via email at support@disnana.com.

**Community Interaction**
  Join our official DictSQLite Discord server!

---

.. note::
   **最終更新 / Last Updated:** 2024年9月 / September 2024
   
   **バージョン / Version:** DictSQLite v2.1.0, CARVS v0.8.0-alpha