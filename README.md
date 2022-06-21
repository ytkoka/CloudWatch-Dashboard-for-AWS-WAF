# CloudWatch Dashboard for AWS WAF
This repository provides CloudFormation templates to quickly set up CloudWatch Dashboard for AWS WAF. This template will allow you to get started more quickly by giving deployable prebuilt CloudWatch dashboards with commonly observed metrics and CloudWatch logs insights. You can add additional metrics depending on the WAF rule set you are using on AWS WAF.
 
## Installation:
To do the installation, copy the template file from this repository (/[cloudformation](/cloudformation/)/) to a local folder. Then open the AWS console in the CloudFormation service, click Create Stack, select with new resources, then in the Template source section select Upload a template file, click Choose file and choose the file you copied to your local folder. click Next:
![Create Stack Image](/images/create-stack.png)

In the next screen, set a name for the stack (it will use as the dashboard name) and fill in the required parameters, CloudWatch Log name, WAF region and WebACL name. Then click Next, and click Create stack on the last screen.
![Parameter Image](/images/parameters.png)
 
 When the deployment process is complete, we can access the CloudWatch dashboard via its URL. You can find it in the Outputs tab of AWS CloudFormation:
 ![Output Image](/images/output.png)

 ## Example dashboard:
![Dashboard Image](/images/cwd.png)

## CloudFormation templates:
[Templates](/cloudformation/)

* [Regional WAF](/cloudformation/cw-waf-dashboard-regional.yaml) Example Template for ALB

* [CloudFront WAF](/cloudformation/cw-waf-dashboard-cloudfront.yaml) Example Template for CloudFront


Below templates will create a Lambda function for the CloudWatch Logs insights query custom widget. [Custom Widget](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/add_custom_widget_dashboard.html) is powered by custom Lambda functions, enabling complete control over the content, layout, and interactions. 

* [Regional WAF + Log insights query widget](/cloudformation/cw-waf-dashboard-regional-logquery.yaml)

* [CloudFront WAF + Log insights query widget](/cloudformation/cw-waf-dashboard-cloudfront-logguery.yaml)






