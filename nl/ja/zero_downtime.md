---

copyright:

  years: 2018

lastupdated: "2018-11-28"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .deprecated}


# ダウン時間をゼロにする方法
{: #zero-downtime}

グローバル戦略が重要です。特定のデータ・センターまたはロケーションを選択して、顧客にとって世界の適切な地域にデータをデプロイできます。
{:shortdesc}

{{site.data.keyword.Bluemix}} プラットフォーム・サービスは自己管理されています。つまり、アプリをデプロイした場所が、複数のデータ・センターにワークロードを分散させることができます。また、確実にフェイルオーバー設計を整えることができます。つまり、顧客にとってお客様のアプリは常に稼働中になります。インフラストラクチャー・リソースについては、リソースをデプロイする個々のデータ・センターを選択できます。 

すべての {{site.data.keyword.Bluemix_notm}} リソースは、世界中のデータ・センターのロケーションでホストされます。高可用性および災害復旧は、すべてのサービスにわたって汎用ではないため、使用可能な高可用性および災害復旧のタイプは、使用しているサービスによって異なります。  

## 災害復旧
{: #disaster-recovery}

災害復旧とは、単一ロケーションでの壊滅的な障害または可用性の消失が発生しても存続できるよう対処することに関する内容です。災害復旧が確実に実施されるようにするには、複数のロケーションに複数の {{site.data.keyword.Bluemix_notm}} 環境をデプロイして、Single Point of Failure を回避することが必要です。これらの環境は、Public、Dedicated、または Local の各プラットフォームを組み合わせたものにすることができます。  

### 災害復旧計画 

{{site.data.keyword.Bluemix_notm}} は災害に対する計画の要件に従っており、すべてのアプリケーションには、災害イベント後のリカバリーまたは再始動のための計画があります。リカバリーは、リカバリー・センターの電子バックアップ、またはコンピューティングをリストアする代替コンピューティング装置から行われます。潜在的な災害の前に、災害復旧計画には、ハードウェア、ソフトウェア、ネットワーキング接続、およびオフサイト・バックアップの能力に関するシステムとホスティングの要件が含まれています。

以下のリストに、災害復旧計画の要件を示します。

- ロード・バランシングに関して、コンピューター・サービスを使用可能にしておく方法を説明する文書が存在します。 
- マルチサイト・フェイルオーバーの発生に関して、災害復旧計画は、フェイルオーバーを実行させて確実に再始動するために、誰が何を実行するかを説明する必要があります。 
- 災害復旧計画は、ソリューションがどのように機能し、データ損失がどのようなものかを定義する必要があります。 
- 災害復旧計画は、許容可能な最大ダウン時間がどのように達成され、災害復旧計画 Rep データベースに保管されるかを確定する必要があります。  
- 災害時復旧計画は、実動での実行と異なる場合に、災害時モードで実行するためのセキュリティー管理を指定します。 

### 災害復旧計画の管理 

{{site.data.keyword.Bluemix}} が従う要件は以下のとおりです。 

- 災害復旧計画は、主要なインフラストラクチャー変更、主要なアプリケーション・リリース、およびすべてのテストの後に更新する必要があります。 
- 災害復旧計画は、毎年承認される必要があります。 

## リソースをデプロイするロケーション 
{: #ov_intro_reg}

異なるロケーションで、アプリケーション管理に同じ {{site.data.keyword.cloud_notm}} インフラストラクチャー、課金に同じ使用量詳細ビューを使用して、アプリおよびサービス・インスタンスを作成できます。 顧客に最も近いロケーションにアプリをデプロイすることで、アプリケーションの待ち時間を短くすることができます。 

また、セキュリティー問題に対応するために、アプリケーション・データを保存しておくロケーションを選択することもできます。 複数のロケーションでアプリを構築すると、1 つのロケーションが使用不可になっても、他のロケーションにあるアプリが稼働し続けます。 使用する各ロケーションで、リソースの割当量は同じです。 プラットフォーム・リソースおよびそれらが使用可能なロケーションについて詳しくは、『[サービス可用性](/docs/resources/services_region.html#services_region)』を参照してください。

{{site.data.keyword.cloud_notm}} コンソールのグローバル・ロード・バランシング機能により、地理的に最も近いロケーションが使用不可になっている場合、コンソールは次に近いロケーションの情報を表示します。 このように、ユーザーは必要なリソースにアクセスするためにアクションを取らずに、常にコンソールにアクセスできます。

コンソールのリソース・リスト・ビューから、デフォルトですべてのロケーションのすべてのリソースを表示できます。特定のロケーションのリソースを表示および処理する場合は、**「ロケーション」**メニューを展開し、リストからロケーションを選択します。 

また、`ibmcloud api` コマンドを使用し、ロケーションの API エンドポイントを指定することにより、コマンド・ライン・インターフェース (CLI) を使用して、作業する {{site.data.keyword.cloud_notm}} ロケーションに接続することもできます。 例えば、
{{site.data.keyword.cloud_notm}} ロンドンに接続するには、次のコマンドを入力します。

```
ibmcloud api https://api.eu-gb.bluemix.net
```

各ロケーションに固有の接頭部が割り当てられています。 {{site.data.keyword.cloud_notm}} には、次のロケーションと、ロケーション接頭部が用意されています。

| **ロケーション** | **API エンドポイント** |
|-----------------|-------------------|
| ダラス | api.ng.bluemix.net |
| シドニー | api.au-syd.bluemix.net |
| フランクフルト | api.eu-de.bluemix.net |
| ロンドン | api.eu-gb.bluemix.net |
| ワシントン DC | api.us-east.bluemix.net |
| 東京 | api.jp-tok.bluemix.net |
{: caption="表 1. {{site.data.keyword.cloud_notm}} ロケーション・リスト" caption-side="top"}

インフラストラクチャーをデプロイするときには、データが置かれる場所についてさらに多くのオプションがあります。 ロケーションを選択することも、{{site.data.keyword.Bluemix_notm}} のデータ・センターのリストから選択することもできます。 

## データ・センター
{: #data_center}

データ・センターは、サービスおよびアプリに使用される電力、冷却、コンピュート、ネットワーク、およびストレージの各リソースをホストする物理的ロケーションです。データ・センターは、1 つのロケーション内のマルチゾーンと同様で、ローカル障害からの分離を提供しません。詳しくは、『[Global locations for your global business ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/data-centers/){: new_window}』を参照してください。

{{site.data.keyword.Bluemix_notm}} は、世界中の多くの場所でデータ・センターを提供しています。 インフラストラクチャー・リソースをデプロイするときに、{{site.data.keyword.Bluemix_notm}} のデータ・センターのリストから選択できます。 


![以下の表で説明されているデータ・センターのマップ ](images/Global-View.svg)

### 北アメリカ
{: #na}

| データ・センター名 | コード |
|----------|---------|
|ダラス 01|dal01|
|ダラス 05|dal05|
|ダラス 06|dal06|
|ダラス 07|dal07|
|ダラス 09|dal09|
|ダラス 10|dal10|
|ダラス 12|dal12|
|ダラス 13|dal13|
|ワシントン DC 01|wdc01|
|ワシントン DC 04|wdc04|
|ワシントン DC 06|wdc06|
|ワシントン DC 07|wdc07|
|サンノゼ 01|sjc01|
|サンノゼ 03|sjc03|
|サンノゼ 04|sjc04|
|シアトル 01|sea01|
|ヒューストン 01|hou01|
|モントリオール 01|mon01|
|トロント 01|tor01|
|メキシコ 01|mex01|
{: caption="表 2. 北アメリカのデータ・センター" caption-side="top"}

### 南アメリカ
{: #sa}

| データ・センター名 | コード |
|----------|---------|
|サンパウロ 01|sao01|
{: caption="表 3. 南アメリカのデータ・センター" caption-side="top"}

### ヨーロッパ
{: #eu}

| データ・センター名 | コード |
|----------|---------|
|ロンドン 02|lon02|
|ロンドン 04|lon04|
|ロンドン 05|lon05|
|ロンドン 06|lon06|
|フランクフルト 02|fra02|
|フランクフルト 04|fra04|
|フランクフルト 05|fra05|
|ミラノ 01|mil01|
|アムステルダム 01|ams01|
|アムステルダム 03|ams03|
|パリ 01|par01|
|オスロ 01|osl01|
{: caption="表 4. ヨーロッパのデータ・センター" caption-side="top"}

### アジア太平洋
{: #ap}

| データ・センター名 | コード |
|----------|---------|
|東京 01|tok02|
|東京 04|tok04|
|東京 05|tok05|
|ソウル 01|seo01|
|香港 02|hkg02|
|シンガポール 01|sng01|
|シドニー 01|syd01|
|シドニー 04|syd04|
|シドニー 05|syd05|
|メルボルン 01|mel01|
{: caption="表 5. アジア太平洋のデータ・センター" caption-side="top"}


## サービス・レベル・アグリーメント (SLA)
{: #SLAs} 

{{site.data.keyword.Bluemix_notm}} は、単一の Dedicated 環境または Local 環境内のプラットフォーム・サービスの複数インスタンスに対して、99.5% の可用性のサービス・レベルを提供します。

ダウン時間に対する請求を送信するには、[{{site.data.keyword.Bluemix_notm}} サポート](https://console.cloud.ibm.com/unifiedsupport/supportcenter){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") までお問い合わせください。

{{site.data.keyword.Bluemix_notm}} には、 {{site.data.keyword.Bluemix_notm}} サービスについて、お客様のアカウントへクレジット補償が適用される SLA が用意されています。SLA は、{{site.data.keyword.Bluemix_notm}} の障害を解決して、指定されたサービス・レベルを達成するための唯一の方法です。{{site.data.keyword.Bluemix_notm}} は、単一の Dedicated 環境または Local 環境内のプラットフォーム・サービスの複数インスタンスに対して、99.5% の可用性のサービス・レベルを提供します。

Dedicated 環境について詳しくは、『[IBM Cloud Dedicated](/docs/dedicated/index.html#dedicated)』を参照してください。Local 環境については、『[Bluemix Local](/docs/local/index.html#local)』を参照してください。 

{{site.data.keyword.Bluemix_notm}} の完全なサービス記述は、『[Cloud Services terms](http://www-03.ibm.com/software/sla/sladb.nsf/sla/bm){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")』から入手できます。

### 可用性ダウン時間 SLA

ダウン時間が 99.5% の可用性に満たない場合は、お客様のアカウントでクレジットを受け取ることができます。可用性ダウン時間とは、お客様のどのサービス・インスタンスにも接続できない合計分数です。ダウン時間の合計分数は、お客様が停止イベントのレポートを送信した時点から、影響を受けるインスタンスの少なくとも 1 つが使用可能になった時点までの期間です。

{{site.data.keyword.Bluemix_notm}} は、以下のサービスに対して 99.95% の可用性の SLA を提供します。 
- 各サービスのカタログ詳細で説明されているように、高可用性向けに構成された Public 環境内のクラウド・サービス。 
- 地理的に分離されたデータ・センター内の複数の Dedicated 環境または Local 環境にわたるクラウド・サービス。 

|タイプ	|説明	|サポートの詳細|
|-----|-------------|---------------|
|高可用性の Public 環境または複数の Dedicated/Local 環境 |その他の環境 |クレジット |
|<99.95% |<99.5% |10% |
|<99.90% |<99.0% |25% |
{: caption="表 6. 月次可用性のサービス・レベル" caption-side="top"}

可用性の割合は、契約月の合計分数からその月のダウン時間の合計分数を差し引き、それをその月の合計分数で割ることにより算出されます。 

例えば、31 日間の月の合計は、44,640 分です。6 時間の可用性ダウン時間が発生した場合、ダウン時間は 360 分です。ダウン時間は 6 時間のみなので、99.19% の可用性になります。99.19 % は 99.90% 未満であるため、Public 環境または Local 環境で 25% のクレジットを受け取ることになります。   

```
= (月の合計 44,640 分 - 360 ダウンタイム分) / 月の合計 44,640 分
= (実際に使用可能な 44,280 分) / 月の合計 44,640 分
= 99.19% の可用性
```

SLA には、指定された除外、{{site.data.keyword.Bluemix_notm}} UI の非可用性、コンテンツの再ロード、構成、有効化、またはアクセスにかかる時間に関連するダウン時間や障害は含まれません。

可用性ダウン時間 SLA には、{{site.data.keyword.Bluemix_notm}} インフラストラクチャー・サービスは含まれません。
{: note}

### インフラストラクチャー・サービス SLA

インフラストラクチャー・サービスとは、ベアメタル・サーバーと仮想サーバー、ネットワーキング、ストレージ、ならびにセキュリティーのサービスです。インフラストラクチャー・サービスの完全なリストを見つけるには、`iaas` のタグで {{site.data.keyword.Bluemix_notm}} カタログを検索してください。 

ダウン時間とは、パブリック・ネットワーク、プライベート・ネットワーク、および予備インフラストラクチャーの電源と HVAC の障害に基づくサービス中断が原因で、顧客が特定したインフラストラクチャー・サービスが使用不可になっている合計分数です。合計ダウン時間分数の計算は、サービスに影響を与える検証された停止が特定されたときから、サービスが使用可能になった時刻までになります。 

ダウン時間には、定期保守や告知済みの保守の時間は含まれません。30 分間連続するダウン時間期間が発生するたびに、障害によって直接影響を受けた、特定されたサービスの月額料金の 5% に相当する額のクレジットを受け取ります。ダウン時間が、連続する 30 分未満の場合は、クレジットを受け取ることはできません。この計算を満たすために、異なる障害タイプのダウン時間を合算することはできません。

### インフラストラクチャー・ハードウェアの交換およびアップグレード SLA
{{site.data.keyword.Bluemix_notm}} は、障害が発生したハードウェアを交換するとき、またはスケジュールされているハードウェア・アップグレードを実行する際のダウン時間を最小限に抑えようとしています。 

{{site.data.keyword.Bluemix_notm}} は、以下に対してクレジットを提供します。
- お客様がハードウェア障害を報告したことを {{site.data.keyword.Bluemix_notm}} が確認した時刻から、交換するための時間に基づくハードウェアの交換。
- アップグレードを受けるサービスの合計ダウン時間に基づく計画的ハードウェア・アップグレード。 

サービス・レベルの時間からは、オペレーティング・システムやアプリケーションの再ロードに要する時間、または性能が低下している時間は除外されます。{{site.data.keyword.Bluemix_notm}} が指定されたサービス・レベル時間を満たしていない場合は、ハードウェアの交換またはアップグレードの影響を受けるサービスの月額料金に基づいてクレジットを受け取ることができます。

|タイプ	|説明	|
|-----|-------------|
|サービス・レベル時間 |クレジットのパーセント |
|2 時間以上 |なし |
|2 時間未満 |20% |
|6 時間未満 |40% |
|10 時間未満 |60% |
|14 時間未満 |80% |
|18 時間未満 |80% |
{: caption="表 7. ハードウェアの交換またはアップグレードの影響を受けるサービスの月額料金に基づくクレジット補償" caption-side="top"}

### 請求
サービス・レベルを満たさなかった契約月の最終日から 60 日以内に請求を送信してください。影響を受けたサービス、エラー・メッセージ、および請求を検証するために必要なその他の情報を特定するのに十分な情報を提供してください。 

このクレジットは、各契約月中において影響を受けるサービスの累積的な可用性に基づき、適用可能な最も高額な補償になり、影響を受ける当該サービスの月額料金を使用して計算されます。クレジットは、最高で月額料金の 25% までとなります。

ダウン時間に対する請求を送信するには、[{{site.data.keyword.Bluemix_notm}} サポート](https://console.cloud.ibm.com/unifiedsupport/supportcenter){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") までお問い合わせください。

### 除外事項
以下のことが原因で SLA を満たせなかった場合、クレジットを受け取ることはできません。
- お客様またはコミュニティーが提供するコンテンツ、テクノロジー、設計、または指示に問題があった
- ベータ版、試験的、または無料のクラウド・サービス。
- IBM 以外のビルドパック
- サポートされないシステム構成およびプラットフォーム
- ネットワーク、ハードウェア、装置、または電源などのお客様のインフラストラクチャーの障害
- お客様のシステム管理のアクション、コマンド、またはファイル転送
- 障害を解決するために必要な情報またはアクセス権限の提供においてお客様側にエラーがあった、またはそれらを提供できなかった
- お客様が原因のセキュリティー・インシデントまたはセキュリティー・テスト
- IBM の妥当な制御を超えたその他の原因
