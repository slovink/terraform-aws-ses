
Terraform AWS SES
Terraform module to create an SES Identity with SES IAM user on AWS.

Terraform Licence tfsec static-checks

Share on Facebook Share on LinkedIn Share on Twitter

We eat, drink, sleep and most importantly love DevOps. We are working towards strategies for standardizing architecture while ensuring security for the infrastructure. We are strong believer of the philosophy Bigger problems are always solved by breaking them into smaller manageable problems. Resonating with microservices architecture, it is considered best-practice to run database, cluster, storage in smaller connected yet manageable pieces within the infrastructure.

This module is basically combination of Terraform open source and includes automatation tests and examples. It also helps to create and improve your infrastructure with minimalistic code instead of maintaining the whole infrastructure code yourself.

We have fifty plus terraform modules. A few of them are comepleted and are available for open source usage while a few others are in progress.

Prerequisites
This module has a few dependencies:

Terraform 1.x.x
Go
github.com/stretchr/testify/assert
github.com/gruntwork-io/terratest/modules/terraform
Examples
IMPORTANT: Since the master branch used in source varies based on new modifications, we suggest that you use the release versions here.

Simple Example
Here is an example of how you can use this module in your inventory structure:

module "ses" {
source = "./../"

name        = "ses"
environment = "example"
label_order = ["name", "environment"]

domain   = ""
iam_name = "ses-user1"

enable_verification = false
enable_mx           = false
enable_spf_domain   = false
}

Inputs
Name	Description	Type	Default	Required
cname_type	CNAME type for Record Set.	string	"CNAME"	no
domain	Domain to use for SES.	string	n/a	yes
enable_domain	Control whether or not to enable domain.	bool	true	no
enable_filter	Control whether or not to enable receipt filter.	bool	false	no
enable_mail_from	Control whether or not to enable mail from domain.	bool	false	no
enable_mx	Control whether or not to enable mx DNS recodrds.	bool	false	no
enable_policy	Control whether identity policy create for SES.	bool	false	no
enable_spf_domain	Control whether or not to enable enable spf domain.	bool	false	no
enable_template	Control whether create a template for emails.	bool	false	no
enable_verification	Control whether or not to verify SES DNS records.	bool	false	no
enabled	Boolean indicating whether or not to create sns module.	bool	true	no
environment	Environment (e.g. prod, dev, staging).	string	""	no
filter_cidr	The IP address or address range to filter, in CIDR notation.	string	""	no
filter_name	The name of the filter.	string	""	no
filter_policy	Block or Allow filter.	string	""	no
iam_name	IAM username.	string	""	no
label_order	Label order, e.g. name,application.	list(any)	[]	no
mail_from_domain	Subdomain (of the route53 zone) which is to be used as MAIL FROM address.	string	""	no
mx_type	MX type for Record Set.	string	"MX"	no
name	Name (e.g. app or cluster).	string	""	no
policy_name	Name of the policy.	string	""	no
repository	Terraform current module repo	string	"https://github.com/slovink/terraform-aws-ses"	no
ses_records	Additional entries which are added to the _amazonses record.	list(string)	[]	no
template_html	The HTML body of the email. Must be less than 500KB in size, including both the text and HTML parts.	string	""	no
template_name	The name of the template. Cannot exceed 64 characters. You will refer to this name when you send email.	string	""	no
template_subject	The subject line of the email.	string	""	no
text	The email body that will be visible to recipients whose email clients do not display HTML.	string	""	no
txt_type	Txt type for Record Set.	string	"TXT"	no
zone_id	Route53 host zone ID to enable SES.	string	""	no
Outputs
Name	Description
domain_identity_arn	ARN of the SES domain identity.
id	The domain name of the domain identity.
Testing
In this module testing is performed with terratest and it creates a small piece of infrastructure, matches the output like ARN, ID and Tags name etc and destroy infrastructure in your AWS account. This testing is written in GO, so you need a GO environment in your system.

You need to run the following command in the testing folder:

go test -run Test
Feedback


If you have found it worth your time, go ahead and give us a ★ on our GitHub!

About us
we offer expert guidance, implementation support and services to help organisations accelerate their journey to the cloud. Our services include docker and container orchestration, cloud migration and adoption, infrastructure automation, application modernisation and remediation, and performance engineering.

We are The Cloud Experts!