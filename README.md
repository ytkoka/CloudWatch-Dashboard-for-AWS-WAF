# CloudWatch Dashboard for AWS WAF
CloudFormation template for creating CloudWatch dashboards for AWS WAF.　This dashboard uses only CloudWatch functionality, making it quick to deploy and easy to customize.
 
## CloudFormation Input Parameters:
* WebACL name
* WAF region
* CloudWatch Log name
 
![Dashboard Image](/images/cwd.png)

## CloudFormation templates:
[Templates](/cloudformation/)

* [Regional WAF](/cloudformation/cw-waf-dashboard-regional.yaml)

* [Regional WAF +Log insights query widget](/cloudformation/cw-waf-dashboard-regional-logquery.yaml)
This will create a Lambda function for the custom widget

* [CloudFront WAF](/cloudformation/cw-waf-dashboard-cloudfront.yaml)

* [CloudFront WAF +Log insights query widget](/cloudformation/cw-waf-dashboard-cloudfront-logguery.yaml)
This will create a Lambda function for the custom widget






