

# ディクショナリ

Dynamo 2.0 では、ディクショナリのデータ タイプをリストのデータ タイプと分離する概念が導入されました。この変更により、ワークフローにおけるデータの作成や操作の方法が大幅に変更される可能性があります。2.0 よりも前のバージョンでは、ディクショナリとリストは 1 つのデータ タイプとして統合されていました。つまり、リストが実際には整数キーを持つディクショナリだったのです。

* #### ディクショナリとは

ディクショナリは、キーと値のペアの集合で構成されたデータ タイプで、各キーは各集合に固有です。ディクショナリは順序付けされておらず、基本的には、リストにあるようなインデックス値の代わりにキーを使用して「調べる」ことができます。*Dynamo 2.0 では、キーに文字列のみを使用できます。*

* #### リストとは

リストは、順序付けされた値の集合で構成されたデータ タイプです。Dynamo では、リストはインデックス値として整数を使用します。

* #### この変更を行った理由、および注意すべき理由

ディクショナリは、リストと分離されたことによって第一級オブジェクトとなりました。そのため、インデックス値を覚えたり、ワークフロー全体で厳密なリスト構造を維持することなく、値の格納や検索をすばやく容易に行うことができます。ユーザのテストにおいて、複数の ```GetItemAtIndex``` ノードの代わりにディクショナリを使用した場合に、グラフのサイズが大幅に低減することがわかりました。

* #### 変更内容

* *構文*の変更により、コード ブロック内のディクショナリとリストの初期化および操作の方法が変更されました。
* ディクショナリは```{キー : 値}```の構文を使用します。
* リストは```[値, 値, 値]```の構文を使用します。

* ディクショナリを作成、編集、クエリーするための*新しいノード*が、ライブラリに追加されました。
* 1.x のコード ブロックで作成されたリストは、スクリプトのロード時に、角括弧```[ ]```を波括弧```{ }```の代わりに使用する新しいリストの構文に自動的に移行されます。![画像](images/9-1/DYN20_dictionary.png)

* #### 注意すべき理由、使用する目的

コンピュータ サイエンスにおいて、ディクショナリはリストのように、オブジェクトの集合です。リストは特定の順序で並んでいますが、ディクショナリは*順序なし*の集合です。一連番号(インデックス)に依存せず、*キー*を使用します。

次の画像では、可能性のあるディクショナリの使用例を示しています。多くの場合、ディクショナリを使用して、直接的な関係を持たない 2 つのデータを関連付けます。ここでは、スペイン語バージョンの単語を英語バージョンに接続して、後で検索できるようにしています。![画像](images/9-1/9-1_dictionaryExample.png)
