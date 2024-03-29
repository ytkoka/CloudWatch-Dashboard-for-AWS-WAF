# CloudWatch Dashboard for AWS WAF

[View this page in Japanese (日本語)](README_ja.md)

This repository provides CloudFormation templates to quickly set up CloudWatch Dashboard for AWS WAF. This template will allow you to get started more quickly by giving deployable prebuilt CloudWatch dashboards with commonly observed metrics and CloudWatch logs insights. You can add additional metrics depending on the WAF rule set you are using on AWS WAF.

If you have not yet created WebACL and CloudWatch Logs, you can use the CloudFormation template [here](https://github.com/ytkoka/cfn-example-aws-waf/blob/main/aws-waf-template-loggingfilter.yaml) to create a WebACL and enable CloudWatch logging.
 
## Installation:
To do the installation, click the Launch Stack button below or copy the template file from this repository (/[cloudformation](/cloudformation/)/) to a local folder, then open the AWS console in the CloudFormation service, click Create Stack, select with new resources, then in the Template source section select Upload a template file, click Choose file and choose the file you copied to your local folder.
![Create Stack Image](/images/create-stack.png)

In the next screen, set a name for the stack (it will use as the dashboard name) and fill in the required parameters, CloudWatch Log name, WAF region and WebACL name. Then click Next, and click Create stack on the last screen.
![Parameter Image](/images/parameters.png)
 
 When the deployment process is complete, we can access the CloudWatch dashboard via its URL. You can find it in the Outputs tab of AWS CloudFormation:
 ![Output Image](/images/output.png)

 ## Dashboard:
The dashboard template provides multiple graphs and queries for you that are available out-of-the-box.

Example
![Dashboard Image2](/images/cwd2.png)
Dashboard template includes the following widgets:
* Allowed vs Blocked Requests
* All Counted Requests
* Bot requests vs Non-bot requests (Require Bot control rule group)
* Percentage of Bot requests (Require Bot control rule group)
* Top Terminating Rules
* Top Countries
* Top User-agents
* Top IP Addresses
* Top Counted URIs
* Top Blocked URIs
* Top IP addresses and URI combination for all the Blocked requests ([Use Contributor insights](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ContributorInsights.html))
* Counted Requests Logs
* Blocked Requests Logs
* Logs Insights Query Form ([Use Custom widget](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/add_custom_widget_dashboard_about.html))

**Please customize it according to the WAF rules you are using.**

## CloudFormation templates:

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][1]
[Regional WAF](/cloudformation/cw-waf-dashboard-regional.yaml) 

[1]: https://console.aws.amazon.com/cloudformation/home#/stacks/create/review?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-regional.yaml

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][2]
[CloudFront WAF](/cloudformation/cw-waf-dashboard-cloudfront.yaml) 

[2]: https://console.aws.amazon.com/cloudformation/home#/stacks/create/review?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-cloudfront.yaml

Below templates will create a Lambda function for the CloudWatch Logs insights query [custom widget](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/add_custom_widget_dashboard.html)

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][3]
[Regional WAF](/cloudformation/cw-waf-dashboard-regional-logquery.yaml) 

[3]: https://console.aws.amazon.com/cloudformation/home#/stacks/create/review?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-regional-logquery.yaml

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][4]
[CloudFront WAF](/cloudformation/cw-waf-dashboard-cloudfront-logguery.yaml) 

[4]: https://console.aws.amazon.com/cloudformation/home#/stacks/create/review?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-cloudfront-logguery.yaml

Below templates will create a [contributor insights rule](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/ContributorInsights.html) to get the top IP addresses and URI combination.

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][5]
[Regional WAF](/cloudformation/cw-waf-dashboard-regional-contributor-insights.yaml) 

[5]: https://console.aws.amazon.com/cloudformation/home#/stacks/create/review?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-regional-contributor-insights.yaml

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][6]
[CloudFront WAF](/cloudformation/cw-waf-dashboard-cloudfront-contributor-insights.yaml) 

[6]: https://console.aws.amazon.com/cloudformation/home#/stacks/create/review?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-cloudfront-contributor-insights.yaml

## Cost:
The cost of this dashboard depends on the following factors :
* CloudWatch Logs ingest size
* CloudWatch Logs store size
* Number of CloudWatch Logs insights queries
* CloudWatch Logs insights query data ranges
* Number of Lambda invocations (If you use the custom widget)
* Contributor Insights Rule and Matched Log Events (If you use Contributor Insights)

Please see the [CloudWatch pricing page](https://aws.amazon.com/cloudwatch/pricing/) to estimate the dashboard cost.
