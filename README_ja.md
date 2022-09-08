# CloudWatch Dashboard for AWS WAF
AWS WAF 用の CloudWatch ダッシュボードをセットアップするための CloudFormation テンプレートです。 このテンプレートを使用して一般的にWAFで利用されるメトリクスや CloudWatch logs insights を利用した CloudWatch ダッシュボードを迅速にデプロイできます。 AWS WAF で使用している WAF ルール セットに応じて、メトリクスを追加しカスタマイズできます。

WebACL と CloudWatch Logs をまだ作成していない場合は、[こちら](https://github.com/ytkoka/cfn-example-aws-waf)の CloudFormation テンプレートを使用して WebACL を作成し、CloudWatch ログを有効にすることができます。
 
## 導入方法:
導入するには、下の [Launch Stack] ボタンをクリックするか、テンプレート ファイルをこのリポジトリ (/[cloudformation](/cloudformation/)/) からローカル フォルダーにコピーしてから、CloudFormation サービスで AWS コンソールを開き、[Create Stack] をクリックします。 新しいリソースで選択し、[テンプレート ソース] セクションで [テンプレートファイルのアップロード] を選択し、[ファイルの選択] をクリックして、ローカル フォルダーにコピーしたファイルを選択します。
![Create Stack Image](/images/create-stack.png)

次の画面で、スタックの名前 (ダッシュボード名として使用されます) を設定し、必要なパラメータ（CloudWatch Log の名前、WAF リージョン、および WebACLの名前）を入力します。 次に [次へ] をクリックし、最後の画面で [スタックの作成] をクリックします。
![Parameter Image](/images/parameters.png)
 
 デプロイプロセスが完了すると、URL を介して CloudWatch ダッシュボードにアクセスできます。 これは、AWS CloudFormation の [出力] タブにあります。
 ![Output Image](/images/output.png)

 ## ダッシュボード:
ダッシュボード テンプレートは、すぐに使用できる複数のグラフとクエリを提供します

例:
![Dashboard Image2](/images/cwd2.png)
ダッシュボード テンプレートには、次のウィジェットが含まれています
* 許可されたリクエストとブロックされたリクエスト
* カウントされたすべてのリクエスト
* ボットリクエストと非ボットリクエスト (Bot Control ルールグループが必要)
* ボット リクエストの割合 (Bot Control ルールグループが必要)
* 上位の Terminating ルール
* 上位の 国
* 上位の ユーザーエージェント
* 上位の IP アドレス
* 上位の カウントされたURI
* 上位のブロックされた URI
* ブロックされたすべてのリクエストの上位 IP アドレスと URI の組み合わせ ([Contributor insightsを使用](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ContributorInsights.html))
* カウントされたリクエストログ
* ブロックされたリクエストのログ
* Logs Insights クエリ フォーム ([カスタム ウィジェットを使用](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/add_custom_widget_dashboard_about.html))

**ご利用のWAFルールに合わせてカスタマイズしてください**

## CloudFormation テンプレート:

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][1]
[Regional WAF](/cloudformation/cw-waf-dashboard-regional.yaml) 

[1]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-regional.yaml

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][2]
[CloudFront WAF](/cloudformation/cw-waf-dashboard-cloudfront.yaml) 

[2]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-cloudfront.yaml

以下のテンプレートは、CloudWatch Logs インサイト クエリの [custom widget](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/add_custom_widget_dashboard.html)用の Lambda 関数を作成します

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][3]
[Regional WAF](/cloudformation/cw-waf-dashboard-regional-logquery.yaml) 

[3]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-regional-logquery.yaml

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][4]
[CloudFront WAF](/cloudformation/cw-waf-dashboard-cloudfront-logguery.yaml) 

[4]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-cloudfront-logguery.yaml

以下のテンプレートは、上位の IP アドレスと URI の組み合わせを取得するための [contributor insights rule](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ContributorInsights.html) を作成します

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][5]
[Regional WAF](/cloudformation/cw-waf-dashboard-regional-contributor-insights.yaml) 

[5]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-regional-contributor-insights.yaml

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][6]
[CloudFront WAF](/cloudformation/cw-waf-dashboard-cloudfront-contributor-insights.yaml) 

[6]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-cloudfront-contributor-insights.yaml

## コスト:
このダッシュボードの費用は、主に次の要因によって変化します
* CloudWatch ログの取り込みサイズ
* CloudWatch Logs ストアのサイズ
* CloudWatch Logs insights クエリの数
* CloudWatch Logs insights のクエリ データ範囲
* Lambda 呼び出し数 (カスタム ウィジェットを使用する場合)
* Contributor Insights ルールと一致したログ イベント (Contributor Insights を使用している場合)

ダッシュボードのコストの見積もりは、[CloudWatch pricing page](https://aws.amazon.com/cloudwatch/pricing/) を参照ください。
