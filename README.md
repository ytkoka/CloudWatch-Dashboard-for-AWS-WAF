# CloudWatch Dashboard for AWS WAF
This repository provides CloudFormation templates to quickly set up CloudWatch Dashboard for AWS WAF. This template will allow you to get started more quickly by giving deployable prebuilt CloudWatch dashboards with commonly observed metrics and CloudWatch logs insights. You can add additional metrics depending on the WAF rule set you are using on AWS WAF.
 
## Installation:
To do the installation, click the Launch Stack button below or copy the template file from this repository (/[cloudformation](/cloudformation/)/) to a local folder, then open the AWS console in the CloudFormation service, click Create Stack, select with new resources, then in the Template source section select Upload a template file, click Choose file and choose the file you copied to your local folder.
![Create Stack Image](/images/create-stack.png)

In the next screen, set a name for the stack (it will use as the dashboard name) and fill in the required parameters, CloudWatch Log name, WAF region and WebACL name. Then click Next, and click Create stack on the last screen.
![Parameter Image](/images/parameters.png)
 
 When the deployment process is complete, we can access the CloudWatch dashboard via its URL. You can find it in the Outputs tab of AWS CloudFormation:
 ![Output Image](/images/output.png)

 ## Example dashboard:
![Dashboard Image](/images/cwd.png)

The dashboard template provides multiple graphs and queries for you that are available out-of-the-box.
The example dashboard includes the following widgets:

* Allowed vs Blocked Requests
* All Counted Requests
* Bot requests vs Non-bot requests (Require Bot control rule group)
* Percentage of Bot requests (Require Bot control rule group)
* Top Terminating Rules
* Top Countries
* Top User-agents
* Blocked requests by Rate based rule  (Require Rate-based rule)
* Top Counted URIs
* Top Blocked URIs
* Counted Requests
* Blocked Requests 
* Logs Insights Query Form (Custom widget)

**Please customize it according to the WAF rules you are using.**

## CloudFormation templates:
[Templates](/cloudformation/)

[Regional WAF](/cloudformation/cw-waf-dashboard-regional.yaml)  (Example Template for ALB)

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][1]

[1]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-regional.yaml

[CloudFront WAF](/cloudformation/cw-waf-dashboard-cloudfront.yaml) (Example Template for CloudFront)

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][2]

[2]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-cloudfront.yaml

Below templates will create a Lambda function for the CloudWatch Logs insights query custom widget. [Custom Widget](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/add_custom_widget_dashboard.html) is powered by custom Lambda functions, enabling complete control over the content, layout, and interactions. see the [custom widgets samples](https://github.com/aws-samples/cloudwatch-custom-widgets-samples)

[Regional WAF + Log insights query widget](/cloudformation/cw-waf-dashboard-regional-logquery.yaml) (Example Template for ALB)

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][3]

[3]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-regional-logquery.yaml

[CloudFront WAF + Log insights query widget](/cloudformation/cw-waf-dashboard-cloudfront-logguery.yaml) (Example Template for CloudFront)

[![launch-stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)][4]

[4]: https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=WAF-Dashboard&templateURL=https://s3.amazonaws.com/ytkoka-resources/CloudWatch-Dashboard-for-AWS-WAF/cw-waf-dashboard-cloudfront-logguery.yaml


